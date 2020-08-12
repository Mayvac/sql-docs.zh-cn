---
title: ReportingServicesService 配置文件 | Microsoft Docs
description: 了解用于在 Reporting Services 中进行跟踪的 ReportingServicesService.exe 的文件位置、编辑指南和配置设置。
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bb3b4d6c7591385f332daab9102613f05f0e5dfc
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535349"
---
# <a name="reportingservicesservice-configuration-file"></a>ReportingServicesService 配置文件

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)]
  
ReportingServicesService.exe.config 文件包含配置跟踪的设置信息。  
  
## <a name="file-location"></a>文件位置  
此文件可以位于下面的任意路径中：  

``` Paths  
\Reporting Services\Report Server\Bin  
\Program Files\Microsoft SQL Server Reporting Services\SSRS\ReportServer\bin  
```  
 
## <a name="editing-guidelines"></a>编辑指南  
 您可以对此文件进行修改，重命名日志文件或提高/降低跟踪级别。 请不要修改任何其他设置。 有关说明，请参阅[修改 Reporting Services 配置文件 (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)。 有关跟踪日志的详细信息，请参阅 [报表服务器服务跟踪日志](../../reporting-services/report-server/report-server-service-trace-log.md)。  
  
## <a name="example-configuration"></a>配置示例  
 下面的示例显示了 ReportingServicesService.exe.config 文件中的设置和默认值。  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
\<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
\</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a>配置设置  
 下表提供了有关具体设置的信息， 将按设置在配置文件中的显示顺序依次列出：  
  
|设置|描述|  
|-------------|-----------------|  
|**RStrace**|指定用于错误和跟踪的命名空间。|  
|**DefaultTraceSwitch**|指定向 ReportServerService 跟踪日志报告的信息的级别。 每个级别都包含所有更低级别（用更小的数字表示）报告的信息。 建议您不要禁用跟踪。 有效值包括：<br /><br /> 0= 禁用跟踪<br /><br /> 1= 异常和重新启动<br /><br /> 2= 异常、重新启动、警告<br /><br /> 3= 异常、重新启动、警告、状态消息（默认值）<br /><br /> 4= 详细模式|  
|**FileName**|指定日志文件名的第一部分。 日志文件名的其余部分由 **Prefix** 指定的值完成。 默认情况下，名称为 ReportServerService_。|  
|**FileSizeLimitMb**|指定跟踪日志大小的上限。 文件大小的单位为 MB。 有效值介于 0 到最大整数之间。 默认值为 32。|  
|**KeepFilesForDays**|指定多少天后删除跟踪日志文件。 有效值介于 0 到最大整数之间。 默认值为 14。|  
|**Prefix**|指定一个生成的值，该值可将日志实例彼此区分开。 默认情况下，跟踪日志文件名后面将附加时间戳值。 此值设置为“ tid, time ”。 请不要修改此设置。|  
|**TraceListeners**|指定输出跟踪日志内容的目标。 您可以通过使用逗号进行分隔来指定多个目标。 有效值包括：<br /><br /> DebugWindow（默认值）<br /><br /> File（默认值）<br /><br /> StdOut|  
|**TraceFileMode**|指定跟踪日志是否包含 24 小时时段内的数据。 每天应当为每个组件设置唯一的跟踪日志。 此值设置为“Unique”（默认值）。 不要修改此值。|  
|**组件**|指定为其创建跟踪日志的组件。 默认值是 **all**秒。 此设置的其他有效值包括内部组件名。 不要修改此值。|  
|**运行时**|指定支持与早期版本的向后兼容性的配置设置。 运行时设置用于将指向早期版本的 Microsoft.ReportingServices.Interfaces 的请求重定向到新版本。<br /><br /> [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 产品文档对本节中的所有配置设置都进行了说明。 有关详细信息，请在 MSDN 网站上或在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 文档中搜索“运行时架构设置”。|  
  
## <a name="see-also"></a>另请参阅  
[Reporting Services 配置文件](../../reporting-services/report-server/reporting-services-configuration-files.md)  
[报表服务器服务跟踪日志](../../reporting-services/report-server/report-server-service-trace-log.md)  
  
