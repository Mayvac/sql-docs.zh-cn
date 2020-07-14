---
title: 示例：指定 ELEMENTXSINIL 指令 | Microsoft Docs
description: 了解如何在 SQL 中指定 ELEMENTXSINIL 指令，为 xsi:nil 属性为 true 的 NULL 值生成 XML 元素。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENTXSINIL directive
ms.assetid: bbcb6f9e-a51b-4775-9795-947c9d6d758f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64e44b8f84f2ff4b908556b31b6088a6a2c77c55
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85632512"
---
# <a name="example-specifying-the-elementxsinil-directive"></a>示例：指定 ELEMENTXSINIL 指令
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  当指定 ELEMENT 指令检索以元素为中心的 XML 时，如果列具有 NULL 值，则 EXPLICIT 模式将不生成相应的元素。 另外，也可以指定 ELEMENTXSINIL 指令以请求为 **xsi:nil** 属性设置为 TRUE 值的 NULL 值生成元素。  
  
 以下查询构造包括雇员地址的 XML。 对于 `AddressLine2` 和 `City` 列，列名指定 `ELEMENTXSINIL` 指令。 这将为行集中的 `AddressLine2` 和 `City` 列中的 NULL 值生成元素。  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID  as [Employee!1!EmpID],  
       BEA.AddressID as [Employee!1!AddressID],  
       NULL        as [Address!2!AddressID],  
       NULL        as [Address!2!AddressLine1!ELEMENT],  
       NULL        as [Address!2!AddressLine2!ELEMENTXSINIL],  
       NULL        as [Address!2!City!ELEMENTXSINIL]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.BusinessEntityAddress AS BEA  
    ON E.BusinessEntityID = BEA.BusinessEntityID  
  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       BEA.AddressID,  
       A.AddressID,  
       AddressLine1,   
       AddressLine2,  
       City   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.BusinessEntityAddress AS BEA  
    ON E.BusinessEntityID = BEA.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BEA.AddressID = A.AddressID  
ORDER BY [Employee!1!EmpID],[Address!2!AddressID]  
FOR XML EXPLICIT;  
```  
  
 下面是部分结果：  

```xml
<Employee xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          EmpID="1"
          AddressID="249">
  <Address AddressID="249">
    <AddressLine1>4350 Minute Dr.</AddressLine1>
    <AddressLine2 xsi:nil="true" />
    <City>Minneapolis</City>
  </Address>
</Employee>
...
```
  
## <a name="see-also"></a>另请参阅  
 [将 EXPLICIT 模式与 FOR XML 一起使用](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
