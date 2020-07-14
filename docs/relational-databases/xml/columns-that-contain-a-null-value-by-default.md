---
title: 默认情况下包含 Null 值的列 | Microsoft Docs
description: 了解如何使用 SQL 中的 ELEMENTS XSINIL 关键字短语来处理默认包含 Null 值的列。
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d6962f6117a857ed5875d503c259b4d54e8dd84d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775602"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>默认情况下包含 Null 值的列

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

默认情况下，列中的 Null 值映射为“缺少相应的属性、节点或元素”。 可以使用 ELEMENTS XSINIL 关键字短语重写此默认行为。 此短语请求以元素为中心的 XML。 这意味着在返回的结果中显式指示 null 值。 这些元素不具有值。

以下 Transact-SQL SELECT 示例显示了 ELEMENTS XSINIL 短语。

```sql
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
  AND  E.EmployeeID=1
FOR XML PATH, ELEMENTS XSINIL;
```  
  
 下面显示了结果。 请注意，如果未指定 XSINIL，将缺少 <`Middle`> 元素。  
  
```xml
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>另请参阅  
 [将 PATH 模式与 FOR XML 一起使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
