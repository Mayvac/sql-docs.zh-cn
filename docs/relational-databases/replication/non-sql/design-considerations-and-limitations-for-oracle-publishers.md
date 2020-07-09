---
title: 注意事项和限制（Oracle 发布服务器）
description: 介绍使用 Oracle 发布服务器配置 SQL Server 订阅服务器时的设计注意事项和限制。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], design considerations and limitations
ms.assetid: 8d9dcc59-3de8-4d36-a61f-bc3ca96516b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 08fa9ac127d663636d77d8fd9b8483303d17b235
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892487"
---
# <a name="design-considerations-and-limitations-for-oracle-publishers"></a>Oracle 发布服务器的设计注意事项和限制
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  在设计上，从 Oracle 数据库中进行发布与从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中进行发布几乎一样。 不过，还应注意下列限制和问题：  
  
-   “Oracle Gateway”选项的性能优于“Oracle Complete”选项；但是，此选项不能用于在多个事务发布中发布同一个表。 一个表最多只能出现在一个事务发布中，但可以出现在任意多个快照发布中。 如果需要在多个事务发布中发布同一个表，请选择“Oracle Complete”选项。  
  
-   复制支持发布表、索引和具体化视图， 不能复制其他对象。  
  
-   Oracle 数据库与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库在对数据的存储和处理方面有一些会影响复制的小差异。  
  
-   当使用 Oracle 发布服务器时，在如何支持事务复制功能方面存在一些差异。  
  
## <a name="support-for-publishing-objects-from-oracle"></a>支持从 Oralce 中发布对象  
 复制支持从 Oracle 数据库中复制下列对象：  
  
-   表  
  
-   按照索引组织的表  
  
-   索引  
  
-   具体化视图（按表复制）  
  
 下列内容可以出现在已发布表上，但不会复制这些内容：  
  
-   基于域的索引  
  
-   基于函数的索引  
  
-   默认值  
  
-   检查约束  
  
-   外键  
  
-   存储选项（表空间、群集等）  
  
 不能复制下列对象：  
  
-   嵌套表  
  
-   视图  
  
-   包、包正文、过程和触发器  
  
-   队列  
  
-   序列  
  
-   同义词  
  
 有关支持的数据类型的信息，请参阅 [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)。  
  
## <a name="differences-between-oracle-and-sql-server"></a>Oracle 和 SQL Server 之间的区别  
  
-   Oracle 对某些对象有不同的最大大小限制。 在 Oracle 发布数据库中创建的任何对象都应遵守 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中相应对象的最大大小限制。 若要了解 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的限制，请参阅 [SQL Server 的最大容量规范](../../../sql-server/maximum-capacity-specifications-for-sql-server.md)。  
  
-   默认情况下，Oracle 对象的名称用大写字母创建。 通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器发布 Oracle 对象时，如果这些对象的名称在 Oracle 数据库中为大写，则必须确保以大写形式提供这些对象的名称。 如果不按正确的大小写指定对象，可能会产生错误消息，指示找不到对象。  
  
-   Oracle 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]在 SQL 语言上稍有差别，行筛选器应以与 Oracle 兼容的语法编写。  
  
### <a name="considerations-for-large-objects"></a>大型对象的注意事项  
 大型对象 (LOB) 数据并不存储在项目日志表中，LOB 数据的更新始终是从已发布的表中直接检索的。 只有当影响 LOB 的操作激发了复制的表上的复制触发器时，才会在事务发布中复制更新。 插入或删除包含 LOB 的行时，将激发 Oracle 触发器；但更新 LOB 列并不会激发触发器。 只有在同一 Oracle 事务中同时更新同一行的 LOB 列和非 LOB 列时，才会立即复制 LOB 列的更新。 否则，只有在下一次更新该行中的非 LOB 列时，才会刷新订阅服务器中的 LOB 列。 请确保您的应用程序可以接受此行为。  
  
 若要在事务发布中复制 LOB 列的更新，请在编写应用程序时考虑使用下列策略之一：  
  
-   在事务中删除并重新插入行，而不是更新行：重新插入行时指定新的 LOB。 因为删除和插入操作都会激发触发器，所以将复制行。  
  
-   除了 LOB 列外，还要在行更新中包括一个非 LOB 列，或在同一 Oracle 事务中更新该行的非 LOB 列。 在这两种情况下，更新非 LOB 列可确保激发触发器。  
  
 有关 LOB 的详细信息，请参阅 [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)。  
  
### <a name="unique-indexes-and-constraints"></a>唯一索引和约束  
 对于快照和事务复制，唯一索引和约束（包括主键约束）中包含的列必须遵守特定的限制。 如果不遵守这些限制，将不复制约束或索引。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 索引中允许的最大列数为 16。  
  
-   唯一约束中包含的所有列都必须具有支持的数据类型。 有关数据类型的详细信息，请参阅 [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)。  
  
-   唯一约束中包含的所有列都必须发布（不能进行筛选）。  
  
-   唯一约束或索引中包含的列都不应为 Null。  
  
 还要考虑下列问题：  
  
