---
title: sp_helparticledts （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticledts
- sp_helparticledts_TSQL
helpviewer_keywords:
- sp_helparticledts
ms.assetid: cd1aed60-e056-4ff3-86ee-62b19433d890
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cfacdd363e66401bc9cfbf494f6cb64ab12446fe
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85634537"
---
# <a name="sp_helparticledts-transact-sql"></a>sp_helparticledts (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  用于获取使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 创建事务订阅时所用的正确自定义任务名称的信息。 此存储过程在发布服务器上对发布数据库执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helparticledts [ @publication = ] 'publication', [ @article = ] 'article'  
```  
  
## <a name="arguments"></a>自变量  
`[ @publication = ] 'publication'`发布的名称。 *发布*为**sysname**，无默认值。  
  
`[ @article = ] 'article'`发布中项目的名称。 *项目*是**sysname**，无默认值。  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**pre_script_ignore_error_task_name**|**sysname**|在复制快照数据之前发生的编程任务的名称。 如果遇到脚本错误，程序应继续执行。|  
|**pre_script_task_name**|**sysname**|在复制快照数据之前发生的编程任务的名称。 遇到错误时程序将停止执行。|  
|**transformation_task_name**|**sysname**|使用数据驱动的查询任务时的编程任务的名称。|  
|**post_script_ignore_error_task_name**|**sysname**|复制快照数据之后发生的编程任务的名称。 如果遇到脚本错误，程序应继续执行。|  
|**post_script_task_name**|**sysname**|复制快照数据之后发生的编程任务的名称。 遇到错误时程序将停止执行。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_helparticledts**用于快照复制和事务复制。  
  
 在复制 Data Transformation Services (DTS) 程序中命名任务时，必须遵从复制代理所需的某些命名约定。 对于自定义任务（如执行 SQL 任务），名称是由项目名称、前缀和可选部分组成的串联字符串。 编写代码时，如果不能确定任务名，则结果集将给出应使用的任务名。  
  
## <a name="permissions"></a>权限  
 只有**sysadmin**固定服务器角色的成员和**db_owner**固定数据库角色的成员才能执行**sp_helparticledts**。  
  
  
