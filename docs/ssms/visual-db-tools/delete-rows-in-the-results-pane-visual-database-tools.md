---
title: 删除“结果”窗格中的行
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 71e70000e6a4b1c6208e19f5d233f44fb31b965b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008333"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a>在“结果”窗格中删除行 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
如果希望删除数据库中的记录，请在“结果”窗格中删除相应的行。 如果希望删除所有行，则可以使用“删除”查询。 有关详细信息，请参阅 [创建“删除”查询 (Visual Database Tools)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)。 如果只希望将行从“结果”窗格中移除，请更改查询的条件。 有关详细信息，请参阅 [指定搜索条件 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)。  
  
### <a name="to-delete-a-row-or-rows"></a>删除一行或多行  
  
1.  在“结果”窗格中选中要删除的行左侧的框。  
  
2.  按 Delete。  
  
3.  在要求确认的消息框中单击“是”  。  
  
> [!CAUTION]  
> 以这种方式删除的行将从数据库中永久移除并且不能恢复。  
  
> [!NOTE]  
> 如果所选行中有任意行无法从数据库中删除，则这些行都不会删除，并且系统将显示消息，指示无法删除哪些行。  
  
## <a name="see-also"></a>另请参阅  
[创建“删除”查询 (Visual Database Tools)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)  
[指定搜索条件 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