-   Oracle 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 处理 NULL 的方式有所不同：对于允许 NULL 值并包含在唯一约束或索引中的列，Oracle 允许存在多个值为 NULL 的行。 而在[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，同一列只允许存在一个值为 NULL 的行，以确保唯一性。 不能发布允许 NULL 值的唯一约束或索引，因为对于索引或约束中包含的任何列，如果已发布的表中包含多个值为 NULL 的行，订阅服务器中将出现违反约束的情况。  
  
-   测试唯一性时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将忽略字段中的尾随空格，而 Oracle 则不会忽略。  
  
 与在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 事务复制中一样，Oracle 事务发布中的表需要具有主键；根据上述规则，主键必须唯一。 如果主键不符合上述规则，则不能为事务复制发布表。  
  
## <a name="differences-between-oracle-publishing-and-standard-transactional-replication"></a>Oracle 发布与标准事务复制之间的区别  
  
-   Oracle 发布服务器不能与以下服务器同名：其 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器；使用分发服务器的任何 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 发布服务器；或接收发布的任何订阅服务器。 由同一分发服务器提供服务的每个发布都必须具有唯一的名称。  
  
-   在 Oracle 发布中发布的表不能接收复制的数据。 因此，Oracle 发布不支持以下功能：包含立即更新订阅或排队更新订阅的发布；或者其中发布表还作为订阅表的拓扑，例如，对等和双向复制。  
  
-   Oracle 数据库中主键与外键的关系不会复制到订阅服务器中。 但是，在传递更改时，会在数据中保持这种关系。  
  
-   标准事务发布支持表的最大列数为 1000。 Oracle 事务发布支持 995 列（进行复制时，将向每个已发布表中添加 5 列）。  
  
-   在 CREATE TABLE 语句中添加了 Collate 子句，以启用区分大小写的比较，这对主键和唯一约束非常重要。 此行为通过架构选项 0x1000 控制，该选项使用 [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) 的 `@schema_option` 参数指定。  
  
-   如果使用存储过程来配置或维护 Oracle 发布服务器，请不要将存储过程放到显式事务中。 用于连接 Oracle 发布服务器的链接服务器不支持这一操作。  
  
-   如果使用向导创建 Oracle 发布的请求订阅，则必须使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 和更高版本提供的新建订阅向导。 而对于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的早期版本，可以使用存储过程和 SQL-DMO 接口来设置 Oracle 发布的请求订阅。  
  
-   如果使用存储过程向订阅服务器传播更改（默认方式），请注意虽然支持 MCALL 语法，但当发布来自 Oracle 发布服务器时，该语法的行为会有所不同。 通常，MCALL 提供一个位图，用于显示在发布服务器中更新的列。 对于 Oracle 发布，位图始终显示已更新的所有列。 若要详细了解如何使用存储过程，请参阅[指定如何传播事务项目的更改](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)。  
  
### <a name="transactional-replication-feature-support"></a>事务复制功能支持  
  
-   对于 SQL Server 发布支持的架构选项，Oracle 发布并非都支持。 有关架构选项的详细信息，请参阅 [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)。  
  
-   Oracle 发布的订阅服务器不能使用立即更新订阅或排队更新订阅，也不能作为对等或双向拓扑中的节点。  
  
-   Oracle 发布的订阅服务器不能从备份中自动初始化。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支持两种验证：二进制验证和行计数验证。 Oracle 发布服务器支持行计数验证。 有关详细信息，请参阅[验证已复制的数据](../../../relational-databases/replication/validate-data-at-the-subscriber.md)。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 提供了两种快照格式：本机 bcp 模式和字符模式。 Oracle 发布服务器支持字符模式快照。  
  
-   不支持对已发布的 Oracle 表进行架构更改。 若要更改架构，请先删除发布，进行更改，然后重新创建发布和任何订阅。  
  
    > [!NOTE]  
    >  如果在已发布的表中没有发生任何活动时执行架构更改以及发布和订阅的后续删除与重新创建，则可以为订阅指定“仅支持复制”选项。 这样不用将快照复制到每个订阅服务器上就能使订阅同步。 有关详细信息，请参阅 [初始化事务订阅（不使用快照）](../../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)中手动初始化订阅。  
  
### <a name="replication-security-model"></a>复制安全模式  
 Oracle 发布的安全模式与标准事务复制的安全模式相同，但下列情况除外：  
  
-   通过下列方法之一指定快照代理和日志读取器代理在分发服务器和发布服务器之间建立连接时使用的帐户：  
  
    -   [sp_adddistpublisher &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md) 的 `@security_mode` 参数（如果使用 Oracle 身份验证，则也请指定 `@login` 和 `@password` 的值）  
  
    -   在 SQL Server Management Studio 的 **“连接到服务器”** 对话框中，在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器上配置 Oracle 发布服务器时就使用这种方法。  
  
     在标准事务复制中，使用 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) 和 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) 指定帐户。  
  
-   不能使用 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) 或通过属性表来更改快照代理和日志读取器代理建立连接时使用的帐户，但可以更改密码。  
  
-   如果将 [sp_adddistpublisher &#40;Transact-SQL&#41;`@security_mode` 的 ](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)参数值指定为 1（Windows 集成身份验证）：  
  
    -   快照代理和日志读取器代理使用的进程帐户和密码（[sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) 和 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) 的 `@job_login` 和 `@job_password` 参数）必须与连接 Oracle 发布服务器时使用的帐户和密码相同。  
  
    -   不能通过 [sp_changepublication_snapshot &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) 或 [sp_changelogreader_agent &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md) 更改 `@job_login` 参数，但可以更改密码。  
  
 有关复制安全性的详细信息，请参阅[查看和修改复制安全设置](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Oracle 发布服务器的管理注意事项](../../../relational-databases/replication/non-sql/administrative-considerations-for-oracle-publishers.md)   
 [配置 Oracle 发布服务器](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle 发布概述](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
