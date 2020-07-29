---
title: 作业属性 - 新建作业（“常规”页）
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: eeb3b97ab94c9510ae66b3ebf6c018799dcf07a1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764126"
---
# <a name="job-properties---new-job-general-page"></a>作业属性 - 新建作业（“常规”页）
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此页可以查看和修改 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的常规属性。  
  
## <a name="options"></a>选项  
**名称**  
更改作业的名称。  
  
**所有者**  
选择作业的所有者。  
  
**类别**  
为作业选择作业类别。  
  
**...**  
查看所选类别的作业。  
  
**说明**  
更改作业的说明。  
  
**已启用**  
启用作业。 虽然可以使用 **sp_start_job** 存储过程启动作业，但是如果不启用作业，作业将不会响应计划或警报。  
  
**数据源**  
显示作业的主服务器。 仅在“作业属性”-“常规”  页上可用。  
  
**创建时间**  
显示作业的创建日期和时间。 仅在“作业属性”-“常规”  页上可用。  
  
**上次修改时间**  
显示上次修改作业的日期和时间。 仅在“作业属性”-“常规”  页上可用。  
  
**上次执行时间**  
显示上次执行作业的日期和时间。 仅在“作业属性”-“常规”  页上可用。  
  
**查看作业历史记录**  
查看作业的历史记录。 仅在“作业属性”-“常规”  页上可用。  
  
## <a name="see-also"></a>另请参阅  
[执行作业](../../ssms/agent/implement-jobs.md)  
[作业类别 - 管理作业类别](../../ssms/agent/job-categories-manage-job-categories.md)  
  
