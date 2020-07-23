---
title: 管理 CDC 服务 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manSer
ms.assetid: 645ae53f-f352-4d6a-9eb0-264e53a93a18
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 187bfb6ccfb9cda80213487c7e315ec517f8d3dc
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922513"
---
# <a name="manage-a-cdc-service"></a>管理 CDC 服务

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  您可以使用 CDC 设计器控制台查看通过 CDC 服务配置控制台创建的服务并且管理 Oracle CDC 服务中的所有实例。  
  
 在左侧窗格中单击服务的名称可显示与该服务有关的信息并且对其进行管理。  
  
> [!NOTE]  
>  您必须首先使用 CDC 服务配置控制台创建一个服务以便向该列表中添加服务。 有关如何创建服务的信息，请参阅随 CDC 服务配置控制台一起提供的联机帮助。  
  
## <a name="what-you-can-do-when-you-display-the-cdc-service-information"></a>在显示 CDC 服务信息时您可以执行的操作  
 在显示与服务有关的信息时您可以执行以下操作：  
  
 **为所选服务创建一个新的 CDC 实例**  
  
 单击 **“新建 Oracle CDC 实例”** ，在右侧窗格中为该服务创建一个新的实例。 新建实例向导将打开以便创建该实例。 有关新建实例向导的详细信息，请参阅 [Use the New Instance Wizard](../../integration-services/change-data-capture/use-the-new-instance-wizard.md)。  
  
 **启动服务中的所有 CDC 实例**  
  
 在右侧窗格中单击 **“启动所有实例”** 可开始从服务中定义的所有实例捕获数据。  
  
 **停止服务中的所有 CDC 实例**  
  
 单击 **“停止所有实例”** 可停止服务中所有实例的变更数据捕获。  
  
## <a name="see-also"></a>另请参阅  
 [如何创建 SQL Server 更改数据库实例](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [如何从 CDC 设计器控制台管理 CDC 服务](../../integration-services/change-data-capture/how-to-manage-a-cdc-service-from-the-cdc-designer-console.md)   
 [使用新建实例向导](../../integration-services/change-data-capture/use-the-new-instance-wizard.md)  
  
  
