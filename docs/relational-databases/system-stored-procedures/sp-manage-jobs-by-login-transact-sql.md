---
title: sp_manage_jobs_by_login （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_manage_jobs_by_login
- sp_manage_jobs_by_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_manage_jobs_by_login
ms.assetid: 832ec15a-6e92-4eb5-8c4a-af4dba79fbaa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e810bf996f7dbaa8624c6a0e834011d759aa9348
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899387"
---
# <a name="sp_manage_jobs_by_login-transact-sql"></a>sp_manage_jobs_by_login (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  删除或重新分配属于指定登录名的作业。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_manage_jobs_by_login  
     [ @action = ] 'action'  
     [, [@current_owner_login_name = ] 'current_owner_login_name']  
     [, [@new_owner_login_name = ] 'new_owner_login_name']  
```  
  
## <a name="arguments"></a>参数  
`[ @action = ] 'action'`要对指定的登录名执行的操作。 *操作*为**varchar （10）**，无默认值。 删除*操作*时**DELETE**， **sp_manage_jobs_by_login**会删除*current_owner_login_name*拥有的所有作业。 **重新分配***操作*时，会将所有作业分配给*new_owner_login_name*。  
  
`[ @current_owner_login_name = ] 'current_owner_login_name'`当前作业所有者的登录名。 *current_owner_login_name* **sysname**，无默认值。  
  
`[ @new_owner_login_name = ] 'new_owner_login_name'`新作业所有者的登录名。 仅在*操作***重新分配**时使用此参数。 *new_owner_login_name*的默认值为**sysname**，默认值为 NULL。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="result-sets"></a>结果集  
 无  
  
## <a name="permissions"></a>权限  
 若要运行此存储过程，用户必须被授予**sysadmin**固定服务器角色。  
  
## <a name="examples"></a>示例  
 以下示例将所有作业从 `danw` 重新分配给 `françoisa`。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_manage_jobs_by_login  
    @action = N'REASSIGN',  
    @current_owner_login_name = N'danw',  
    @new_owner_login_name = N'françoisa' ;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [sp_delete_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
