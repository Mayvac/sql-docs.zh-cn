---
title: sp_helplogreader_agent （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords:
- sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 31b4811542fa291fd1ff61368e6c5ac3ce9e714a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728126"
---
# <a name="sp_helplogreader_agent-transact-sql"></a>sp_helplogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  为发布数据库返回日志读取器代理作业属性。 此存储过程在发布服务器上对发布数据库执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helplogreader_agent [ [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>自变量  
`[ @publisher = ] 'publisher'`发布服务器的名称。 *发布服务器*的**sysname**，默认值为 NULL。  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|代理的 ID。|  
|**name**|**nvarchar （100）**|代理的名称。|  
|**publisher_security_mode**|**smallint**|代理在连接发布服务器时所使用的安全模式，可以是下列模式之一：<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证<br /><br /> **1** = Windows 身份验证。|  
|**publisher_login**|**sysname**|连接到发布服务器时使用的登录名。|  
|**publisher_password**|**nvarchar （524）**|出于安全原因， **\*\*\*\*\*\*\*\*\*\*** 始终返回值。|  
|**job_id**|**uniqueidentifier**|代理作业的唯一 ID。|  
|**job_login**|**nvarchar(512)**|是日志读取器代理运行时所用的 Windows 帐户，它以 "*域*用户名" 的格式返回 \\ *username*。|  
|**job_password**|**sysname**|出于安全原因， **\*\*\*\*\*\*\*\*\*\*** 始终返回值。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_helplogreader_agent**用于事务复制。  
  
## <a name="permissions"></a>权限  
 只有发布服务器上的**sysadmin**固定服务器角色的成员或发布数据库上**db_owner**固定数据库角色的成员才能执行**sp_helplogreader_agent**。  
  
## <a name="see-also"></a>另请参阅  
 [查看和修改复制安全设置](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addlogreader_agent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
