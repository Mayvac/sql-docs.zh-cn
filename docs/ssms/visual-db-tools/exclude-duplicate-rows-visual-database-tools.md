---
description: 排除重复行 (Visual Database Tools)
title: 排除重复行
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: fcd3d8c3b45e98c6fe0d46c8f596c1d5ff42a8ac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497150"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>排除重复行 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
如果希望在结果集中看到的值都是唯一的，则可指定要从结果集中排除重复项。  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>从结果集中排除重复行  
  
1.  右键单击“关系图”窗格的背景，再从快捷菜单中选择“属性”****。  
  
2.  在“属性”窗口，单击“DISTINCT 值”****，再将其值设置为“是”****。  
  
    查询和视图设计器将在 SQL 语句中显示列的列表之前插入关键字 DISTINCT。  
  
    > [!NOTE]  
    > 如果使用 DISTINCT 关键字，则可能无法在结果窗格中修改结果集。  
  
## <a name="see-also"></a>另请参阅  
[指定搜索条件 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[对查询结果进行排序和分组 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
