---
title: sp_change_agent_profile （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_agent_profile
- sp_change_agent_profile_TSQL
helpviewer_keywords:
- sp_change_agent_profile
ms.assetid: e73acf8d-0be8-4197-ba11-fe798d0e2820
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b0084338c2629b8ffeb208edc5ac7532105e1271
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715939"
---
# <a name="sp_change_agent_profile-transact-sql"></a>sp_change_agent_profile (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  更改存储在[MSagent_profiles &#40;transact-sql&#41;](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)表中的复制代理配置文件的参数。 此存储过程在分发服务器上的任何数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_change_agent_profile [ @profile_id = ] profile_id   
        , [ @property = ] 'property'   
        , [ @value = ] 'value'   
```  
  
## <a name="arguments"></a>自变量  
`[ @profile_id = ] profile_id`配置文件的 ID。 *profile_id*为**int**，没有默认值。  
  
`[ @property = ] 'property'`属性的名称。 *属性*为**sysname**，无默认值。  
  
`[ @value = ] 'value'`属性的新值。 *值*为**nvarchar （3000）**，无默认值。  
  
 下表说明可以更改的配置文件属性。  
  
|Property|描述|  
|--------------|-----------------|  
|**2008**|配置文件的说明。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_change_agent_profile**在所有类型的复制中使用。  
  
## <a name="permissions"></a>权限  
 只有**sysadmin**固定服务器角色的成员才能**sp_change_agent_profile**执行。  
  
## <a name="see-also"></a>另请参阅  
 [sp_add_agent_profile &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_drop_agent_profile &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_profile &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
