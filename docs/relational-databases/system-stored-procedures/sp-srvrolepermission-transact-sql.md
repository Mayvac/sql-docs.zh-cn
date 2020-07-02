---
title: sp_srvrolepermission （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_srvrolepermission_TSQL
- sp_srvrolepermission
dev_langs:
- TSQL
helpviewer_keywords:
- sp_srvrolepermission
ms.assetid: 5709667f-e3e4-48a2-93ec-af5e22a2ac58
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7f158839f45b3b890c0ae46aee1d74f4e6a3e59b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772957"
---
# <a name="sp_srvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  显示固定服务器角色的权限。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_srvrolepermission [ [ @srvrolename = ] 'role']  
```  
  
## <a name="arguments"></a>自变量  
`[ @srvrolename = ] 'role'`为其返回权限的固定服务器角色的名称。 *role*的值为**sysname**，默认值为 NULL。 如果未指定角色，则返回所有固定服务器角色的权限。 *角色*可以具有以下值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**sysadmin**|系统管理员|  
|**securityadmin**|安全管理员|  
|**serveradmin**|服务器管理员|  
|**setupadmin**|安装程序管理员|  
|**processadmin**|进程管理员|  
|**diskadmin**|磁盘管理员|  
|**dbcreator**|数据库创建者|  
|**bulkadmin**|可执行 BULK INSERT 语句|  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**ServerRole**|**sysname**|固定服务器角色的名称|  
|**权限**|**sysname**|与**ServerRole**关联的权限|  
  
## <a name="remarks"></a>备注  
 列出的权限包括可以执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和固定服务器角色成员可执行的其他特殊活动。 若要显示固定服务器角色的列表，请执行**sp_helpsrvrole**。  
  
 **Sysadmin**固定服务器角色具有其他所有固定服务器角色的权限。  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。  
  
## <a name="examples"></a>示例  
 以下查询返回与 `sysadmin` 固定服务器角色关联的权限。  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [安全存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
