---
title: 基于 XML 列创建视图 | Microsoft Docs
description: 了解如何创建视图，以便在其中使用 xml 数据类型的 value() 方法检索 xml 类型列中的值。
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5d4a9d8d0aa40f8454a2bd0fd089022630c34ca2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85691536"
---
# <a name="create-views-over-xml-columns"></a>对 XML 列创建视图
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  可以使用 **xml** 类型列创建视图。 下面的示例创建了一个视图，在该视图中，使用 `xml` xml **数据类型的** value() **方法检索** 类型列中的值。  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 对此视图执行下面的查询：  
  
```  
SELECT *   
FROM   MyView  
```  
  
 结果如下：  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 关于使用 **xml** 数据类型创建视图，请注意以下几点：  
  
-   可以在具体化视图中创建 xml 数据类型。 具体化视图不能基于 xml 数据类型方法。 但是，它可以转换为不同于基表中的 xml 类型列的 XML 架构集合。  
  
-   不能将 **xml** 数据类型用于分布式分区视图。  
  
-   不会将对视图运行的 SQL 谓词推送到相应视图定义的 XQuery 中。  
  
-   视图中的 XML 数据类型方法不可更新。  
  
  
