---
description: 自动创建自联接 (Visual Database Tools)
title: 创建自动自联接
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 3792e29ae83d28e8c695cfebbd5fc086fe4c267b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468377"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>自动创建自联接 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
如果表在数据库中有自反关系，则可自动将其与自身联接。  
  
### <a name="to-create-a-self-join-automatically"></a>自动创建自联接  
  
1.  将要处理的表添加到 [“关系图”窗格](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) 中。  
  
2.  再次添加同一表，以便“关系图”窗格显示同一表两次。  
  
    [查询和视图设计器](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) 将通过为表名添加一个顺序号来为第二个实例分配别名。 此外，查询和视图设计器还会在表示该表参与查询的两种不同方式的两个矩形之间创建联接线。  
  
## <a name="see-also"></a>另请参阅  
[使用联接进行查询 (Visual Database Tools)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
