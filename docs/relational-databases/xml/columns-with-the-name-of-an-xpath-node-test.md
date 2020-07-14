---
title: 列名为 XPath 节点测试的列 | Microsoft Docs
description: 了解当 SQL 查询包含名称为 XPath 节点测试的列（如 text() 或 comment()）时，如何映射 XML 内容。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2605e407cabf004ba05d48fca092a7db269ecacd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85692314"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a>列名为 XPath 节点测试的列
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  如果列名是某个 XPath 节点测试，将如下表所示映射该列的内容。 如果列名是某个 XPath 节点测试，则该列的内容将映射到相应的节点。 如果该列的 SQL 类型是 **xml**，将返回一个错误。  
  
|列名|行为|  
|-----------------|--------------|  
|text()|对于名为 text() 的列，该列中的字符串值将被添加为文本节点。|  
|comment()|对于名为 comment() 的列，该列中的字符串值将被添加为 XML 注释。|  
|node()|对于名为 node() 的列，结果与列名为通配符 (*) 时相同。|  
|处理指令（名称）|如果列名为处理指令，该列中的字符串值将被添加为此处理指令目标名称的 PI 值。|  
  
 以下查询显示用作列名的节点测试。 它在得到的 XML 中添加文本节点和注释。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 结果如下：  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>Sánchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a>另请参阅  
 [将 PATH 模式与 FOR XML 一起使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
