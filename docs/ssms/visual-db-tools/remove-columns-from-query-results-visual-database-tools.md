---
title: 从查询结果中删除列
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- result sets [SQL Server], queries
- removing columns
- results [SQL Server], query
- deleting columns
- queries [SQL Server], results
ms.assetid: a7de7a87-4249-49bd-863d-dc0b40a49e78
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: a8b69a12cd11006b00cabcffd6b3c2f6112bffc5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999462"
---
# <a name="remove-columns-from-query-results-visual-database-tools"></a>从查询结果中删除列 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
如果在“选择”查询中使用某列，但不希望在结果集中显示该列（即不希望它显示在查询的选择列表中），则可将其从输出中移除。 从查询的输出中移除该列后，您仍可在搜索条件中使用它或将其用作排序字段。  
  
> [!NOTE]  
> 如果希望从查询中完全删除某一列，请参阅 [从查询中删除列 (Visual Database Tools)](../../ssms/visual-db-tools/remove-columns-from-queries-visual-database-tools.md)。  
  
### <a name="to-remove-a-column-from-the-query-output"></a>从查询输出中移除列  
  
-   在“条件”  窗格中，对于要删除的数据列，清除“输出”  列中的复选框。 （如果希望将该列添加回查询输出中，可再次选中“输出”  列。）  
  
    -或-  
  
-   将该列从 [SQL 窗格](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)的输出列表中删除。  
  
## <a name="see-also"></a>另请参阅  
[向查询中添加列 (Visual Database Tools)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[从查询中删除列 (Visual Database Tools)](../../ssms/visual-db-tools/remove-columns-from-queries-visual-database-tools.md)  
[对查询结果进行排序和分组 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[汇总查询结果 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[执行基本的查询操作 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
