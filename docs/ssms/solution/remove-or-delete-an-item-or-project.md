---
title: 移除或删除项或项目
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1f88ef2cd69bcb3beb8729830a35f40232c4bd04
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009653"
---
# <a name="remove-or-delete-an-item-or-project"></a>移除或删除项或项目
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 项目中的项目项为查询、连接和杂项文件。 您可以从解决方案中移除项目查询文件和杂项文件，而并不清除存储区中的文件。 如果项目或项在当前解决方案中不再有用，但是您希望将其包含到其他解决方案中，此时可以将其移除。  
  
### <a name="to-remove-a-project-item"></a>移除项目项  
  
1.  在解决方案资源管理器中，选择想要移除的项目项。  
  
2.  在“编辑”  菜单上，单击“删除”  。  
  
3.  在确认对话框中，单击“删除”  以从项目中删除项。  
  
已移除的项仍存在于文件系统中。 因此，您可以将已移除的项添加到各自的初始解决方案或其他解决方案中。  
  
#### <a name="to-remove-a-project"></a>删除项目  
  
1.  在解决方案资源管理器中，选择想要移除的项目。  
  
2.  在“编辑”  菜单上，单击“删除”  。  
  
3.  在确认对话框中，单击“确定”  以从解决方案中删除项目。  
  
您可以永久删除项目，但是必须先从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 解决方案中移除对该项目的所有引用，然后再使用 [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 资源管理器从存储区中永久删除关联的文件。  
  
#### <a name="to-delete-a-project"></a>删除项目  
  
1.  在解决方案资源管理器中，移除要从解决方案中删除的项目。  
  
2.  在 Windows 资源管理器中，找到并选中与所要删除的项目或项相关联的文件。  
  
3.  在“文件”  菜单上，单击“删除”  。  
  
## <a name="see-also"></a>另请参阅  
[解决方案资源管理器](../../ssms/solution/solution-explorer.md)  
[向项目添加新项](../../ssms/solution/add-new-items-to-a-project.md)  
[向项目中添加现有项](../../ssms/solution/add-existing-items-to-a-project.md)  
  
