---
title: Disable or Enable a Job
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bb548d5284001bd8491bf97706f2a9d497d7c31f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85690827"
---
# <a name="disable-or-enable-a-job"></a>Disable or Enable a Job
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中禁用 [!INCLUDE[tsql](../../includes/tsql-md.md)]代理作业。 禁用作业不会将其删除，必要时可以再次启用该作业。  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>开始之前  
  
### <a name="security"></a><a name="Security"></a>安全性  
有关详细信息，请参阅[实现 SQL Server 代理安全性](../../ssms/agent/implement-sql-server-agent-security.md)。  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>使用 SQL Server Management Studio  
  
#### <a name="to-disable-or-enable-a-job"></a>禁用或启用作业  
  
1.  在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]的实例，然后展开该实例。  
  
2.  展开 **“SQL Server 代理”** 。  
  
3.  展开“作业”  ，然后右键单击要禁用或启用的作业。  
  
4.  若要禁用作业，请单击 **“禁用”** 。 若要启用作业，请单击 **“启用”** 。  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>使用 Transact-SQL  
  
#### <a name="to-disable-or-enable-a-job"></a>禁用或启用作业  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde_md.md)]的实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。  
  
    ```  
    -- changes the name, description, and disables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 0 ;  
    GO  
    ```  
  
有关详细信息，请参阅 [sp_update_job (Transact-SQL)](https://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623)。  
  
