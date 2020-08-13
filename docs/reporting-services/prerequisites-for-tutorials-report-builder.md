---
title: 教程先决条件（报表生成器）| Microsoft Docs
description: 了解完成报表生成器教程必须具备的先决条件。
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 27fbd90962370cf3198c53b0c39c5d7886ed943a
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247486"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>教程先决条件（报表生成器）

若要完成报表生成器教程，你需要能够在报表服务器上或与报表服务器集成的 SharePoint 站点上查看和保存 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 分页报表。 对于数据，所有教程都使用必须由 SQL Server 实例处理的文字查询。  
  
如果您无权访问报表服务器或站点或数据源，则可以通过生成脱机报表来了解报表生成器。 请参阅[教程：脱机生成快速图表报表（报表生成器）](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)。  

## <a name="requirements"></a>要求

若要完成“报表生成器”教程，您必须满足下列先决条件：  
  
-   对报表生成器的访问权限。 可以在 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 报表服务器上或 SharePoint 集成模式下的 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 报表服务器上运行报表生成器。 在其他服务器上只有第一步不同，即如何打开报表生成器。  
  
    在报表服务器上，选择“新建” > “分页报表” 。
  
    在 SharePoint 集成模式下的报表服务器上，在“文档”选项卡上选择“新建文档”，然后从下拉列表中，选择“报表生成器报表”************。 例如，`https://<servername>/sites/mySite/reports`。 SharePoint 管理员必须为每个文档库启用“报表生成器报表”功能。  
  
-   指向 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 报表服务器或与 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 报表服务器集成的 SharePoint 站点的 URL。 您必须拥有保存和查看报表、共享数据源、共享数据集、报表部件和模型的权限。 默认情况下，报表服务器的 URL 是 `https://<servername>/reportserver`。 默认情况下，SharePoint 站点的 URL 是 `https://<sitename>` 或 `https://<server>/site`。  
  
-   SQL Server 实例的名称和足以对任何数据库进行只读访问的凭据。 各教程中的数据集查询使用文字数据，但必须由 SQL Server 实例处理每个查询以返回报表数据集所必需的元数据。 例如，以下连接字符串仅指定一个服务器： `data source=<servername>`。 您必须对默认数据库具有读取权限，该权限是由授予您对服务器的访问权限的系统管理员分配给您的。 您还可以指定数据库，如以下连接字符串中所示： `data source=<servername>;initial catalog=<database>`。  
  
-   对于[教程：地图报表（报表生成器）](tutorial-map-report-report-builder.md)，报表服务器必须配置为支持将必应地图用作背景。 有关详细信息，请参阅 [计划地图报表支持](https://msdn.microsoft.com/5ddc97a7-7ee5-475d-bc49-3b814dce7e19)。   

-   [教程：生成钻取报表和主报表（报表生成器）](tutorial-creating-drillthrough-and-main-reports-report-builder.md)教程要求有权访问 Contoso Sales 多维数据集。 有关详细信息，请参阅该教程。 
  
报表服务器管理员必须向你授予对报表服务器的必要权限，配置 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 文件夹位置，并且配置报表生成器默认选项。 有关详细信息，请参阅 [Install Report Builder](install-windows/install-report-builder.md)。  

## <a name="next-steps"></a>后续步骤

[报表生成器教程](../reporting-services/report-builder-tutorials.md)  

更多疑问？ [请访问 Reporting Services 论坛](https://go.microsoft.com/fwlink/?LinkId=620231)
