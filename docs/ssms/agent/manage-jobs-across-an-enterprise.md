---
title: 管理整个企业内的作业
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b4eb4810d62a1ba669803997432c00ae4539e7db
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726985"
---
# <a name="manage-jobs-across-an-enterprise"></a>管理整个企业内的作业
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

如果在 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 以外对多服务器作业定义进行了更改，则必须将更改发布到下载列表中，以便目标服务器可以再次下载更新后的作业。 为了确保目标服务器具有当前的作业定义，在更新多服务器作业后，请发布一条 INSERT 指令，如下所示：  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
若要通知目标服务器多服务器作业已被修改，必须在使用以下任一过程之后调用前一个命令：  
  
-   [sp_add_jobstep (Transact-SQL)](https://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755)  
  
-   [sp_update_jobstep (Transact-SQL)](https://msdn.microsoft.com/e158802c-c347-4a5d-bf75-c03e5ae56e6b)  
  
-   [sp_delete_jobstep (Transact-SQL)](https://msdn.microsoft.com/421ede8e-ad57-474a-9fb9-92f70a3e77e3)  
  
-   [管理事件](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
-   [sp_detach_schedule (Transact-SQL)](https://msdn.microsoft.com/9a1fc335-1bef-4638-a33a-771c54a5dd19)  
  
    > [!NOTE]  
    > 调用 **sp_update_job** 或 **sp_delete_job** 后不需要调用 **sp_post_msx_operation**，因为这些存储过程会自动向下载列表发布所需的更改。  
  
以下是管理整个企业内的作业要执行的常规任务：  
  
**检查目标服务器的状态**  
  
-   [Transact-SQL](https://msdn.microsoft.com/f841d3bd-901a-4980-ad0b-1c6eeba3f717)  
  
-   [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**更改作业的目标服务器**  
  
-   [SQL Server Management Studio](../../ssms/agent/modify-the-target-servers-for-a-job.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/485252cc-0081-490a-9bd1-cbbd68eea286)  
  
-   [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**更改目标服务器的位置**  
  
-   [SQL Server Management Studio](../../ssms/agent/specify-a-target-server-s-location-sql-server-management-studio.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f)  
  
-   [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**同步目标服务器的时钟**  
  
-   [SQL Server Management Studio](../../ssms/agent/synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/40e44df7-d3e3-44ee-b149-08aba629a21f)  
  
**强制目标服务器轮询主服务器**  
  
-   [SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](https://msdn.microsoft.com/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>另请参阅  
[管理事件](../../ssms/agent/manage-events.md)  
  
