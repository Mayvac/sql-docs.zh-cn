---
title: PDOStatement::bindValue | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89126d696f7210132adb5ef10ec557604ebc543f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993120"
---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

将某个值绑定到 SQL 语句中的命名占位符或问号占位符。  
  
## <a name="syntax"></a>语法  
  
```  
  
bool PDOStatement::bindValue($parameter, $value[, $data_type]);  
```  
  
#### <a name="parameters"></a>parameters  
$parameter：（混合）参数标识符  。 对于使用命名占位符的语句，使用参数名 (:name)。 对于使用问号语法的已准备的语句，为基于 1 的参数索引。
  
$value：要绑定到参数的（混合）值  。  
  
$data_type：由 PDO::PARAM_* 常量表示的可选（整数）数据类型  。 默认值为 PDO::PARAM_STR。  
  
## <a name="return-value"></a>返回值  
如果成功，则为 TRUE；否则为 FALSE。  
  
## <a name="remarks"></a>备注  
  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  
  
## <a name="example"></a>示例  
本示例显示，在绑定 $contact 的值后，更改该值不会更改在查询中传递的值。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```

> [!NOTE]
> 当由于 PHP 的[浮点数](https://php.net/manual/en/language.types.float.php)具有有限精确度而将值绑定到[十进制或数值列](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql)以确保精确度和准确度时，建议将字符串用作输入。 这同样适用于 bigint 列，尤其是在值超出[整数](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)范围的情况下。

## <a name="example"></a>示例  
此代码示例演示如何将十进制值作为输入参数进行绑定。  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```
  
## <a name="see-also"></a>另请参阅  
[PDOStatement 类](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
