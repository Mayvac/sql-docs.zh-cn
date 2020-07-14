---
title: 在同一 SQL 实例中运行实用工具和非实用工具收集组 | Microsoft Docs
description: 了解如何使用并行工作的实用工具和非实用工具收集组来监视 SQL Server 的实例。 查看配置要求。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 522b21e2a2c7e78c8ca16483fc02f2564e0ebaf5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773477"
---
# <a name="run-utility-and-non-utility-collection-sets-on-same-sql-instance"></a>在同一 SQL 实例中运行实用工具和非实用工具收集组
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组与非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组并行。 也就是说，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某一托管实例是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具的成员时，该托管实例可由其他收集组监视。 但是，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例正在注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具时，您必须禁用非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组功能。  
  
 在向 UCP 注册了该实例后，您可以重新启动非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组。 但要注意的是，该托管实例上的所有收集组会将其数据上载到实用工具管理数据仓库 (UMDW) 中；UMDW 文件名为 sysutility_mdw。  
  
 若要将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组与非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具收集组并行运行，请考虑以下要点：  
  
-   支持并行收集组。  
  
-   在将实例注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具时您必须禁用现有的数据收集器。  
  
-   为了满足验证要求，您必须在创建 UCP 前在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例上运行以下存储过程，并且在将其注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中之前在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例上运行以下存储过程：  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     如果您在启动“创建 UCP 向导”或“添加托管实例向导”之前未运行这些存储过程，操作将失败：  
  
-   您必须为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例上的所有收集组使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实用工具 UMDW (sysutility_mdw)。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server 实用工具的功能和任务](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [配置实用工具控制点数据仓库（SQL Server 实用工具）](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
