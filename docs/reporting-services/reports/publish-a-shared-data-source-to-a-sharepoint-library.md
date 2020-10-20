---
title: 将共享数据源发布到 SharePoint 库 | Microsoft Docs
description: 了解如何将共享数据源发布到以 SharePoint 集成模式运行的报表服务器。
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0a60966d6ba73a7669562d406b460f749303ca56
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988599"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a>将共享数据源发布到 SharePoint 库
  若要将共享数据源发布到在 SharePoint 集成模式下运行的报表服务器，必须在报表设计器中设置报表的项目属性。 在项目属性中，对服务器、报表和共享数据源的所有引用都必须为完全限定的 URL。  
  
 必须对 SharePoint 站点拥有 **“成员”** 或 **“所有者”** 权限。 有关详细信息，请参阅 [用于 SharePoint 模式下在报表服务器上已发布的报表项的 URL 示例 (SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)。  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a>将共享数据源发布到 SharePoint 站点。  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开现有的或新的报表服务器项目。  
  
2.  在 **“项目”** 菜单上，单击 **“属性”** 。 打开 \<project>“属性页”对话框。  
  
3.  选择发布到 SharePoint 站点所用的 **“配置”** 。  
  
4.  如果想在项目中发布共享数据源，并覆盖以前发布的共享数据源，请将 **OverwriteDataSources** 设置为 **True**。  
  
5.  （可选）对于 **TargetDataSourceFolder**，键入指向 SharePoint 库或库文件夹的 URL。 例如，`https://TestServer/TestSite/Documents/DataSources` 。  
  
     如果不指定值，将使用 **TargetReportFolder** 值。  
  
6.  对于 **TargetReportFolder**，键入指向库或库文件夹的 URL。 例如，`https://TestServer/TestSite/Documents/Reports` 。  
  
7.  对于 **TargetServerURL**，键入指向 SharePoint 顶级站点或子站点的 URL。 如果不指定站点，将使用默认顶级站点。 例如，`https://servername`、`https://servername/site` 或 `https://servername/site/subsite`。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. 在解决方案资源管理器中，右键单击要发布的共享数据源，然后单击“部署”  。 数据源将发布到 **TargetDataSourceFolder**中指定的位置。 部署错误将显示在输出窗口中。  
  
    > [!NOTE]  
    >  将共享数据源发布到 SharePoint 站点后，该数据源文件的扩展名会更改为 .rsds。 可以直接在 SharePoint 站点上编辑和管理共享数据源。 有关详细信息，请参阅[创建和管理共享数据源（SharePoint 集成模式下的 Reporting Services）](/previous-versions/sql/)。  
  
## <a name="see-also"></a>另请参阅  
 [将报表发布到 SharePoint 库](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [SharePoint 模式下的报表服务器上已发布报表项的 URL 示例 (SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [“项目属性页”对话框](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [设置部署属性 (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [将报表发布到报表服务器](../../reporting-services/reports/publishing-reports-to-a-report-server.md)   
 [将 Office 数据连接 (.odc) 用于报表（SharePoint 集成模式下的 Reporting Services）](../../reporting-services/report-data/use-an-office-data-connection-odc-with-reports.md)  
  
