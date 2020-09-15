---
description: 稀疏列
title: 稀疏列 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7d4237e0-818f-4639-9093-d5ac9683fc71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 406f4fea8df9a3c410f126f5a766aeb2e1ad4bb8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88396293"
---
# <a name="sparse-columns"></a>稀疏列

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

稀疏列是对 Null 值采用优化的存储方式的普通列。 稀疏列减少了 Null 值的空间需求，但代价是检索非 Null 值的开销增加。 当至少能够节省 20% 到 40% 的空间时，才应考虑使用稀疏列。

当连接到 [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]（或更高版本）的服务器时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC Driver 3.0 支持稀疏列。 可以使用 [SQLServerDatabaseMetaData.getColumns](../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md)、[SQLServerDatabaseMetaData.getFunctionColumns](../../connect/jdbc/reference/getfunctioncolumns-method-sqlserverdatabasemetadata.md) 或 [SQLServerDatabaseMetaData.getProcedureColumns](../../connect/jdbc/reference/getprocedurecolumns-method-sqlserverdatabasemetadata.md) 确定哪个列是稀疏列以及哪个列是列集列。

此示例的代码文件名为 SparseColumns.java，位于以下位置：  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\sparse  
```

列集是返回非类型化 XML 形式的所有稀疏列的计算列。 当表中有很多列、大于 1024 或分别对这些稀疏列进行操作很烦琐时，应考虑使用列集。 列集最多可以包含 30,000 个列。

## <a name="example"></a>示例

### <a name="description"></a>说明

此示例说明如何检测列集。 它还显示如何分析列集的 XML 输出，以便从稀疏列获取数据。

所列的代码是 Java 源代码。 在编译应用程序之前，更改连接字符串。

### <a name="code"></a>代码

```java
import java.io.StringReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.SQLException;
import java.sql.Statement;

import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;

import org.w3c.dom.Document;
import org.w3c.dom.Node;
import org.w3c.dom.NodeList;
import org.xml.sax.InputSource;


public class SparseColumns {

    public static void main(String args[]) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement()) {

            createColdCallingTable(stmt);

            // Determine the column set column
            String columnSetColName = null;
            String strCmd = "SELECT name FROM sys.columns WHERE object_id=(SELECT OBJECT_ID('ColdCalling')) AND is_column_set = 1";

            try (ResultSet rs = stmt.executeQuery(strCmd)) {
                if (rs.next()) {
                    columnSetColName = rs.getString(1);
                    System.out.println(columnSetColName + " is the column set column!");
                }
            }

            strCmd = "SELECT * FROM ColdCalling";
            try (ResultSet rs = stmt.executeQuery(strCmd)) {

                // Iterate through the result set
                ResultSetMetaData rsmd = rs.getMetaData();

                DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
                DocumentBuilder db = dbf.newDocumentBuilder();
                InputSource is = new InputSource();
                while (rs.next()) {
                    // Iterate through the columns
                    for (int i = 1; i <= rsmd.getColumnCount(); ++i) {
                        String name = rsmd.getColumnName(i);
                        String value = rs.getString(i);

                        // If this is the column set column
                        if (name.equalsIgnoreCase(columnSetColName)) {
                            System.out.println(name);

                            // Instead of printing the raw XML, parse it
                            if (value != null) {
                                // Add artificial root node "sparse" to ensure XML is well formed
                                String xml = "<sparse>" + value + "</sparse>";

                                is.setCharacterStream(new StringReader(xml));
                                Document doc = db.parse(is);

                                // Extract the NodeList from the artificial root node that was added
                                NodeList list = doc.getChildNodes();
                                Node root = list.item(0); // This is the <sparse> node
                                NodeList sparseColumnList = root.getChildNodes(); // These are the xml column nodes

                                // Iterate through the XML document
                                for (int n = 0; n < sparseColumnList.getLength(); ++n) {
                                    Node sparseColumnNode = sparseColumnList.item(n);
                                    String columnName = sparseColumnNode.getNodeName();
                                    // The column value is not in the sparseColumNode, it is the value of the
                                    // first child of it
                                    Node sparseColumnValueNode = sparseColumnNode.getFirstChild();
                                    String columnValue = sparseColumnValueNode.getNodeValue();

                                    System.out.println("\t" + columnName + "\t: " + columnValue);
                                }
                            }
                        } else { // Just print the name + value of non-sparse columns
                            System.out.println(name + "\t: " + value);
                        }
                    }
                    System.out.println();// New line between rows
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    private static void createColdCallingTable(Statement stmt) throws SQLException {
        stmt.execute("if exists (select * from sys.objects where name = 'ColdCalling')" + "drop table ColdCalling");

        String sql = "CREATE TABLE ColdCalling  (  ID int IDENTITY(1,1) PRIMARY KEY,  [Date] date,  [Time] time,  PositiveFirstName nvarchar(50) SPARSE,  PositiveLastName nvarchar(50) SPARSE,  SpecialPurposeColumns XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  );";
        stmt.execute(sql);

        sql = "INSERT ColdCalling ([Date], [Time])  VALUES ('10-13-09','07:05:24')  ";
        stmt.execute(sql);

        sql = "INSERT ColdCalling ([Date], [Time], PositiveFirstName, PositiveLastName)  VALUES ('07-20-09','05:00:24', 'AA', 'B')  ";
        stmt.execute(sql);

        sql = "INSERT ColdCalling ([Date], [Time], PositiveFirstName, PositiveLastName)  VALUES ('07-20-09','05:15:00', 'CC', 'DD')  ";
        stmt.execute(sql);
    }
}

```

## <a name="see-also"></a>另请参阅

[通过 JDBC 驱动程序提升性能和可靠性](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
