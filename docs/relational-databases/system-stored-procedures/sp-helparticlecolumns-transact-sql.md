---
title: sp_helparticlecolumns （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticlecolumns
- sp_helparticlecolumns_TSQL
helpviewer_keywords:
- sp_helparticlecolumns
ms.assetid: 9ea55df3-2e99-4683-88ad-bde718288bc7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4ab8250e12f5b553a9c2c080b0a1e4efe9eb1657
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786190"
---
# <a name="sp_helparticlecolumns-transact-sql"></a>sp_helparticlecolumns (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  返回基础表中的所有列。 此存储过程在发布服务器上对发布数据库执行。 对于 Oracle 发布服务器，此存储过程在分发服务器的任一数据库上执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helparticlecolumns [ @publication = ] 'publication'   
        , [ @article = ] 'article'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>自变量  
`[ @publication = ] 'publication'`包含项目的发布的名称。 *发布*为**sysname**，无默认值。  
  
`[ @article = ] 'article'`返回其列的项目的名称。 *项目*是**sysname**，无默认值。  
  
`[ @publisher = ] 'publisher'`指定一个非 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布服务器。 *发布服务器*的**sysname**，默认值为 NULL。  
  
> [!NOTE]  
>  如果发布服务器发布请求的项目，则不应指定*发布服务器* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （未发布的列）或**1** （已发布的列）  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**列 id**|**int**|列的标识符。|  
|**column**|**sysname**|列的名称。|  
|**发布**|**bit**|指示是否发布列：<br /><br /> **0** = 否<br /><br /> **1** = 是|  
|**发布服务器类型**|**sysname**|发布服务器上列的数据类型。|  
|**订阅服务器类型**|**sysname**|订阅服务器上列的数据类型。|  
  
## <a name="remarks"></a>备注  
 **sp_helparticlecolumns**用于快照复制和事务复制。  
  
 **sp_helparticlecolumns**可用于检查垂直分区。  
  
## <a name="permissions"></a>权限  
 只有**sysadmin**固定服务器角色的成员、 **db_owner**固定数据库角色的成员或当前发布的发布访问列表才能执行**sp_helparticlecolumns**。  
  
## <a name="see-also"></a>另请参阅  
 [定义和修改列筛选器](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [sp_addarticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_droppublication &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
