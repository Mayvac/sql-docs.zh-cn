---
title: Master 数据库
description: 了解并行数据仓库中的 master 数据库。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 7bf3928bfb21d34d0f60e6c52be8dae43621e4bd
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766736"
---
# <a name="master-database---parallel-data-warehouse"></a>Master 数据库-并行数据仓库
SQL Server PDW master 数据库存储设备级登录信息和数据库目录。 它是驻留在控制节点上 SQL Server 的 master 数据库。 在这种情况下，它提供了类似的功能，可以 SQL Server PDW 主 SQL Server 提供。  
  
有关系统数据库的详细信息，请参阅 [系统数据库](system-databases.md)。  
  
## <a name="limitations-and-restrictions"></a>限制和局限  
以下列表描述了无法对 SQL Server PDW master 数据库执行的操作。  
  
*不能：*  
  
-   执行 master 的差异备份。  
  
-   在 master 中创建用户对象。  
  
-   更改 master 的排序规则。  
  
-   更改 master 的所有者。  
  
-   删除或重命名 master。  
  
-   修改对 master 的权限。  
  
-   执行 **DBCC SHRINKLOG**。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|任务|说明|  
|--------|---------------|  
|创建 master 的完整备份。|示例：<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />有关详细信息，请参阅 [BACKUP DATABASE](../t-sql/statements/backup-transact-sql.md?view=aps-pdw-2016)。|  
|还原 master 数据库|若要还原 master 数据库，请使用 Configuration Manager 工具中的 " [还原 Master 数据库](restore-the-master-database.md) " 页。|  
|查看数据库目录信息。|`SELECT * FROM master.sys.databases;`|  
|查看系统范围的登录名和权限信息。|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
