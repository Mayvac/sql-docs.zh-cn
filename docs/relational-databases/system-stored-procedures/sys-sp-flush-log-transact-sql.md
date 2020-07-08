---
title: sys. sp_flush_log （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_flush_log_TSQL
- sys.sp_flush_log
- sys.sp_flush_log_TSQL
- sp_flush_log
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_flush_log
ms.assetid: 75cc9f52-3b1f-4754-b1e7-ce0dd3323bc9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: cbcb731a4396829b38596619e4b52babcb6f9425
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052707"
---
# <a name="syssp_flush_log-transact-sql"></a>sys.sp_flush_log (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  将当前数据库的事务日志刷新至磁盘，从而强化所有之前已提交的延迟持久事务。  
  
 如果您出于性能优势原因而选择使用延迟事务持续性，但还想对在服务器崩溃或故障转移时丢失的数据量进行有保证的限制，请定期执行 `sys.sp_flush_log`。 例如，如果要确保不会丢失 x 秒以上的数据，则 `sp_flush_log` 每隔 x 秒执行一次。  
  
 执行 `sys.sp_flush_log` 可保证所有之前提交的延迟持久事务都是持久的。 有关详细信息，请参阅概念主题[控制事务持续](../../relational-databases/logs/control-transaction-durability.md)性。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```sql  
  
sys.sp_flush_log  
  
```  
  
#### <a name="parameters"></a>参数  
 无。  
  
## <a name="return-code-values"></a>返回代码值  
 返回代码 1 表示成功。  任何其他值表示失败。  
  
## <a name="result-sets"></a>结果集  
 无。  
  
## <a name="sample-code"></a>示例代码  
  
```sql  
.  
EXECUTE sys.sp_flush_log  
  
```  
  
  
