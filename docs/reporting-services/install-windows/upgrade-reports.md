---
description: 升级报表 (SSRS)
title: 升级报表 | Microsoft Docs
ms.date: 06/04/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], upgrading
- published reports [Reporting Services], upgrades
- custom report items, upgrading
- Reporting Services, upgrades
- upgrading Reporting Services
- snapshots [Reporting Services], upgrading
- report definition files [Reporting Services]
- .rdl files
ms.assetid: a1a10c67-7462-4562-9b07-a8822188a161
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1454c579739c892cc3d0c03211283589ba3e6b82
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446019"
---
# <a name="upgrade-reports-ssrs"></a>升级报表 (SSRS)

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

报表定义 (.rdl) 文件通过以下方式自动升级：  
  
-   在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的报表设计器中打开分页报表时，报表定义将升级到当前支持的 RDL 架构。 当在项目属性中指定某一 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 报表服务器时，报表定义将保存在与目标服务器兼容的架构中。  
  
-   将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装升级到 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 安装时，已发布到报表服务器的现有报表和快照将在第一次进行处理时编译并自动升级为新的架构。 如果报表不能自动升级，则将使用向后兼容模式处理报表。 报表定义保留在原始架构中。  
  
 在本地或在报表服务器上升级报表后，您可能注意到出现附加的错误、警告和消息。 这是对内部报表对象模型和处理组件进行更改的结果，当在报表中检测到根本问题时，将导致出现这些消息。 有关详细信息，请参阅 [Reporting Services Backward Compatibility](../../reporting-services/reporting-services-backward-compatibility.md)。  
  
 有关 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 的新功能的详细信息，请参阅 [SQL Server Reporting Services (SSRS) 中的新增功能](../what-s-new-in-sql-server-reporting-services-ssrs.md)。  

##  <a name="versions-supported-by-upgrade"></a><a name="bkmk_versionsupported"></a> 能够升级的版本  
 在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 早期的任一版本中创建的报表都可以升级。 包括下列版本：  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
##  <a name="report-definition-rdl-files-and-report-designer"></a><a name="bkmk_rdlfiles"></a> 报表定义 (.rdl) 文件和报表设计器  
 报表定义文件包括对 RDL 命名空间的引用，该命名空间指定了用于验证 .rdl 文件的报表定义架构的版本。  
  
 当您在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的报表设计器中打开某个 .rdl 文件时，如果报表是针对先前命名空间创建的，报表设计器会自动创建一个备份文件，并将该报表升级到当前命名空间。 这是升级报表定义文件的唯一方法。  
  
 您设置的部署属性可以影响保存报表定义文件的架构。 有关详细信息，请参阅 [SQL Server Data Tools 中的部署和版本支持 (SSRS)](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)中。  
  
 可以将在早期版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中创建的 .rdl 文件上载到新版本，该报表将在第一次使用时自动升级。 报表服务器将以原始格式存储报表定义文件。 报表将在第一次被查看时自动升级，但是存储的报表定义文件仍保持不变。  
  
 若要为报表、报表服务器或报表设计器标识当前 RDL 架构，请参阅[查找报表定义架构版本 (SSRS)](../../reporting-services/reports/find-the-report-definition-schema-version-ssrs.md)。  
  
##  <a name="published-reports-and-report-snapshots"></a><a name="bkmk_publishedreports_and_snapshots"></a> 已发布的报表和报表快照  
 第一次使用时，报表服务器会尝试将现有的已发布报表和报表快照升级为新的报表定义架构，不需要您执行特定操作。 当用户查看报表或报表快照时，或者当报表服务器处理订阅时，将尝试进行升级。 报表定义不会被替换，而是继续存储在它在报表服务器上的原始架构中。 如果报表不能升级，则报表将在向后兼容模式下运行。  
  
##  <a name="backward-compatibility-mode"></a><a name="bkmk_backcompat"></a> 向后兼容模式  
 成功升级的报表由 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表处理器进行处理。 无法升级的报表是由 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表处理器在向后兼容性模式下处理。 一个报表不能同时由这两个报表处理器来处理。 第一次使用时，报表将成功升级或标记为向后兼容。  
  
 只有 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表处理器才支持新功能。 如果报表不能升级，您仍然可以查看呈现的报表，但不能使用新功能。 若要利用新功能，必须成功地升级报表。  
  
##  <a name="upgrading-a-report-with-subreports"></a><a name="bkmk_subreports"></a> 使用子报表升级报表  
 当报表中包含子报表时，升级过程中会出现四种可能的状态之一：  
  
-   主报表和所有子报表都能成功地升级。 它们由 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表处理器来处理。  
  
-   主报表和所有子报表都不能升级。 它们是由 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表处理器处理。  
  
-   主报表可以升级，但一个或多个子报表不能升级。 主报表由 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表处理器处理，但呈现的报表在不能升级的子报表将出现的位置显示消息“错误: 无法处理子报表”。  
  
-   主报表不能升级，但一个或多个子报表可以升级。 主报表由 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表处理器处理，但呈现的报表在子报表将出现的位置显示消息“错误: 无法处理子报表”。  
  
 如果看到错误“错误: 无法处理子报表”，则必须更改主报表或子报表的定义，以便可以由报表处理器的同一版本处理报表。  
  
 钻取报表没有此限制，因为它们被作为独立的报表处理。  
  
