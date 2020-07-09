---
title: catalog.disable_worker_agent（SSISDB 数据库）| Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3f19dc4c-a000-4318-8fe1-e80d56720e66
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc3aae082a59cf122971798739e5add2b1886689
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053686"
---
# <a name="catalogdisable_worker_agent-ssisdb-database"></a>catalog.disable_worker_agent（SSISDB 数据库）

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

为使用此 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录的 Scale Out Master 禁用 Scale Out Worker。

## <a name="syntax"></a>语法

```sql
catalog.disable_worker_agent [ @WorkerAgentId = ] WorkerAgentId
```
## <a name="arguments"></a>参数
[@WorkerAgentId =] WorkerAgentId  Scale Out Worker 的辅助角色代理 ID。 WorkerAgentId 为 uniqueidentifier   。

## <a name="example"></a>示例
此示例在 MachineA 上禁用 Scale Out Worker。

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[disable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>返回代码值  
 0（成功）  
  
## <a name="result-sets"></a>结果集  
 无  

## <a name="permissions"></a>权限  
 此存储过程需要下列权限之一：  
  
-   **ssis_admin** 数据库角色的成员资格  
  
-   **sysadmin** 服务器角色的成员资格 

## <a name="errors-and-warnings"></a>错误和警告
如果辅助角色代理 ID 无效，则存储过程返回错误。
