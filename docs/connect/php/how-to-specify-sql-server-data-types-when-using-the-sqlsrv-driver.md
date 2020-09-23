---
title: 如何：在使用 SQLSRV 驱动程序时指定 SQL Server 数据类型
description: 了解如何在使用 SQLSRV Driver for PHP 时，在预定义语句或直接查询中使用可选的 $params 数组指定 SQL Server 数据类型
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data types
- streaming data
ms.assetid: 1fcf73cb-5634-4d89-948f-9326f1dbd030
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0720c14429aa4088d906a2063feeb34057065682
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680565"
---
# <a name="how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver"></a>如何：在使用 SQLSRV 驱动程序时指定 SQL Server 数据类型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

本主题演示如何使用 SQLSRV 驱动程序为发送到服务器的数据指定 SQL Server 数据类型。 本主题不适用于使用 PDO_SQLSRV 驱动程序的情况。  
  
若要指定 SQL Server 数据类型，必须在准备或执行可插入或更新数据的查询时使用可选的 *$params* 数组。 有关 *$params* 数组的结构和语法的详细信息，请参阅 [sqlsrv_query](../../connect/php/sqlsrv-query.md) 或 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)。  
  
以下步骤总结了如何在将数据发送到服务器时指定 SQL Server 数据类型：  
  
> [!NOTE]  
> 如果没有指定任何 SQL Server 数据类型，将使用默认类型。 有关默认 SQL Server 数据类型的信息，请参阅 [Default SQL Server Data Types](../../connect/php/default-sql-server-data-types.md)。  
  
1.  定义可插入或更新数据的 Transact-SQL 查询。 将作为占位符的问号 (?) 用于查询中的参数值。  
  
2.  初始化或更新对应于 Transact-SQL 查询中的占位符的 PHP 变量。  
  
3.  构建要在准备或执行查询时使用的 *$params* 数组。 请注意，在指定 SQL Server 数据类型时， *$params* 数组的每个元素必须也是一个数组。  
  
4.  通过将相应的 SQLSRV_SQLTYPE_&#42;**** 常量用作 $params** 数组的每个子数组中的第四个参数，指定所需的 SQL Server 数据类型。 有关 SQLSRV_SQLTYPE_&#42;**** 常量的完整列表，请参阅[常量 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md) 的 SQLTYPE 部分。 例如，在下列代码中， *$changeDate*、 *$rate*和 *$payFrequency* 分别指定为 **$params**数组中的 SQL Server 类型 **datetime**、 **money** 和 *tinyint* 。 因为没有为 *$employeeId* 指定任何 SQL Server 类型，并且该类型初始化为一个整数，所以将使用默认的 SQL Server 类型 **integer** 。  
  
    ```  
    $employeeId = 5;  
    $changeDate = "2005-06-07";  
    $rate = 30;  
    $payFrequency = 2;  
    $params = array(  
                array($employeeId, null),  
                array($changeDate, null, null, SQLSRV_SQLTYPE_DATETIME),  
                array($rate, null, null, SQLSRV_SQLTYPE_MONEY),  
                array($payFrequency, null, null, SQLSRV_SQLTYPE_TINYINT)  
              );  
    ```  
  
## <a name="example"></a>示例  
以下示例将数据插入 AdventureWorks 数据库的 HumanResources.EmployeePayHistory 表中。 为 *$changeDate*、 *$rate*和 *$payFrequency* 参数指定 SQL Server 类型。 将默认 SQL Server 类型用于 *$employeeId* 参数。 若要验证数据是否已成功插入，请检索和显示相同的数据。  
  
该示例假定已在本地计算机上安装了 SQL Server 和 [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 数据库。 从命令行运行该示例时，所有输出都将写入控制台。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the query. */  
$tsql1 = "INSERT INTO HumanResources.EmployeePayHistory (EmployeeID,  
                                                        RateChangeDate,  
                                                        Rate,  
                                                        PayFrequency)  
           VALUES (?, ?, ?, ?)";  
  
/* Construct the parameter array. */  
$employeeId = 5;  
$changeDate = "2005-06-07";  
$rate = 30;  
$payFrequency = 2;  
$params1 = array(  
               array($employeeId, null),  
               array($changeDate, null, null, SQLSRV_SQLTYPE_DATETIME),  
               array($rate, null, null, SQLSRV_SQLTYPE_MONEY),  
               array($payFrequency, null, null, SQLSRV_SQLTYPE_TINYINT)  
           );  
  
/* Execute the INSERT query. */  
$stmt1 = sqlsrv_query($conn, $tsql1, $params1);  
if( $stmt1 === false )  
{  
     echo "Error in execution of INSERT.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve the newly inserted data. */  
/* Define the query. */  
$tsql2 = "SELECT EmployeeID, RateChangeDate, Rate, PayFrequency  
          FROM HumanResources.EmployeePayHistory  
          WHERE EmployeeID = ? AND RateChangeDate = ?";  
  
/* Construct the parameter array. */  
$params2 = array($employeeId, $changeDate);  
  
/*Execute the SELECT query. */  
$stmt2 = sqlsrv_query($conn, $tsql2, $params2);  
if( $stmt2 === false )  
{  
     echo "Error in execution of SELECT.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the results. */  
$row = sqlsrv_fetch_array( $stmt2 );  
if( $row === false )  
{  
     echo "Error in fetching data.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
echo "EmployeeID: ".$row['EmployeeID']."\n";  
echo "Change Date: ".date_format($row['RateChangeDate'], "Y-m-d")."\n";  
echo "Rate: ".$row['Rate']."\n";  
echo "PayFrequency: ".$row['PayFrequency']."\n";  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt($stmt1);  
sqlsrv_free_stmt($stmt2);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[检索数据](../../connect/php/retrieving-data.md)

[文档中相关的代码示例](../../connect/php/about-code-examples-in-the-documentation.md)

[如何：指定 PHP 数据类型](../../connect/php/how-to-specify-php-data-types.md)

[转换数据类型](../../connect/php/converting-data-types.md)

[如何：使用内置 UTF-8 支持发送和检索 UTF-8 数据](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)  
  