##  <a name="upgrading-a-report-with-custom-report-items"></a><a name="bkmk_CRIs"></a> 使用自定义报表项升级报表  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表可能包含第三方软件供应商提供的自定义报表项 (CRI)，系统管理员将这些项安装在报表创作计算机和报表服务器上。 可以按以下方式升级包含 CRI 的报表：  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器升级为 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表服务器。 在首次使用时自动升级报表服务器上的已发布报表。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表上传到 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表服务器。 报表将在首次使用时自动升级。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的报表设计器中打开。 将创建原始报表的一个备份副本。 发生以下两种情况之一：  
  
    1.  报表中的所有 CRI 没有不受支持的功能。 CRI 将转换为新报表定义架构中的报表项，以便升级整个报表。 如果保存该文件，则它将保存在当前 RDL 命名空间中。  
  
    2.  报表中的一个或多个 CRI 具有不受支持的功能。 出现一个对话框，提示用户是转换这些 CRI 还是将它们保留不变。  
  
     有关详细信息，请参阅本主题后面的 [在报表设计器中打开报表](#OpeningaReport) 。  
  
 有关为报表服务器、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 或报表标识当前 RDL 命名空间的信息，请参阅[查找报表定义架构版本 (SSRS)](../../reporting-services/reports/find-the-report-definition-schema-version-ssrs.md)。  
  
### <a name="upgrading-reports-on-a-report-server"></a>升级报表服务器上的报表  
 当 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表第一次在已升级为 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表服务器的报表服务器上运行时，报表自动升级为报表服务器当前支持的报表定义命名空间。 报表可能在升级前就已存在于报表服务器上，或报表可能已通过 Web 门户上传，或已从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中的报表设计器发布到报表服务器。  
  
 下表列出由报表服务器为报表中特定类型的 CRI 执行的升级操作。  
  
|CRI 类型|报表服务器升级操作|  
|--------------|----------------------------------|  
|第三方 CRI|不执行升级。<br /><br /> 由 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表处理器进行处理。|  
  
###  <a name="opening-a-report-with-cris-in-report-designer"></a><a name="OpeningaReport"></a> 在报表设计器中使用 CRI 打开报表  
 在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中使用报表设计器中的 CRI 打开 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表时，报表将升级到新的报表定义架构。 根据报表中包含的 CRI，将执行下列操作之一：  
  
-   检测到第三方 CRI。 如果安装在报表创作计算机上的 CRI 的版本与新的 RDL 架构不兼容，则设计图面将显示带有红色 X 的文本框。您必须与系统管理员联系，以便从与新的 RDL 架构兼容的第三方供应商那里安装新版本的 CRI。  
  
 在报表创作环境中升级报表后将其保存，这是将现有报表升级到新的报表定义架构的唯一方式。  
  
###  <a name="convert-cri-dialog-box"></a><a name="bkmk_convertCRIdialog"></a> “转换 CRI”对话框  
 该报表包含其中有不受支持的功能的自定义报表项 (CRI)。 CRI 是对报表定义语言 (RDL) 的扩展，它支持用于显示报表中的数据的自定义对象。 CRI 包含由第三方软件供应商提供的设计时和运行时组件。  
  
> [!NOTE]  
>  对于是否选择在报表服务器上支持自定义报表项，需要由系统管理员决定。 若要查看报表中的 CRI，必须将 CRI 组件安装在报表创作客户端上以预览报表，并将其安装在报表服务器上以查看已发布或上载的报表。 有关详细信息，请参阅 [自定义报表项](../../reporting-services/custom-report-items/custom-report-items.md) 和第三方软件供应商的文档。  
  
 某些 CRI 可以转换为采用新的报表定义格式的报表项。 使用下表可以决定是否转换该报表中的 CRI：  
  
-   **是** 选择 **“是”** 将转换报表中所有可以转换的 CRI。 无法升级 CRI 中不受支持的功能，也不能从报表定义文件中删除它们。 查看报表时，可能看到 CRI 在报表中的显示方式存在差异。  
  
-   **否** ：如果不希望转换报表中的 CRI，请选择 **“否”** 。 当前版本中的报表处理器无法显示这些 CRI。 如果您的系统管理员计划安装从第三方软件供应商那里得到的且与新报表定义格式兼容的新版本 CRI，则应当选择 **“否”**。 在使用新版本以前，CRI 将作为带有红色 X 的空文本框显示在报表中。  
  
 在这两种情况下，报表都将升级为采用新的报表定义格式，并且原始报表的备份副本会另存为 *\<Report Name>* `-` Backup.rdl。 如果在报表创作工具中保存报表，则会以新的报表定义格式保存升级的报表。 如果发布报表，则报表首先保存在您的计算机上，然后发布到报表服务器。 您需要将报表的升级版本发布到报表服务器。  
  
 如果不保存报表，则原始报表将保持不变。 但是，不能在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的 SQL Server 2016 版本中或者在使用较新报表定义格式的报表创作环境中编辑该报表。 对于报表的原始版本，通过使用 Web 门户将它上载到 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 报表服务器，可以继续运行它。 有关详细信息，请参阅 [Web 门户](../../reporting-services/web-portal-ssrs-native-mode.md)。  
  
 对于上载而不是发布到报表服务器的报表，报表处理器将在第一次使用该报表时确定是否可以将它升级。 对于无法升级的报表，将以向后兼容模式对其进行处理，并像在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的早期版本中那样继续显示它们。  

## <a name="next-steps"></a>后续步骤

[升级和迁移 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[SQL Server 2016 的 SQL Server Reporting Services 中的重大更改](../breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)   
[SQL Server 2016 中 SQL Server Reporting Services 的行为更改](../behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
[SQL Server 2016 的 SQL Server Reporting Services 中停止使用的功能](../../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
[自定义报表项](../../reporting-services/custom-report-items/custom-report-items.md)   
[升级报表服务器数据库](../../reporting-services/install-windows/upgrade-a-report-server-database.md)  

更多疑问？ [请访问 Reporting Services 论坛](https://go.microsoft.com/fwlink/?LinkId=620231)
