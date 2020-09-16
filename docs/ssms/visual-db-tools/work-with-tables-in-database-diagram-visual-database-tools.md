---
description: 使用数据库关系图中的表 (Visual Database Tools)
title: 使用数据库关系图中的表
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], tables
- Table Designer, database diagrams
- tables [SQL Server], database diagrams
- database diagrams [SQL Server], Table Designer
ms.assetid: ee2c5d84-22bf-4597-ac70-a27ed8cc94f4
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 1f947afca06a3f27ae972885b20199917b14862e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459985"
---
# <a name="work-with-tables-in-database-diagram-visual-database-tools"></a>使用数据库关系图中的表 (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
您可以在表设计器或数据库关系图设计器中修改和创建数据库表。  
  
> [!NOTE]  
> 如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) 或 SQL Server 管理对象 (SMO) 对架构进行更改。 使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。 由于您不能删除已发布的对象，因此架构更改将失败。  
  
## <a name="in-this-section"></a>本节内容

[向关系图中添加表 (Visual Database Tools)](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
[向关系图中添加相关的表 (Visual Database Tools)](../../ssms/visual-db-tools/add-related-tables-to-diagrams-visual-database-tools.md)  
  
[保存关系图中所选的表 (Visual Database Tools)](../../ssms/visual-db-tools/save-selected-tables-on-a-diagram-visual-database-tools.md)  
  
[将表从一个数据库关系图复制到另一个数据库关系图 (Visual Database Tools)](../../ssms/visual-db-tools/copy-tables-from-one-database-diagrams-to-another-visual-database-tools.md)  
  
[从数据库关系图中移除表 (Visual Database Tools)](../../ssms/visual-db-tools/remove-tables-from-database-diagrams-visual-database-tools.md)  
  
[映射多对多关系 (Visual Database Tools)](../../ssms/visual-db-tools/map-many-to-many-relationships-visual-database-tools.md)  
  
[绘制自反关系 (Visual Database Tools)](../../ssms/visual-db-tools/draw-reflexive-relationships-visual-database-tools.md)  
  
## <a name="reference"></a>引用

[“添加表”对话框（数据库设计器）(Visual Database Tools)](../../ssms/visual-db-tools/add-table-dialog-box-database-designer-visual-database-tools.md)

## <a name="related-sections"></a>相关章节
