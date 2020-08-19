---
description: 使用 Transact-SQL 存储过程创建和运行跟踪
title: 使用 Transact-SQL 存储过程创建和运行跟踪
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eac3736784845b5dbae102bd91aa824b203a7ab8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88402473"
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a>使用 Transact-SQL 存储过程创建和运行跟踪
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  根据使用的是 Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 还是系统存储过程来创建和运行跟踪，用 SQL 跟踪进行跟踪的过程会有所不同。  
  
 除了 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，还可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系统存储过程来创建和运行跟踪。 通过系统存储过程进行跟踪的过程如下：  
  
1.  使用 **sp_trace_create**创建跟踪。  
  
2.  使用 **sp_trace_setevent**添加事件。  
  
3.  （可选）使用 **sp_trace_setfilter**设置筛选器。  
  
4.  使用 **sp_trace_setstatus**启动跟踪。  
  
5.  使用 **sp_trace_setstatus**停止跟踪。  
  
6.  使用 **sp_trace_setstatus**关闭跟踪。  
  
    > [!NOTE]  
    >  使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系统存储过程创建服务器端跟踪，这可以保证只要磁盘上有空间且不出现写入错误，就不会丢失任何事件。 如果磁盘已满或发生故障， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例会继续运行，但跟踪将停止。 如果设置了 **c2 audit mode** 且出现写入错误，跟踪将停止且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例关闭。 有关 **c2 audit mode** 设置的详细信息，请参阅 [c2 audit mode 服务器配置选项](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md)。  
  
## <a name="in-this-section"></a>本节内容  
  
|主题|描述|  
|-----------|-----------------|  
|[优化 SQL 跟踪](../../relational-databases/sql-trace/optimize-sql-trace.md)|说明如何降低跟踪对系统性能的影响。|  
|[筛选跟踪](../../relational-databases/sql-trace/filter-a-trace.md)|介绍使用筛选器进行跟踪。|  
|[限制跟踪文件和表的大小](../../relational-databases/sql-trace/limit-trace-file-and-table-sizes.md)|说明如何限制写入跟踪数据的文件和表的大小。 请注意，只有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 可以将跟踪信息写入表。|  
|[安排跟踪](../../relational-databases/sql-trace/schedule-traces.md)|说明如何设置跟踪的开始时间和结束时间。|  
  
## <a name="see-also"></a>另请参阅  
 [sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
