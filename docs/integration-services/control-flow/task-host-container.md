---
title: 任务宿主容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c934687c159d81ddaa20852844859801dc248405
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920964"
---
# <a name="task-host-container"></a>任务宿主容器

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  任务宿主容器封装单个任务。 在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中，无需对任务宿主进行单独配置；设置其要封装任务的属性时即可对其进行配置。 有关任务宿主容器所封装任务的详细信息，请参阅 [Integration Services Tasks](../../integration-services/control-flow/integration-services-tasks.md)。  
  
 此容器将变量和事件处理程序的使用扩展到任务级。 有关详细信息，请参阅 [Integration Services (SSIS) 事件处理程序](../../integration-services/integration-services-ssis-event-handlers.md)和 [Integration Services (SSIS) 变量](../../integration-services/integration-services-ssis-variables.md)。  
  
## <a name="configuration-of-the-task-host"></a>任务宿主的配置  
 可以在 **的** “属性” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 窗口中设置属性，或以编程方式设置属性。  
  
 有关在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中设置这些属性的信息，请参阅 [设置任务或容器的属性](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)。  
  
 有关如何以编程方式设置这些属性的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [设置任务或容器的属性](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>另请参阅  
 [Integration Services 容器](../../integration-services/control-flow/integration-services-containers.md)  
  
  
