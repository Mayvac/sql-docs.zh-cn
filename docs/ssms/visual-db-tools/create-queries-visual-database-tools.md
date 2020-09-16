---
description: 创建查询 (Visual Database Tools)
title: 创建查询
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: fc2206e180c922f816337545a491af7bf8b2f461
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468388"
---
# <a name="create-queries-visual-database-tools"></a>创建查询 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
使用查询，您可以从数据库的表和视图中检索数据。 在“查询和视图设计器”**** 中创建和使用查询，该窗口由四个窗格组成：[“关系图”窗格](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)、[“SQL”窗格](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)、[“条件”窗格](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)和[“结果”窗格](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)。  
  
### <a name="to-create-a-new-query"></a>创建新查询  
  
1.  在“对象资源管理器”**** 中，展开要查询的数据库的“表”**** 节点。 右键单击要查询的表，再单击“打开表”****。  
  
2.  若要向查询添加更多表，请在“查询设计器”菜单中，选择“添加表”****。  
  
    > [!NOTE]  
    > 如果没有看到“关系图”****、“SQL”****、“条件”**** 或“结果”**** 窗格，请在“查询设计器”菜单中指向“窗格”****，再单击要打开的窗格。  
  
3.  在“添加表”**** 对话框中，选择要查询的表，再对每个表单击“添加”****。  
  
4.  添加完要查询的所有表之后，单击“关闭”****。  
  
    若要在以后添加更多表，请右键单击“关系图”**** 窗格中的空白位置，然后在快捷菜单中单击“添加表”****。  
  
5.  在“关系图”**** 窗格中，对于要查询的每个列，选中其表值对象中的复选框。  
  
6.  在“查询设计器”菜单中，选择“执行 SQL”**** 以运行查询。  
  
若要进一步改进查询，可以在“SQL”**** 窗格中更改 SQL 代码，或者在“条件”**** 窗格中选择排序顺序和列别名等选项。  
  
## <a name="see-also"></a>另请参阅  
[保存查询 (Visual Database Tools)](../../ssms/visual-db-tools/save-queries-visual-database-tools.md)  
[查询类型 (Visual Database Tools)](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
[指定搜索条件 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[汇总查询结果 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[执行基本的查询操作 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
