---
description: dbo.syssessions (Transact-SQL)
title: " (Transact-sql) dbo.sys会话 |Microsoft Docs"
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 72fa9a3d55b3ed783fcbfc7c230676e7fe653eea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473278"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理时，该代理都会创建一个新会话。 当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务意外重新启动或停止时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将使用该会话来保留作业的状态。 **Syssessions**表中的每一行都包含一个会话的相关信息。 使用 **sysjobactivity** 表可以查看每个会话结束时的作业状态。  
  
 该表存储在 **msdb** 数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理会话的 ID。 此 session_id 不是会话的 SPID，而是此系统表中的标识值。|  
|**agent_start_date**|**datetime**|为此会话启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的日期和时间。|  
  
## <a name="remarks"></a>备注  
 只有作为 **sysadmin** 固定服务器角色成员的用户才能访问此表。  
  
## <a name="see-also"></a>另请参阅  
 [dbo.sysjobactivity &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
