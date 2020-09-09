---
description: sys.dm_os_volume_stats (Transact-SQL)
title: sys. dm_os_volume_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/06/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_volume_stats_TSQL
- dm_os_volume_stats
- sys.dm_os_volume_stats
- sys.dm_os_volume_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_volume_stats dynamic management function
ms.assetid: fa1c58ad-8487-42ad-956c-983f2229025f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 085659b4c6754bc2de68124dcb7d5c6fbbcdeb16
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539240"
---
# <a name="sysdm_os_volume_stats-transact-sql"></a>sys.dm_os_volume_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-2008R2SP1-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-2008R2sp1-xxxx-xxxx-xxx-md.md)]

  返回有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 中存储指定数据库和文件的操作系统卷（目录）的信息。 通过使用此动态管理函数，可以检查物理磁盘驱动器的属性，或返回有关目录的可用空间的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
sys.dm_os_volume_stats (database_id, file_id)  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a> 参数  
 database_id  
 数据库 ID。 database_id 的数据类型为 int，无默认值******。 不能为 NULL。  
  
 file_id  
 文件的 ID。 *file_id* 为 **int**，没有默认值。 不能为 NULL。  
  
## <a name="table-returned"></a>返回的表  
  
||||  
|-|-|-|  
|**列**|**Data type**|**说明**|  
|database_id|**int**|数据库 ID。 不能为 null。|  
|file_id|**int**|文件的 ID。 不能为 null。|  
|**volume_mount_point**|**nvarchar(512)**|根卷上的装入点。 可返回空字符串。|  
|**volume_id**|**nvarchar(512)**|操作系统卷 ID。 可以返回空字符串|  
|**logical_volume_name**|**nvarchar(512)**|逻辑卷名称。 可以返回空字符串|  
|**file_system_type**|**nvarchar(512)**|文件系统卷的类型（例如 NTFS、FAT、RAW）。 可以返回空字符串|  
|**total_bytes**|**bigint**|卷的总大小（字节）。 不能为 null。|  
|**available_bytes**|**bigint**|卷上的可用空间。 不能为 null。|  
|**supports_compression**|**bit**|指示卷是否支持操作系统压缩。 不能为 null。|  
|**supports_alternate_streams**|**bit**|指示卷是否支持备用流。 不能为 null。|  
|**supports_sparse_files**|**bit**|指示卷是否支持稀疏文件。  不能为 null。|  
|**is_read_only**|**bit**|指示卷当前是否标记为只读。 不能为 null。|  
|**is_compressed**|**bit**|指示此卷当前是否已压缩。 不能为 null。|  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>权限  
 需要 `VIEW SERVER STATE` 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-return-total-space-and-available-space-for-all-database-files"></a>A. 返回所有数据库文件的总空间和可用空间  
 下面的示例返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中所有数据库文件的总空间和可用空间（字节）。  
  
```sql  
SELECT f.database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.master_files AS f  
CROSS APPLY sys.dm_os_volume_stats(f.database_id, f.file_id);  
```  
  
### <a name="b-return-total-space-and-available-space-for-the-current-database"></a>B. 返回当前数据库的总空间和可用空间  
 下面的示例返回当前数据库中数据库文件的总空间和可用空间（字节）。  
  
```sql  
SELECT database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.database_files AS f  
CROSS APPLY sys.dm_os_volume_stats(DB_ID(f.name), f.file_id);  
```  
  
## <a name="see-also"></a>另请参阅  
 [sys. master_files &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
  
  
