---
description: sys.dm_db_xtp_transactions (Transact-SQL)
title: sys. dm_db_xtp_transactions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_transactions
- sys.dm_db_xtp_transactions_TSQL
- dm_db_xtp_transactions
- dm_db_xtp_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_transactions dynamic management view
ms.assetid: 5c1a0a7a-e851-4b6f-8dfd-c9655fbf5a51
author: markingmyname
ms.author: maghan
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 01f918c14409cdb23c017aaadb6432f18b25e67f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534127"
---
# <a name="sysdm_db_xtp_transactions-transact-sql"></a>sys.dm_db_xtp_transactions (Transact-SQL)
[!INCLUDE[sql-asdb-asdbmi](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

  报告内存中 OLTP 数据库引擎中的活动事务。  
  
 有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
    
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|xtp_transaction_id|**bigint**|此事务在 XTP 事务管理器中的内部 ID。|  
|transaction_id|**bigint**|事务 ID。 与其他事务相关 DMV 中的事务 ID（如 sys.dm_tran_active_transactions）联接。<br /><br /> 0 表示仅限 XTP 的事务，如本机编译存储过程启动的事务。|  
|session_id|**smallint**|正在执行此事务的会话的会话标识符。 与 sys.dm_exec_sessions 联接。|  
|begin_tsn|**bigint**|事务的起始事务序列号。|  
|end_tsn|**bigint**|事务的结束事务序列号。|  
|state|**int**|事务的状态：<br /><br /> 0=ACTIVE<br /><br /> 1=COMMITTED<br /><br /> 2=ABORTED<br /><br /> 3=VALIDATING|  
|state_desc|**nvarchar**|事务状态的说明。|  
|result|**int**|此事务的结果。 下面是可能的值。<br /><br /> 0 - IN PROGRESS<br /><br /> 1 - SUCCESS<br /><br /> 2 - ERROR<br /><br /> 3 - COMMIT DEPENDENCY<br /><br /> 4 - VALIDATION FAILED (RR)<br /><br /> 5 - VALIDATION FAILED (SR)<br /><br /> 6 - ROLLBACK|  
|result_desc|**nvarchar**|此事务的结果。 下面是可能的值。<br /><br /> IN PROGRESS<br /><br /> 成功<br /><br /> ERROR<br /><br /> COMMIT DEPENDENCY<br /><br /> VALIDATION FAILED (RR)<br /><br /> VALIDATION FAILED (SR)<br /><br /> ROLLBACK|  
|last_error|**int**|仅限内部使用|  
|is_speculative|**bit**|仅限内部使用|  
|is_prepared|**bit**|仅限内部使用|  
|is_delayed_durability|**bit**|仅限内部使用|  
|memory_address|**varbinary**|仅限内部使用|  
|database_address|**varbinary**|仅限内部使用|  
|thread_id|**int**|仅限内部使用|  
|read_set_row_count|**int**|仅限内部使用|  
|write_set_row_count|**int**|仅限内部使用|  
|scan_set_count|**int**|仅限内部使用|  
|savepoint_garbage_count|**int**|仅限内部使用|  
|log_bytes_required|**bigint**|仅限内部使用|  
|count_of_allocations|**int**|仅限内部使用|  
|allocated_bytes|**int**|仅限内部使用|  
|reserved_bytes|**int**|仅限内部使用|  
|commit_dependency_count|**int**|仅限内部使用|  
|commit_dependency_total_attempt_count|**int**|仅限内部使用|  
|scan_area|**int**|仅限内部使用|  
|scan_area_desc|**nvarchar**|仅限内部使用|  
|scan_location|**int**|仅限内部使用。|  
|dependent_1_address|**varbinary(8)**|仅限内部使用|  
|dependent_2_address|**varbinary(8)**|仅限内部使用|  
|dependent_3_address|**varbinary(8)**|仅限内部使用|  
|dependent_4_address|**varbinary(8)**|仅限内部使用|  
|dependent_5_address|**varbinary(8)**|仅限内部使用|  
|dependent_6_address|**varbinary(8)**|仅限内部使用|  
|dependent_7_address|**varbinary(8)**|仅限内部使用|  
|dependent_8_address|**varbinary(8)**|仅限内部使用|  
  
## <a name="permissions"></a>权限  
 要求对服务器具有 VIEW DATABASE STATE 权限。  
  
## <a name="see-also"></a>另请参阅  
 [内存优化表动态管理视图 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
