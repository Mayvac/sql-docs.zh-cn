---
title: sp_revokedbaccess （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokedbaccess_TSQL
- sp_revokedbaccess
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokedbaccess
ms.assetid: c997cfa1-539d-485c-a664-9c6f76bfe0c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 41d2c1aa64bc3d7913cadbb5e54e9895af55e554
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750486"
---
# <a name="sp_revokedbaccess-transact-sql"></a>sp_revokedbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  从当前数据库中删除数据库用户。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]改用[DROP USER](../../t-sql/statements/drop-user-transact-sql.md) 。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_revokedbaccess [ @name_in_db = ] 'name'  
```  
  
## <a name="arguments"></a>自变量  
`[ @name_in_db = ] 'name'`要删除的数据库用户的名称。 *名称*是**sysname** ，无默认值。 *name*可以是服务器登录名、windows 登录名或 windows 组名，并且必须存在于当前数据库中。 当您指定 Windows 登录或 Windows 组时，请指定其在数据库中所使用的名称。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>备注  
 删除数据库用户时，依赖于该用户的权限和别名也会删除。  
  
 **sp_revokedbaccess**只能从当前数据库中删除数据库用户。 删除在当前数据库中拥有对象的数据库用户之前，您必须转移对象的所有权，或者将这些对象从数据库中删除。 有关详细信息，请参阅 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)。  
  
 不能在用户定义的事务中执行**sp_revokedbaccess** 。  
  
## <a name="permissions"></a>权限  
 需要对数据库具有 ALTER ANY USER 权限。  
  
## <a name="examples"></a>示例  
 下面的示例 `Edmonds\LolanSo` 从当前数据库中删除映射到的数据库用户。  
  
```  
EXEC sp_revokedbaccess 'Edmonds\LolanSo';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [安全存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [&#40;Transact-sql&#41;系统存储过程](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-sql&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
