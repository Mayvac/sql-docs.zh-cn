---
description: sp_replflush (Transact-SQL)
title: sp_replflush (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replflush
- sp_replflush_TSQL
helpviewer_keywords:
- sp_replflush
ms.assetid: 20809f5f-941d-427f-8f0c-de7a6c487584
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 144bffdd6076b73c8b10fca3c7d9f878d77091d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485728"
---
# <a name="sp_replflush-transact-sql"></a>sp_replflush (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  刷新项目缓存。 此存储过程在发布服务器上对发布数据库执行。  
  
> [!IMPORTANT]  
>  用户不应手动执行此过程。 **sp_replflush** 应仅用于排查有经验的复制支持专业人员指导的复制问题。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_replflush  
```  
  
## <a name="return-code-values"></a>返回代码值  
 **0** (成功) 或 **1** (失败)   
  
## <a name="remarks"></a>备注  
 **sp_replflush** 用于事务复制。  
  
 为提高效率，项目定义存储在缓存中。 当修改或删除项目定义时，其他复制存储过程将使用**sp_replflush** 。  
  
 只有一个客户端连接有权访问给定数据库的日志读取器。 如果客户端有权访问数据库的日志读取器，则执行 **sp_replflush** 将导致客户端释放其访问权限。 然后，其他客户端可以使用 **sp_replcmds** 或 **sp_replshowcmds**来扫描事务日志。  
  
## <a name="permissions"></a>权限  
 只有 **sysadmin** 固定服务器角色的成员或 **db_owner** 固定数据库角色的成员才能执行 **sp_replflush**。  
  
## <a name="see-also"></a>另请参阅  
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_repltrans &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
