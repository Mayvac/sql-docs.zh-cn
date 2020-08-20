---
description: 'sys. dm_pdw_dms_workers (Transact-sql) '
title: sys. dm_pdw_dms_workers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0a284d18-3c46-4ffa-bcc9-689e660ee8b4
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 886b96bebe2d7535694dc724d7ad236ae1c2b5f7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474757"
---
# <a name="sysdm_pdw_dms_workers-transact-sql"></a>sys. dm_pdw_dms_workers (Transact-sql) 
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  保存有关完成 DMS 步骤的所有工作线程的信息。  
  
|列名|数据类型|说明|范围|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|查询此 DMS 工作线程所属的部分。<br /><br /> request_id、step_index 和 dms_step_index 构成此视图的键。|请参阅 dm_pdw_exec_requests sys.databases 中的 request_id [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)。|  
|step_index|**int**|查询步骤此 DMS 辅助角色所属的部分。<br /><br /> request_id、step_index 和 dms_step_index 构成此视图的键。|请参阅 dm_pdw_request_steps sys.databases 中的 step_index [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|dms_step_index|**int**|此工作线程正在运行的 DMS 计划中的步骤。<br /><br /> request_id、step_index 和 dms_step_index 构成此视图的键。||  
|pdw_node_id|**int**|正在运行辅助角色的节点。|请参阅 dm_pdw_nodes sys.databases 中的 node_id [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)。|  
|distribution_id|**Int**|正在运行辅助进程的分发（如果有）。|请参阅 pdw_distributions sys.databases 中的 distribution_id [&#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md)。|  
|type|**nvarchar(32)**|此项表示的 DMS 工作线程的类型。|"DIRECT_CONVERTER"、"DIRECT_READER"、"FILE_READER"、"HASH_CONVERTER"、"HASH_READER"、"ROUNDROBIN_CONVERTER"、"EXPORT_READER"、"EXTERNAL_READER"、"EXTERNAL_WRITER"、"PARALLEL_COPY_READER"、"REJECT_WRITER"、"WRITER"|  
|状态|**nvarchar(32)**|DMS 工作线程的状态。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|bytes_per_sec|**bigint**|读取或写入吞吐量。|大于或等于0。 如果查询在执行之前已取消或失败，则为 NULL。|  
|bytes_processed|**bigint**|此工作线程处理的总字节数。|大于或等于0。 如果查询在执行之前已取消或失败，则为 NULL。|  
|rows_processed|**bigint**|为此辅助角色读取或写入的行数。|大于或等于0。 如果查询在执行之前已取消或失败，则为 NULL。|  
|start_time|**datetime**|此工作线程的执行开始的时间。|大于或等于此辅助线程所属的查询步骤的开始时间。 请参阅 [sys.databases &#40;transact-sql&#41;dm_pdw_request_steps ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|end_time|**datetime**|执行结束、失败或已取消的时间。|对于正在进行的或已排队的工作线程，为 NULL。 否则，大于 start_time。|  
|total_elapsed_time|**int**|执行所用的总时间（以毫秒为单位）。|大于或等于0。<br /><br /> 自系统启动或重新启动以来经过的总时间。 如果 total_elapsed_time 超过24.8 天（以毫秒为单位） (整数的最大值) ，则会导致具体化失败，因为溢出。<br /><br /> 最大值（以毫秒为单位）等效于24.8 天。|  
|cpu_time|**bigint**|此工作线程占用的 CPU 时间（以毫秒为单位）。|大于或等于0。|  
|query_time|**int**|SQL 开始将行返回到线程之前的时间段（以毫秒为单位）。|大于或等于0。|  
|buffers_available|**int**|未使用的缓冲区数。| 如果查询在执行之前已取消或失败，则为 NULL。|  
|sql_spid|**int**|为此 DMS 辅助角色执行工作的 SQL Server 实例的会话 id。||  
|dms_cpid|**int**|运行的实际线程的进程 ID。||  
|error_id|**nvarchar (36) **|执行此辅助进程期间发生的错误的唯一标识符（如果有）。|请参阅 dm_pdw_request_steps sys.databases 中的 error_id [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|source_info|**nvarchar(4000)**|对于读取器，说明源表和列。||  
|destination_info|**nvarchar(4000)**|对于编写器，指定目标表。||  
  
 有关此视图保留的最大行的信息，请参阅 [容量限制](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) 主题中的元数据部分。  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
