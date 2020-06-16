---
title: Web 应用程序要求
description: 了解安装和运行 Internet Information Services 承载 Master Data Services web 应用程序的要求。
ms.custom: ''
ms.date: 02/13/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
keywords:
- master data services
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6e5e80c3e4e9437efa41b43e7bf6469d06432745
ms.sourcegitcommit: 7d6eb09588ff3477cf39a8fd507d537a603bc60d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2020
ms.locfileid: "84796261"
---
# <a name="web-application-requirements-master-data-services"></a>Web 应用程序要求 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 是 Internet Information Services (IIS) 托管的 Web 应用程序。 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 仅适用于 Internet Explorer (IE) 9 或更高版本。 IE 8 及早期版本、Microsoft Edge 和 Chrome 均不受支持。  

有关如何安装和配置 IIS 的说明****，请参阅[安装和配置 IIS](../../master-data-services/master-data-services-installation-and-configuration.md#InstallIIS)。
  
 使用 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 可以创建和配置 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序。 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 在本地计算机上配置 IIS，因此适用于初始 Web 配置任务。 例如，配置具有单个 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 应用程序的 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 环境，或在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]的扩展部署中配置第一个 Web 应用程序。 使用 IIS 工具来执行一些更复杂的任务，如在扩展部署中配置多个 Web 服务器。  
  
> [!NOTE]  
>  您安装 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 组件的任何计算机必须具有许可证。 有关详细信息，请参阅“最终用户许可协议 (EULA)”。  
  
## <a name="requirements"></a>要求  
  
### <a name="operating-system"></a>操作系统  
 安装 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]之前，请首先查看以下要求：    
    
-   [安装 SQL Server 2016 的硬件和软件要求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)    
  
### <a name="microsoft-silverlight"></a>Microsoft Silverlight  
 在使用 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 应用程序时，Silverlight 5 必须安装在客户端计算机上。 如果您不具有所需版本的 Silverlight，则在您导航到需要 Silverlight 的 Web 应用程序区域时，系统将提示您安装 Silverlight。 可以从[此处安装 Silverlight 5](https://go.microsoft.com/fwlink/?LinkId=243096)。  
  
### <a name="role-and-role-services"></a>角色和角色服务  
 在 Windows Server 2012 或 Windows Server 2012 R2 中，可以使用“服务器管理器”****（在 Microsoft 管理控制台 (MMC) 中提供）来安装“Web 服务器 (IIS)”**** 角色和必需的角色服务。  
 
 
> [!IMPORTANT]  
>默认情况下，已启用“动态内容压缩”**** 。 这极大地减少了 xml 响应的大小，并可节省网络 I/O，不过会增加 CPU 使用率。  有关详细信息，请参阅 [Master Data Services (MDS) 中的新增功能](../../master-data-services/what-s-new-in-master-data-services-mds.md)中的 **[CTP 2.0] 改进的功能**。  
  
||  
|-|  
|Internet Information Services<br /><br /> Web 管理工具<br /><br /> IIS 管理控制台<br /><br /> 万维网服务<br /><br /> 应用程序开发<br /><br /> .NET Extensibility 3.5<br /><br /> .NET Extensibility 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> ISAPI 扩展插件<br /><br /> ISAPI 筛选器<br /><br /> 常见的 HTTP 功能<br /><br /> 默认文档<br /><br /> 目录浏览<br /><br /> HTTP 错误<br /><br /> 静态内容<br /><br /> [注意：请不要安装 WebDAV 发布]<br /><br /> 运行状况和诊断<br /><br /> HTTP 日志记录<br /><br /> 请求监视器<br /><br /> 性能<br /><br /> 静态内容压缩<br /><br /> 安全性<br /><br /> 请求筛选<br /><br /> Windows 身份验证|  
  
### <a name="features"></a>功能 
 在 Windows Server 2012 和 Windows Server 2012 R2 中，可以使用“服务器管理器”**** 来安装以下必需的功能。  
  
||  
|-|  
|.NET Framework 3.5（包括 .NET 2.0 和 3.0）<br /><br /> .NET Framework 4.5 高级服务<br /><br /> ASP.NET 4.5<br /><br /> WCF Services<br /><br /> HTTP 激活 [注意：这是必需的。]<br /><br /> TCP 端口共享<br /><br /> Windows Process Activation Service<br /><br /> 进程模型<br /><br /> .NET 环境<br /><br /> 配置 API<br/><br/>动态内容压缩|  
  
 下面是一个示例性的 PowerShell 脚本，用于添加必备的服务器角色和功能。 因环境而异的必备服务器角色和功能。  
  
```powershell  
Install-WindowsFeature Web-Mgmt-Console, AS-NET-Framework, Web-Asp-Net, Web-Asp-Net45, Web-Default-Doc, Web-Dir-Browsing, Web-Http-Errors, Web-Static-Content, Web-Http-Logging, Web-Request-Monitor, Web-Stat-Compression, Web-Filtering, Web-Windows-Auth, NET-Framework-Core, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs  
  
Install-WindowsFeature Web-App-Dev, NET-Framework-45-Features -IncludeAllSubFeature -Restart  
```  
  
 有关 PowerShell 命令的详细信息，请参阅 [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature)。  
  
### <a name="accounts-and-permissions"></a>帐户和权限  
  
|类型|说明|  
|----------|-----------------|  
|Windows 帐户|您必须使用有权配置 Windows 角色、角色服务和功能以及有权在本地计算机上的 IIS 中创建和管理应用程序池、网站和 Web 应用程序的 Windows 帐户登录到 Web 服务器计算机。|  
|服务帐户|当您在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 中创建 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]Web 应用程序时，必须为应用程序运行所在的应用程序池指定标识。 此帐户可不同于在创建 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库时指定的服务帐户。<br /><br /> 此标识必须是域用户帐户，并且添加到 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库中的 mds_exec 数据库角色以便用于数据库访问。 有关详细信息，请参阅 [数据库登录、用户和角色](../../master-data-services/database-logins-users-and-roles-master-data-services.md)。 此帐户还添加到 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Windows 组 **MDS_ServiceAccounts**，该组有权访问文件系统中的临时编译目录 **MDSTempDir**。 有关详细信息，请参阅[文件夹和文件权限 (Master Data Services)](../../master-data-services/folder-and-file-permissions-master-data-services.md)。|  
  
## <a name="see-also"></a>另请参阅  
 [安装 Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
      
 [&#40;Master Data Services 创建主数据管理器 Web 应用程序&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [“Web 配置”页（Master Data Services 配置管理器）](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  
