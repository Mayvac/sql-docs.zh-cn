---
title: FILEGROUP_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILEGROUP_NAME_TSQL
- FILEGROUP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- displaying filegroup names
- identification numbers [SQL Server], filegroups
- filegroups [SQL Server], IDs
- IDs [SQL Server], filegroups
- FILEGROUP_NAME function
- filegroups [SQL Server], names
- names [SQL Server], filegroups
- viewing filegroup names
ms.assetid: 26add1c0-56e5-47a8-b489-ae56784a7ee9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 329b354b5b5e3fe66637962d2808742083c4cfac
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85895752"
---
# <a name="filegroup_name-transact-sql"></a>FILEGROUP_NAME (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

此函数返回指定文件组标识 (ID) 号的文件组名。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
FILEGROUP_NAME ( filegroup_id )   
```  
  
## <a name="arguments"></a>参数  
 *filegroup_id*  

文件组名 `FILEGROUP_NAME` 将返回的文件组 ID 号。 filegroup_id  具有 smallint  数据类型。  
  
## <a name="return-types"></a>返回类型  
**nvarchar(128)**  
  
## <a name="remarks"></a>备注  
filegroup_id  对应于 sys.filegroups  目录视图的 data_space_id  列。  
  
## <a name="examples"></a>示例  
此示例将返回 `1` 数据库中文件组 ID [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 的文件组名称。  
  
```  
SELECT FILEGROUP_NAME(1) AS [Filegroup Name];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Filegroup Name   
-----------------------  
PRIMARY  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>另请参阅  
 [元数据函数 (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
