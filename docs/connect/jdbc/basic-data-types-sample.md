---
title: 基本数据类型示例 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9374c76a76aa12f60fc3fa5f911916f39000d8b4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028462"
---
# <a name="basic-data-types-sample"></a>基本数据类型示例

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

此 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 示例应用程序说明了如何使用结果集的 getter 方法来检索基本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型值，以及如何使用结果集的 update 方法来更新这些值。

此示例的代码文件名为 BasicDT.java，该文件可在以下位置找到：

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes
```

## <a name="requirements"></a>要求

若要运行此示例应用程序，必须设置 classpath 以包含 mssql-jdbc jar 文件。 还将需要访问 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 示例数据库。 若要详细了解如何设置类路径，请参阅[使用 JDBC 驱动程序](../../connect/jdbc/using-the-jdbc-driver.md)。

本示例将创建所需的表并在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 示例数据库中插入示例数据：

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 提供要使用的 mssql-jdbc 类库文件，具体使用哪个文件取决于首选的 Java Runtime Environment (JRE) 设置。 有关选择哪个 JAR 文件的详细信息，请参阅 [JDBC 驱动程序的系统要求](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)。

## <a name="example"></a>示例

在下面的示例中，示例代码将建立与 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 数据库的连接，然后从 DataTypesTable 测试表中检索一行数据。 然后，将调用自定义的 displayRow 方法，以使用 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) 类的各种 get\<Type> 方法来显示结果集中的所有数据。

接下来，示例代码使用 SQLServerResultSet 类的各种 update\<Type> 方法来更新结果集中的数据，然后调用 [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) 方法将输入更新到数据库中。

最后，示例代码刷新结果集中的数据，然后再次调用自定义的 displayRow 方法来显示该结果集中的数据。

```java
import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Time;
import java.sql.Timestamp;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

import microsoft.sql.DateTimeOffset;

public class BasicDataTypes {
    private static final String tableName = "DataTypesTable";

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);) {

            dropAndCreateTable(stmt);
            insertOriginalData(con);

            String SQL = "SELECT * FROM " + tableName;
            ResultSet rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("ORIGINAL DATA", rs);

            // Update the data in the result set.
            rs.updateString(2, "B");
            rs.updateString(3, "Some updated text.");
            rs.updateBoolean(4, true);
            rs.updateDouble(5, 77.89);
            rs.updateDouble(6, 1000.01);
            long timeInMillis = System.currentTimeMillis();
            Timestamp ts = new Timestamp(timeInMillis);
            rs.updateTimestamp(7, ts);
            rs.updateDate(8, new Date(timeInMillis));
            rs.updateTime(9, new Time(timeInMillis));
            rs.updateTimestamp(10, ts);

            // -480 indicates GMT - 8:00 hrs
            ((SQLServerResultSet) rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));

            rs.updateRow();

            // Get the updated data from the database and display it.
            rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("UPDATED DATA", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        System.out.println(rs.getInt(1) + " , " +                 // SQL integer type.
                rs.getString(2) + " , " +                         // SQL char type.
                rs.getString(3) + " , " +                         // SQL varchar type.
                rs.getBoolean(4) + " , " +                        // SQL bit type.
                rs.getDouble(5) + " , " +                         // SQL decimal type.
                rs.getDouble(6) + " , " +                         // SQL money type.
                rs.getTimestamp(7) + " , " +                      // SQL datetime type.
                rs.getDate(8) + " , " +                           // SQL date type.
                rs.getTime(9) + " , " +                           // SQL time type.
                rs.getTimestamp(10) + " , " +                     // SQL datetime2 type.
                ((SQLServerResultSet) rs).getDateTimeOffset(11)); // SQL datetimeoffset type.
        System.out.println();
    }

    private static void dropAndCreateTable(Statement stmt) throws SQLException {
        stmt.executeUpdate("if object_id('" + tableName + "','U') is not null" + " drop table " + tableName);

        String sql = "create table " + tableName + " (" + "c1 int, " + "c2 char(20), " + "c3 varchar(20), " + "c4 bit, "
                + "c5 decimal(10,5), " + "c6 money, " + "c7 datetime, " + "c8 date, " + "c9 time(7), "
                + "c10 datetime2(7), " + "c11 datetimeoffset(7), " + ");";

        stmt.execute(sql);
    }

    private static void insertOriginalData(Connection con) throws SQLException {
        String sql = "insert into " + tableName + " values( " + "?,?,?,?,?,?,?,?,?,?,?" + ")";
        try (PreparedStatement pstmt = con.prepareStatement(sql)) {
            pstmt.setObject(1, 100);
            pstmt.setObject(2, "original text");
            pstmt.setObject(3, "original text");
            pstmt.setObject(4, false);
            pstmt.setObject(5, 12.34);
            pstmt.setObject(6, 56.78);
            pstmt.setObject(7, new java.util.Date(1453500034839L));
            pstmt.setObject(8, new java.util.Date(1453500034839L));
            pstmt.setObject(9, new java.util.Date(1453500034839L));
            pstmt.setObject(10, new java.util.Date(1453500034839L));
            pstmt.setObject(11, new java.util.Date(1453500034839L));
            pstmt.execute();
        }
    }
}

```

## <a name="see-also"></a>另请参阅

[处理数据类型 &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)
