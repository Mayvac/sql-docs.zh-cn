---
title: 移动或删除项（报表管理器）| Microsoft Docs
description: 报表管理器报表服务器将报表及相关项存储在文件夹中。 可以移动或删除项。 报表服务器维护对移动的项的引用。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c02d85c3230502f3360039b132e8328e40d06d28
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987153"
---
# <a name="move-or-delete-an-item-report-manager"></a>移动或删除项（报表管理器）
  发布到报表服务器的报表和与报表相关的项将存储在文件夹中。 您可以将这些项移动到不同文件夹，并且报表服务器自动维护对这些项的引用。 在删除项之前，请注意是否有其他项依赖它。  
  
## <a name="move-an-item"></a>移动项  
 您可以将报表服务器项移动到报表服务器文件夹层次结构中的不同位置。 移动项时，所有属性（包括安全设置）也随之移至新的位置。 移动文件夹时，文件夹中的所有项也随之移动。  
  
 在报表管理器中，可以移动的项会在文件夹层次结构中指明。 下表列出了每种可移动项的图标。  
  
|图标|可移动项|  
|----------|-------------------|  
|![Report icon](../../reporting-services/report-server/media/hlp-16doc.gif "报表图标")|报表|  
|![链接报表图标](../../reporting-services/report-server/media/hlp-16linked.gif "链接报表图标")|链接报表|  
|![文件夹图标](../../reporting-services/report-server/media/hlp-16folder.gif "文件夹图标")|Folder|  
|![通用资源图标](../../reporting-services/report-server/media/hlp-16file.gif "通用资源图标")|一般资源|  
|![Shared data source icon](../../reporting-services/report-data/media/hlp-16datasource.png "共享数据源图标")|共享数据源|  
||共享数据集|  
  
 并非所有使用的项都可以移动。 不能移动与报表相关联的项，例如订阅或报表历史记录。 这些项随其关联报表一起移动。 同样，也不能移动文件夹层次结构之外的项（如共享计划）。 不具备相应权限时不能移动项。 如果您对相关项的角色分配选择了以下任务，则说明已被授予移动相应项的权限：“管理报表”、“管理模型”、“管理文件夹”和“管理数据源”。  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a>从“内容”页中移动项  
  
1.  启动 [报表管理器（SSRS 本机模式）](../web-portal-ssrs-native-mode.md)。  
  
2.  在报表管理器中，导航到 **“内容”** 页，然后找到要移动的项。  
  
3.  悬停在该项之上，然后单击下拉箭头。  
  
4.  在下拉菜单中，单击 **“移动”** 。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  在 **“位置”** 中，指定要将该项移动到的文件夹。 可以键入完全限定文件夹名称，或使用树控件导航到相应的文件夹。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 或者，您也可以导航到要移动的对象，单击 **“属性”** ，再单击该页顶部的 **“移动”** 。  
  
## <a name="delete-an-item"></a>删除项  
 在删除项之前，确定是否有其他项使用该项。 例如，如果您删除了一个共享数据源，则使用该数据源的报表和模型将无法再运行。 删除报表时，也将删除与该报表关联的订阅和报表历史记录。 若要查找项的依赖项，请参阅[“依赖项”页（报表管理器）](../web-portal-ssrs-native-mode.md)。  
  
#### <a name="to-delete-a-report-or-item"></a>删除报表或项  
  
1.  启动 [报表管理器（SSRS 本机模式）](../web-portal-ssrs-native-mode.md)。  
  
2.  在报表管理器中，导航到 **“内容”** 页，然后找到要删除的项。  
  
3.  悬停在该项之上，然后单击下拉箭头。  
  
4.  在下拉菜单中，单击“删除”。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [“内容”页（报表管理器）](/previous-versions/sql/sql-server-2016/ms186470(v=sql.130))   
 [查找、查看和管理报表（报表生成器和 SSRS）](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
