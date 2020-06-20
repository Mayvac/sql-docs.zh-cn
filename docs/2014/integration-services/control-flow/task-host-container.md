---
title: 任务宿主容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c5a389a39320ef37e3dc2b2a5fcef015d664fce6
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84917960"
---
# <a name="task-host-container"></a>任务宿主容器
  任务宿主容器封装单个任务。 在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中，无需对任务宿主进行单独配置；设置其要封装任务的属性时即可对其进行配置。 有关任务宿主容器所封装任务的详细信息，请参阅 [Integration Services Tasks](integration-services-tasks.md)。  
  
 此容器将变量和事件处理程序的使用扩展到任务级。 有关详细信息，请参阅 [Integration Services (SSIS) 事件处理程序](../integration-services-ssis-event-handlers.md)和 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。  
  
## <a name="configuration-of-the-task-host"></a>任务宿主的配置  
 可以在 **的** “属性” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 窗口中设置属性，或以编程方式设置属性。  
  
 有关在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中设置这些属性的信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。  
  
 有关如何以编程方式设置这些属性的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>另请参阅  
 [Integration Services 容器](integration-services-containers.md)  
  
  
