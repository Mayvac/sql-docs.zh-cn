---
title: 在 sql： relationship （SQLXML）上设置 sql：反向特性
description: 了解如何在 sql： relationship 元素上使用 sql：反函数特性来指定 updategram 操作中数据库列之间的关系。
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0bf9f98482ad83d1cf5104f9379ac294f2064c62
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725882"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>在 sql:relationship 上指定 sql:inverse 属性 (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  仅当 XSD 架构用于大容量加载或 updategram 时， **sql：反向**特性才有用。 可在元素上指定**sql：反向**特性 **\<sql:relationship>** 。 在 updategram 中，updategram 逻辑在确定由 updategram 操作更新的表和列时会解释架构。 架构中所指定的父子关系决定了修改（插入或删除）记录的顺序。  
  
 如果在 XSD 架构中指定的父子关系与相应数据库列之间的主键/外键关系顺序相反，则插入或删除 updategram 操作将因主键/外键冲突而失败。 在这种情况下，在元素中指定了**sql：反向**特性（**sql：反函数 = "true"**） **\<sql:relationship>** ，并且 updategram 逻辑逆了架构中指定的父子关系的解释。  
  
 **Sql：反向**属性采用布尔值（0 = false，1 = true）。 可接受的值为 0、1、true 和 false。  
  
 有关使用**sql：反向**批注的工作示例，请参阅[在 Updategram 中指定带批注的映射架构](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。  
  
## <a name="see-also"></a>另请参阅  
 [使用 sql： relationship 指定关系 &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
