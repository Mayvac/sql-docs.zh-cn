---
title: 如何：禁用多个活动的结果集 (MARS)
description: 了解如何在使用 Microsoft Drivers for PHP for SQL Server 时禁用多个活动的结果集支持
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple active result sets, disabling
- MARS, disabling
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 544d64a8c81342fbb3592371098a5e2ddec60ee5
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680692"
---
# <a name="how-to-disable-multiple-active-resultsets-mars"></a>如何：禁用多个活动的结果集 (MARS)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

如果你需要连接到不启用多个活动的结果集 (MARS) 的 SQL Server 数据源，可以使用 MultipleActiveResultSets 连接选项禁用或启用 MARS。  
  
## <a name="procedure"></a>过程  
  
#### <a name="to-disable-mars-support"></a>禁用 MARS 支持  
  
-   使用以下连接选项：  
  
    ```  
    'MultipleActiveResultSets'=>false  
    ```  
  
    如果应用程序尝试在具有开放的活动结果集的连接上执行查询，第二次查询尝试将返回以下错误信息：  
  
    连接无法处理此操作，因为存在具有挂起结果的语句。  若要使该连接可用于其他查询，请提取所有结果、取消或释放该语句。 有关 MultipleActiveResultSets 连接选项的详细信息，请参阅 [Connection Options](../../connect/php/connection-options.md)。  
  
## <a name="example"></a>示例  
以下示例显示如何使用 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的 SQLSRV 驱动程序禁用 MARS 支持。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'MultipleActiveResultSets'=> false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>示例  
以下示例显示如何使用 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的 PDO_SQLSRV 驱动程序禁用 MARS 支持。  
  
```  
<?php  
// Connect to the local server using Windows Authentication and AdventureWorks database  
$serverName = "(local)";   
$database = "AdventureWorks";  
  
try {  
   $conn = new PDO(" sqlsrv:server=$serverName ; Database=$database ; MultipleActiveResultSets=false ", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );   
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
$conn = null;   
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[连接到服务器](../../connect/php/connecting-to-the-server.md)  
  
