---
title: 将 PATH 模式与 FOR XML 一起使用 | Microsoft Docs
description: 了解如何将 PATH 模式与嵌套的 FOR XML 查询和 TYPE 指令一起使用，以编写返回 XML 类型实例的复杂度较低的查询。
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff6beee153a5f923178436710d1b38b1151d6c7d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724539"
---
# <a name="use-path-mode-with-for-xml"></a>将 PATH 模式与 FOR XML 一起使用
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  如 [使用 FOR XML 构造 XML](../../relational-databases/xml/for-xml-sql-server.md)中所述，PATH 模式提供了一种较简单的方法来混合元素和属性。 PATH 模式还是一种用于引入附加嵌套来表示复杂属性的较简单的方法。 尽管您可以使用 FOR XML EXPLICIT 模式查询从行集构造这种 XML，但 PATH 模式为可能很麻烦的 EXPLICIT 模式查询提供了一种较简单的替代方法。 通过 PATH 模式，以及用于编写嵌套 FOR XML 查询的功能和返回 **xml** 类型实例的 TYPE 指令，您可以编写简单的查询。  
  
 在 PATH 模式中，列名或列别名被作为 XPath 表达式来处理。 这些表达式指明了如何将值映射到 XML。 每个 XPath 表达式都是一个相对 XPath，它提供了项类型（例如属性、元素和标量值）以及将相对于行元素而生成的节点的名称和层次结构。  
  
 本节介绍了如何在各种条件下映射行集中的列，并提供了相关示例。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [没有名称的列](../../relational-databases/xml/columns-without-a-name.md)  
  
-   [具有名称的列](../../relational-databases/xml/columns-with-a-name.md)  
  
-   [名称指定为通配符的列](../../relational-databases/xml/columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [列名为 XPath 节点测试的列](../../relational-databases/xml/columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [带有指定为 data() 的路径的列名](../../relational-databases/xml/column-names-with-the-path-specified-as-data.md)  
  
-   [默认情况下包含 Null 值的列](../../relational-databases/xml/columns-that-contain-a-null-value-by-default.md)  
  
-   [PATH 模式中的命名空间支持](../../relational-databases/xml/namespace-support-in-path-mode.md)  
  
-   [示例：使用 PATH 模式](../../relational-databases/xml/examples-using-path-mode.md)  
  
## <a name="see-also"></a>另请参阅  
 [使用 WITH XMLNAMESPACES 将命名空间添加到查询](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md)  
  
  
