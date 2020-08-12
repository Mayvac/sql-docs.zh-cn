---
title: Windows 应用程序日志 | Microsoft Docs
description: 了解如何在由在本地系统上运行报表服务器应用程序生成的应用程序日志中查看事件消息。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5466c8a3e839a6db9438fde3ca7ce295405f3f23
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547829"
---
# <a name="windows-application-log"></a>Windows 应用程序日志
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 将事件消息写入 Windows 应用程序日志。 您可以使用写入应用程序日志的消息信息，找出在本地系统上运行的报表服务器应用程序生成的事件。  
  
## <a name="viewing-report-server-events"></a>查看报表服务器事件  
 使用事件查看器可以查看日志文件并筛选其中包含的消息。 有关事件消息的详细信息，请参阅 [错误和事件参考 (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)。 有关 Windows 应用程序日志或事件查看器的详细信息，请参阅 Windows 产品文档。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供以下三个事件源：  
  
-   报表服务器（报表服务器 Windows 服务）  
  
-   报表管理器  
  
-   计划和传递处理器  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 未提供关闭报表服务器的应用程序事件记录的方法，也无法控制记录哪些事件。 描述报表服务器事件日志记录的架构是固定的。 您不能将架构扩展到可以支持自定义事件。  
  
 下表对报表服务器写入应用程序事件日志的事件类型进行了说明：  
  
|事件类型|描述|  
|----------------|-----------------|  
|信息|描述成功操作的事件（例如，报表服务器服务的启动时间）。|  
|警告|指示潜在问题的事件（如磁盘空间不足）。|  
|错误|描述重要问题的事件（如服务未能启动）。|  
|审核成功|描述成功登录的安全性事件。|  
|审核失败|登录失败时记录的事件。|  
  
## <a name="see-also"></a>另请参阅  
 [Reporting Services 日志文件和来源](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [错误和事件参考 (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
