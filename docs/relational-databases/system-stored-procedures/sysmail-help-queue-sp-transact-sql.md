---
title: sysmail_help_queue_sp （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_queue_sp
- sysmail_help_queue_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_queue_sp
ms.assetid: 94840482-112c-4654-b480-9b456c4c2bca
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4f47e06875d2076e4ae9510d7cb1c5bf5f706c45
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890879"
---
# <a name="sysmail_help_queue_sp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  数据库邮件中具有两个队列：邮件队列和状态队列。 邮件队列存储正在等待发送的邮件项。 状态队列存储已发送项的状态。 此存储过程允许查看邮件队列的状态或状态队列的状态。 如果未指定参数** \@ queue_type** ，则存储过程将为每个队列返回一行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>参数  
`[ @queue_type = ] 'queue_type'`可选参数删除指定为*queue_type*的类型的电子邮件。 *queue_type*为**nvarchar （6）** ，无默认值。 有效条目为 "**邮件**" 和 "**状态**"。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="result-set"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar （6）**|队列的类型。 可能的值为 "**邮件**" 和 "**状态**"。|  
|**length**|**int**|指定队列中邮件项的数量。|  
|State |**nvarchar （64）**|监视器的状态。 可能的值为**非活动状态**（队列处于非活动状态）、已**通知**（队列已通知发生接收）和**RECEIVES_OCCURRING** （队列正在接收）。|  
|**last_empty_rowset_time**|**型**|上次队列为空的日期和时间。 采用军用时间格式和 GMT 时区。|  
|**last_activated_time**|**型**|上次激活队列的日期和时间。 采用军用时间格式和 GMT 时区。|  
  
## <a name="remarks"></a>备注  
 在对数据库邮件进行故障排除时，使用**sysmail_help_queue_sp**来查看队列中有多少项、队列的状态以及上次激活的时间。  
  
## <a name="permissions"></a>权限  
 默认情况下，只有**sysadmin**固定服务器角色的成员才能访问此过程。  
  
## <a name="examples"></a>示例  
 以下示例返回邮件队列和状态队列。  
  
```  
EXECUTE msdb.dbo.sysmail_help_queue_sp ;  
GO  
```  
  
 此示例针对结果集的长度对结果集进行了编辑。  
  
```  
queue_type length      state              last_empty_rowset_time  last_activated_time  
---------- -------- ------------------ ----------------------- -----------------------  
mail       0        RECEIVES_OCCURRING 2005-10-07 21:14:47.010 2005-10-10 20:52:51.517  
status     0        INACTIVE           2005-10-07 21:04:47.003 2005-10-10 21:04:47.003  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据库邮件](../../relational-databases/database-mail/database-mail.md)  
  
  
