---
title: sqlsrv_execute | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_execute
apitype: NA
helpviewer_keywords:
- sqlsrv_exclude
- executing queries
- API Reference, sqlsrv_execute
ms.assetid: 38331bc2-4391-4f9f-aa83-9873dad605a0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ba15ea2e756e6c83b2fcdb6cf56c39511bd95296
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "67992750"
---
# <a name="sqlsrv_execute"></a>sqlsrv_execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

执行之前准备的语句。 有关准备语句进行指向的信息，请参阅 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) 。  
  
> [!NOTE]  
> 如果要对不同的参数值多次执行已准备的语句，该函数是理想之选。  
  
## <a name="syntax"></a>语法  
  
```  
  
sqlsrv_execute( resource $stmt)  
```  
  
#### <a name="parameters"></a>参数  
$stmt  ：用于指定要执行的语句的资源。 有关如何创建语句资源的详细信息，请参阅 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)。  
  
## <a name="return-value"></a>返回值  
布尔值：如果成功执行语句，则为 **true** 。 否则为 **false**。  
  
## <a name="example"></a>示例  
以下示例执行在 AdventureWorks 数据库的 [Sales.SalesOrderDetail](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 表中更新字段的语句。 该示例假定已在本地计算机上安装了 SQL Server 和 AdventureWorks 数据库。 从命令行运行该示例时，所有输出都将写入控制台。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Set up the parameters array. Parameters correspond, in order, to  
question marks in $tsql. */  
$params = array( 5, 10);  
  
/* Create the statement. */  
$stmt = sqlsrv_prepare( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Statement prepared.\n";  
}  
else  
{  
     echo "Error in preparing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute the statement. Display any errors that occur. */  
if( sqlsrv_execute( $stmt))  
{  
      echo "Statement executed.\n";  
}  
else  
{  
     echo "Error in executing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[SQLSRV 驱动程序 API 参考](../../connect/php/sqlsrv-driver-api-reference.md)

[文档中相关的代码示例](../../connect/php/about-code-examples-in-the-documentation.md)  

[sqlsrv_query](../../connect/php/sqlsrv-query.md)  
  
