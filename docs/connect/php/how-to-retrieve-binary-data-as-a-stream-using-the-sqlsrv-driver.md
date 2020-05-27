---
title: 如何：使用 SQLSRV 驱动程序以流的形式检索二进制数据 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, as a binary stream
- streaming data
ms.assetid: cd8d6382-abe6-48ee-9d10-4e6c52c0cb9a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3f77439f2369d7fbf4e27603bcbf8c8a2f8d8399
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993486"
---
# <a name="how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver"></a>如何：使用 SQLSRV 驱动程序以流的形式检索二进制数据
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

以流的形式检索数据仅在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的 SQLSRV 驱动程序中可用，在 PDO_SQLSRV 驱动程序中不可用。  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 利用 PHP 流从服务器检索大量二进制数据。 本主题介绍如何以流的形式检索二进制数据。  
  
使用流检索二进制数据（如图像）后，通过检索数据块而不是将整个对象加载到脚本内存中可避免使用大量脚本内存。  
  
## <a name="example"></a>示例  
以下示例从 AdventureWorks 数据库的 *Production.ProductPhoto* 表中检索二进制数据（在本例中为图像）。 图像以流的形式检索，并显示在浏览器中。  
  
通过使用 [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) 和 [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) （其中返回类型指定为二进制流）来完成以流的形式检索图像数据操作。 返回类型通过使用常量 SQLSRV_PHPTYPE_STREAM 指定  。 有关 sqlsrv 常量的信息，请参阅[常量 (Microsoft Drivers for PHP for SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)。  
  
该示例假定已在本地计算机上安装了 SQL Server 和 [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 数据库。 当从浏览器运行该示例时，所有输出都将写入该浏览器。  
  
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
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT LargePhoto   
         FROM Production.ProductPhoto   
         WHERE ProductPhotoID = ?";  
  
/* Set the parameter values and put them in an array. */  
$productPhotoID = 70;  
$params = array( $productPhotoID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data.  
The return data is retrieved as a binary stream. */  
if ( sqlsrv_fetch( $stmt ) )  
{  
   $image = sqlsrv_get_field( $stmt, 0,   
                      SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_BINARY));  
   header("Content-Type: image/jpg");  
   fpassthru($image);  
}  
else  
{  
     echo "Error in retrieving data.</br>";  
     die(print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
在示例中指定返回类型演示了如何以二进制流的形式指定 PHP 返回类型。 从技术上说，这在示例中不需要，因为 LargePhoto 字段具有 SQL Server 类型 varbinary(max)，因此默认返回为二进制流  。 有关默认 PHP 数据类型的信息，请参阅 [Default PHP Data Types](../../connect/php/default-php-data-types.md)。 若要了解如何指定 PHP 返回类型，请参阅[操作说明：指定 PHP 数据类型](../../connect/php/how-to-specify-php-data-types.md)。  
  
## <a name="see-also"></a>另请参阅  
[检索数据](../../connect/php/retrieving-data.md)

[使用 SQLSRV 驱动程序以流的形式检索数据](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[文档中相关的代码示例](../../connect/php/about-code-examples-in-the-documentation.md)  
  
