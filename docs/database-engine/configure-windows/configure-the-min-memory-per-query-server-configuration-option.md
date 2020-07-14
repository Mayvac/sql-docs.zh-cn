---
title: 配置 min memory per query 服务器配置选项 | Microsoft Docs
description: 了解如何使用“每次查询占用的最小内存”选项指定 SQL Server 为查询分配的最小内存授予或最小千字节数。
ms.custom: ''
ms.date: 11/24/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
- min memory grant
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 784dc57403cdb5c8dad6ba3e8f910ecd6d4dee26
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85696848"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>配置每次查询占用的最小内存服务器配置选项
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  本主题说明了如何使用 **或** 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “每次查询占用的最小内存” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。 “每次查询占用的最小内存”选项指定将分配给查询执行时所需要的最小内存量 (KB)。 这也称为最小内存授予。 例如，如果将 **min memory per query** 设置为 2048 KB，则查询保证将至少获取那么多的总内存。 默认值为 1,024 KB。 最小值为 512 KB，最大值为 2,147,483,647 KB (2 GB)。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [建议](#Recommendations)  
  
     [安全性](#Security)  
  
-   **若要配置每次查询占用的最小内存选项，请使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **跟进：** [在配置每次查询占用的最小内存选项之后](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 限制和局限  
  
-   min memory per query 的量优先于 [index create memory](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) 选项。 如果改变这两个选项，并且索引创建内存小于每次查询占用的最小内存，则将收到警告消息，但仍会设置值。 在查询执行期间会收到另一个类似警告。  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> 建议  
  
-   此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 专业人员更改。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查询处理器尝试确定要分配给查询的最佳内存量。 min memory per query 选项允许管理员指定任何单个查询收到的最小内存量。 如果查询需要对大量数据执行哈希和排序操作，则这些查询获得的内存通常比该选项指定的最小内存多。 对于一些小型查询和中等大小的查询，增大 min memory per query 的值可能提高性能，但会导致内存资源争夺加剧。 min memory per query 选项包括为排序操作分配的内存。  

-    不要将 min memory per query 服务器配置选项设置得太高，尤其是在非常繁忙的系统上，因为查询将不得不等到<sup>1</sup>能确保占有所请求的最小内存、或直到时间超过 query wait 服务器配置选项内所指定的值。 如果可用内存比执行查询所需的指定最小内存多，则只要查询能对多出的内存加以有效的利用，就可以使用多出的内存。     

<sup>1</sup>在此方案中，等待类型通常是 RESOURCE_SEMAPHORE。 有关详细信息，请参阅 [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)。

###  <a name="security"></a><a name="Security"></a> Security  
  
####  <a name="permissions"></a><a name="Permissions"></a> 权限  
 默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。 若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。 ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>配置每次查询占用的最小内存选项  
  
1.  在对象资源管理器中，右键单击服务器并选择 **“属性”** 。  
  
2.  单击 **“内存”** 节点。  
  
3.  在“每次查询占用的最小内存”框中，输入将分配给查询执行时所需要的最小内存量 (KB)。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>配置每次查询占用的最小内存选项  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。 本示例演示如何使用 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 将 `min memory per query` 选项的值设置为 `3500` KB。  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO    
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a> 跟进：在配置每次查询占用的最小内存选项之后  
 该设置将立即生效，无需重新启动服务器。  
  
## <a name="see-also"></a>另请参阅  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [配置 index create memory 服务器配置选项](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md)     
 [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)     
 [sys.dm_exec_query_memory_grants (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)
  
  
