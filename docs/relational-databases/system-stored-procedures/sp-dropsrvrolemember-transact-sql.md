---
title: sp_dropsrvrolemember （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropsrvrolemember
- sp_dropsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropsrvrolemember
ms.assetid: 7be99181-d221-49d0-9cb2-c930d8c044a0
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 213b8301a471e00107ce7d3ac6bf493e6aea87c4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85662467"
---
# <a name="sp_dropsrvrolemember-transact-sql"></a>sp_dropsrvrolemember (Transact-SQL)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

从固定服务器角色中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名或 Windows 用户或组。

> [!IMPORTANT]
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]请改用[ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) 。

![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>语法

```
sp_dropsrvrolemember [ @loginame = ] 'login' , [ @rolename = ] 'role'  
```

## <a name="arguments"></a>自变量

**[ @loginame =]** "_login_"  
要从固定服务器角色中删除的登录名。 *login*的**sysname**为，无默认值。 *登录名*必须存在。  

**[ @rolename =]** "_role_"  
服务器角色的名称。 *role*的值为**sysname**，默认值为 NULL。 *role*必须是下列值之一：  

-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin 
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>备注  
 只能使用 sp_dropsrvrolemember 从固定服务器角色中删除登录。 使用 sp_droprolemember 从数据库角色删除成员。  
  
 不能从任何固定服务器角色中删除 sa 登录。  
  
 不能在用户定义的事务中执行 sp_dropsrvrolemember。  
  
## <a name="permissions"></a>权限  
 需要具有 sysadmin 固定服务器角色中的成员身份，或同时具有对服务器的 ALTER ANY LOGIN 权限以及从中删除成员的角色中的成员身份。  
  
## <a name="examples"></a>示例  
 以下示例从 `JackO` 固定服务器角色中删除登录 `sysadmin`。  
  
```sql
EXEC sp_dropsrvrolemember 'JackO', 'sysadmin';  
```  
  
## <a name="see-also"></a>另请参阅  
 [&#40;Transact-sql&#41;创建服务器角色](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40;Transact-sql&#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [安全存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [&#40;Transact-sql&#41;系统存储过程](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [安全函数 (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)  
