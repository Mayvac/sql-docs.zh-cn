---
title: sys. dm_pdw_dms_cores (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e3ff3270394d7185d0dbf8e865a27d61380613b5
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197137"
---
# <a name="sysdm_pdw_dms_cores-transact-sql"></a>sys. dm_pdw_dms_cores (Transact-sql) 
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  保存有关设备计算节点上运行的所有 DMS 服务的信息。 它针对每个服务实例列出一行，每个节点当前占一行。  
  
|列名|数据类型|说明|范围|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|与此 DMS 核心关联的唯一数字 id。<br /><br /> 此视图的键。|设置为运行此 DMS core 的节点的 pdw_node_id。|  
|pdw_node_id|**int**|此 DMS 服务正在其上运行的节点的 ID。|请参阅 dm_pdw_nodes sys.databases 中的 node_id [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)。|  
|状态|**nvarchar(32)**|DMS 服务的当前状态。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 有关此视图保留的最大行的信息，请参阅[容量限制](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)主题中的元数据部分。  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
