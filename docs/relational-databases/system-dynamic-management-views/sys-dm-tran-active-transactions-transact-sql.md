---
description: sys.dm_tran_active_transactions (Transact-SQL)
title: sys. dm_tran_active_transactions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_active_transactions
- sys.dm_tran_active_transactions_TSQL
- dm_tran_active_transactions_TSQL
- dm_tran_active_transactions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_active_transactions dynamic management view
ms.assetid: 154ad6ae-5455-4ed2-b014-e443abe2c6ee
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 614c53545631de7de3a62edd30e8b8e1f71b664f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454806"
---
# <a name="sysdm_tran_active_transactions-transact-sql"></a>sys.dm_tran_active_transactions (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  返回有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的事务的信息。  
  
> [!NOTE]  
>  若要从或调用此 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ，请使用名称 **dm_pdw_nodes_tran_active_transactions**。  
  
|列名|数据类型|说明|  
|-----------------|---------------|-----------------|  
|transaction_id|**bigint**|实例级而非数据库级的事务 ID。 仅在一个实例的所有数据库中唯一，在所有服务器实例中则不唯一。|  
|name|**nvarchar(32)**|事务名称。 如果事务已被标记且标记的名称替换事务名称，则此名称被覆盖。|  
|transaction_begin_time|**datetime**|事务的开始时间。|  
|transaction_type|**int**|事务的类型。<br /><br /> 1 = 读/写事务<br /><br /> 2 = 只读事务<br /><br /> 3 = 系统事务<br /><br /> 4 = 分布式事务|  
|transaction_uow|**uniqueidentifier**|分布式事务的事务工作单元 (UOW) 标识符。 MS DTC 使用 UOW 标识符来处理分布式事务。|  
|transaction_state|**int**|0 = 事务尚未完全初始化。<br /><br /> 1 = 事务已初始化但尚未启动。<br /><br /> 2 = 事务处于活动状态。<br /><br /> 3 = 事务已结束。 该状态用于只读事务。<br /><br /> 4 = 已对分布式事务启动提交进程。 仅用于分布式事务。 分布式事务仍然处于活动状态，但不会进行进一步处理。<br /><br /> 5 = 事务处于准备就绪状态且等待解析。<br /><br /> 6 = 事务已提交。<br /><br /> 7 = 事务正在被回滚。<br /><br /> 8 = 事务已回滚。|  
|transaction_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|transaction_status2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_state|**int**|**适用**于： [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 通过 [当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299659))  (初始版本。<br /><br /> 1 = 活动<br /><br /> 2 = 准备就绪<br /><br /> 3 = 已提交<br /><br /> 4 = 中止<br /><br /> 5 = 已恢复|  
|dtc_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_isolation_level|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|filestream_transaction_id|**varbinary(128)**|**适用**于： [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 通过 [当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299659))  (初始版本。<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|pdw_node_id|**int**|**适用**于： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分发所在的节点的标识符。|  
  
## <a name="permissions"></a>权限

在上 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ，需要 `VIEW SERVER STATE` 权限。   
在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 高级层上，需要具有 `VIEW DATABASE STATE` 数据库中的权限。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 标准层和基本层上，需要  **服务器管理员** 或 **Azure Active Directory 管理员** 帐户。   
  
## <a name="see-also"></a>另请参阅  
 [sys. dm_tran_session_transactions &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-session-transactions-transact-sql.md)   
 [sys. dm_tran_database_transactions &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-database-transactions-transact-sql.md)   
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与事务相关的动态管理视图和函数 (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


