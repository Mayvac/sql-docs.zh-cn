---
title: PDOStatement::rowCount
description: Microsoft PDO_SQLSRV Driver for PHP for SQL Server 中 PDOStatement::rowCount 函数的 API 参考。
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0569f26a-2376-4c20-8813-bd3c87d0ae9f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31671bc3db85a31cde4109cedb11f3ab44f07ea1
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646577"
---
# <a name="pdostatementrowcount"></a>PDOStatement::rowCount
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

返回由最后一个语句添加、删除或更改的行数。  
  
## <a name="syntax"></a>语法  
  
```  
  
int PDOStatement::rowCount ();  
```  
  
## <a name="return-value"></a>返回值  
已添加、删除或更改的行数。  
  
## <a name="remarks"></a>注解  
如果由相关联的 PDOStatement 执行的最后一个 SQL 语句为 SELECT 语句，PDO::CURSOR_FWDONLY 光标将返回 -1。 PDO::CURSOR_SCROLLABLE 光标返回结果集中的行数。  
  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  
  
## <a name="example"></a>示例  
本示例显示两次使用了 rowCount。 第一次使用返回已添加到表中的行数。 第二次使用表明当你指定可滚动光标时，rowCount 可以返回结果集中的行数。  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table2(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
  
echo "\n\n";  
  
$con = null;  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
print $stmt->rowCount();  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[PDOStatement 类](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
