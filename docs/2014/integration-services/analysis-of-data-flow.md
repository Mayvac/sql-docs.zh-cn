---
title: 数据流分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 5723ba6fcbcd8e5b2280fc977aa5f405d461b805
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925558"
---
# <a name="analysis-of-data-flow"></a>数据流分析
  您可以使用[catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` 数据库视图来分析包的数据流。 此视图在每当数据流组件将数据发送到下游组件时显示一行。 这些信息可用来进一步了解发送到每个组件的行。  
  
> [!NOTE]  
>  日志记录级别必须设置为“详细”****，才能通过 catalog.execution_data_statistics 视图捕获信息。  
  
 以下示例显示在包的组件之间发送的行数。  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 以下示例计算每个组件针对特定的执行每毫秒所发送的行数。 计算的值为：  
  
-   **total_rows** - 组件发送的所有行的总和  
  
-   **wall_clock_time_ms** - 每个组件已使用的执行总时间（以毫秒为单位）  
  
-   **num_rows_per_millisecond** - 每个组件每毫秒发送的行数  
  
 `HAVING`子句用于防止在计算中出现被零除错误。  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 [调试数据流](troubleshooting/debugging-data-flow.md)  
  
 [对包执行进行故障排除的工具](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a>另请参阅  
 [数据流中的数据](data-flow/data-in-data-flows.md)  
  
  
