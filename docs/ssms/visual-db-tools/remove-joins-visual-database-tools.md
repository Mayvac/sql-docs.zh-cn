---
title: 删除联接
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 5c96529e6b66d61dcee5fff9c6ba69a9d878d578
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008895"
---
# <a name="remove-joins-visual-database-tools"></a>删除联接 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
如果您不希望表通过内部联接或外部联接进行联接，则可移除它们之间的联接。 例如，希望删除 [查询和视图设计器](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) 在两个表之间自动创建的联接。  
  
> [!NOTE]  
> 从查询中移除联接不会更改数据库中的基础关系。  
  
如果两个联接表都是查询的一部分，而且移除了它们之间的所有联接条件，那么生成的查询结果将变为这两个表的积，即变为 CROSS JOIN。  
  
### <a name="to-remove-a-join"></a>移除联接  
  
-   在“ [关系图](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)”窗格中，选择要删除的联接的联接线，再按 Delete 键。 您可一次选择并删除多个联接线。  
  
查询和视图设计器将删除联接线并相应地更改 [SQL 窗格](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)中的语句。  
  
## <a name="see-also"></a>另请参阅  
[自动联接表 (Visual Database Tools)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[手动联接表 (Visual Database Tools)](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[使用联接进行查询 (Visual Database Tools)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
