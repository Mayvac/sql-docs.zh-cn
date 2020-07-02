---
title: sp_helpfilegroup （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c59a7c87c2252497a8a7865c179939a601039157
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733176"
---
# <a name="sp_helpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  返回与当前数据库相关联的文件组的名称及属性。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>自变量  
`[ @filegroupname = ] 'name'`当前数据库中任意文件组的逻辑名称。 *名称*为**sysname**，默认值为 NULL。 如果未指定*name* ，则列出当前数据库中的所有文件组，并仅显示 "结果集" 部分中显示的第一个结果集。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**groupname**|**sysname**|文件组的名称。|  
|**groupid**|**smallint**|数字文件组标识符。|  
|**filecount**|**int**|文件组中的文件数目。|  
  
 如果指定*name* ，则返回文件组中的每个文件对应一行。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|文件组中文件的逻辑名称。|  
|**fileid**|**smallint**|数字文件标识符。|  
|**filename**|**nchar （260）**|文件的物理名称，包括目录路径。|  
|size |**nvarchar （15）**|文件大小 (KB)。|  
|**maxsize**|**nvarchar （15）**|文件的最大大小。<br /><br /> 这是文件可增长到的最大大小。 此字段中的 UNLIMITED 值表示文件可以一直增长到磁盘变满为止。|  
|**growth**|**nvarchar （15）**|文件的增量。 表示每次需要新的空间时给文件增加的空间大小。<br /><br /> 0 = 文件的大小是固定的，不会增长。|  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. 返回数据库中的所有文件组  
 下面的示例返回有关 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库中文件组的信息。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>B. 返回文件组中的所有文件  
 下面的示例返回有关 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库的 `PRIMARY` 文件组中所有文件的信息。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据库引擎存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys. database_files &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. master_files &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [&#40;Transact-sql&#41;系统存储过程](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [数据库文件和文件组](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
