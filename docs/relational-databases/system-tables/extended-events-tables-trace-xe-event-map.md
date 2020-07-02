---
title: trace_xe_event_map （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_xe_event_map_TSQL
- trace_xe_event_map
dev_langs:
- TSQL
helpviewer_keywords:
- trace_xe_event_map
- extended events [SQL Server], tables
ms.assetid: 537aa292-3540-47e8-be28-56dc01abc343
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 154eb6731264fb8363aff0825e3ec0639e4e142c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750192"
---
# <a name="extended-events-tables---trace_xe_event_map"></a>Extended Events Tables - trace_xe_event_map
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  映射到 SQL 跟踪事件类的每个扩展事件各占一行。 此表存储在 sys 架构中的 master 数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|trace_event_id|**smallint**|正在映射的 SQL 跟踪事件类的 ID。|  
|package_name|**nvarchar(60)**|映射事件所在的扩展事件包的名称。|  
|xe_event_name|**nvarchar(60)**|映射到 SQL 跟踪事件类的“扩展事件”事件的名称。|  
  
## <a name="remarks"></a>备注  
 您可以使用以下查询确定与 SQL 跟踪事件类等效的“扩展事件”事件：  
  
```  
SELECT te.name, xe.package_name, xe.xe_event_name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NOT NULL  
```  
  
 并非所有事件类都有等效的“扩展事件”事件。 您可以使用以下查询列出没有扩展事件等效项的事件类：  
  
```  
SELECT te.trace_event_id, te.name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NULL  
```  
  
 在前面的查询中，返回的大多数事件类都与审核相关。 建议您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 进行审核。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 使用扩展事件来帮助创建审核。 有关详细信息，请参阅 [SQL Server Audit（数据库引擎）](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。  
  
## <a name="see-also"></a>另请参阅  
 [trace_xe_action_map (Transact-SQL)](../../relational-databases/system-tables/extended-events-tables-trace-xe-action-map.md)  
  
  
