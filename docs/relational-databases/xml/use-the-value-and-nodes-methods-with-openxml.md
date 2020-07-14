---
title: 将 value() 和 nodes() 方法用于 OPENXML | Microsoft Docs
description: 了解如何使用 value() 和 nodes() 方法或 OpenXML() 方法提取 SQL 查询中 XML 值的行集。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- OpenXML method [XML in SQL Server]
- value method [XML in SQL Server]
- nodes method [XML in SQL Server]
ms.assetid: c73dbe55-d685-42eb-b0ee-9f3c5b9d97f3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a719b990c78af4429958fffb6027daf5d578a682
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738371"
---
# <a name="use-the-value-and-nodes-methods-with-openxml"></a>将 value() 和 nodes() 方法用于 OPENXML
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  你可以在 **SELECT** 子句中对 **xml** 数据类型使用多个 **value()** 方法以生成所提取值的行集。 **nodes()** 方法为可用于其他查询的每个所选节点生成一个内部引用。 生成行集时，如果行集有多个列且用于生成行集的路径表达式比较复杂，结合使用 **nodes()** 和 **value()** 方法可能会更有效。  
  
 **nodes()** 方法生成特殊的 **xml** 数据类型的实例，每个实例都将其上下文设置为不同的选定节点。 这种 XML 实例支持 **query()** 、**value()** 、**nodes()** 和 **exist()** 方法，并可在 **count(\*)** 聚合中使用。 所有其他用法都会导致错误。  
  
## <a name="example-using-nodes"></a>示例：使用 nodes()  
 假定您希望提取作者的名字和姓氏，而名字不是“David”。 此外，您希望提取该信息作为一个包含两列 FirstName 和 LastName 的行集。 通过使用 **nodes()** 方法和 **value()** 方法便可以完成该操作，如下所示：  
  
```  
SELECT nref.value('(first-name/text())[1]', 'nvarchar(50)') FirstName,  
       nref.value('(last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T CROSS APPLY xCol.nodes('//author') AS R(nref)  
WHERE  nref.exist('first-name[. != "David"]') = 1  
```  
  
 在此示例中， `nodes('//author')` 生成一个由对每个 XML 实例的 `<author>` 元素引用组成的行集。 通过计算与那些引用相关的 **value()** 方法，即可获得作者的名字和姓氏。  
  
 SQL Server 2000 提供了通过使用 **OpenXml()** 从 XML 实例生成行集的功能。 您可以指定行集的关系架构，以及如何将 XML 实例中的值映射到行集中的列。  
  
## <a name="example-using-openxml-on-the-xml-data-type"></a>示例：对 xml 数据类型使用 OpenXml()  
 可以通过使用 **OpenXml()** 重写上一个示例中的查询，如下所示。 方法是创建一个游标，该游标将每个 XML 实例读取到 XML 变量，然后向其应用 OpenXML：  
  
```  
DECLARE name_cursor CURSOR  
FOR  
   SELECT xCol   
   FROM   T  
OPEN name_cursor  
DECLARE @xmlVal XML  
DECLARE @idoc int  
FETCH NEXT FROM name_cursor INTO @xmlVal  
  
WHILE (@@FETCH_STATUS = 0)  
BEGIN  
   EXEC sp_xml_preparedocument @idoc OUTPUT, @xmlVal  
   SELECT   *  
   FROM   OPENXML (@idoc, '//author')  
          WITH (FirstName  varchar(50) 'first-name',  
                LastName   varchar(50) 'last-name') R  
   WHERE  R.FirstName != 'David'  
  
   EXEC sp_xml_removedocument @idoc  
   FETCH NEXT FROM name_cursor INTO @xmlVal  
END  
CLOSE name_cursor  
DEALLOCATE name_cursor   
```  
  
 **OpenXml()** 创建一个内存中的表示形式，并且使用工作表而不是查询处理器。 它依赖于 MSXML 3.0 版的 XPath 1.0 版处理器，而不是 XQuery 引擎。 工作表在对 **OpenXml()** 的多个调用间不共享（即使是在同一个 XML 实例上）。 这就限制了它的可伸缩性。 在未指定 WITH 子句时，可以通过**OpenXml()** 访问 XML 数据的边缘表格式。 另外，也可以通过它在单独的“overflow”列中使用其余的 XML 值。  
  
 将 **nodes()** 和 **value()** 函数结合起来可有效地使用 XML 索引。 因此，与 **OpenXml**相比，这种结合有更高的可伸缩性。  
  
## <a name="see-also"></a>另请参阅  
 [OPENXML (SQL Server)](../../relational-databases/xml/openxml-sql-server.md)  
  
  
