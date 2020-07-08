---
title: 使用 OPENROWSET BULK 行集提供程序批量导入大型对象数据
description: SQL Server OPENROWSET Bulk 行集提供程序支持作为大型对象数据批量导入。 支持的类型是 varbinary(max)、varchar(max) 和 nvarchar(max)。
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 3c998b1efeb6fff7726161ffb02e240e8a8847f1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85640704"
---
# <a name="bulk-import-large-object-data-with-openrowset-bulk-rowset-provider-sql-server"></a>使用 OPENROWSET BULK 行集提供程序批量导入大型对象数据 (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET 大容量行集提供程序使您可以将数据文件作为大型对象数据大容量导入。  
  
 OPENROWSET 大容量行集提供程序支持的大型对象数据类型为 **varbinary**(max) 或 **image**、 **varchar**(max) 或 **text**以及 **nvarchar**(max) 或 **ntext**。  
  
> [!NOTE]  
>  不推荐使用 **image**、 **text** 和 **ntext** 数据类型。  
  
 OPENROWSET BULK 子句支持通过三个选项以单行或单列行集导入数据文件的内容。 您可以指定其中一个大型对象选项，而不是使用格式化文件。 这些选项如下所示：  
  
 SINGLE_BLOB  
 以单行读取 *data_file* 的内容，以 **varbinary(max)** 类型的单列行集返回内容。  
  
 SINGLE_CLOB  
 以字符读取指定数据文件的内容，以 **varchar(max)** 类型的单行、单列行集返回内容，使用的是当前数据库的排序规则，例如文本或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word 文档。  
  
 SINGLE_NCLOB  
 以 Unicode 读取指定数据文件的内容，以 **nvarchar(max)** 类型的单行、单列行集返回内容，并使用当前数据库的排序规则。  
  
## <a name="see-also"></a>另请参阅  
 [使用 BULK INSERT 或 OPENROWSET (BULK...) 导入批量数据 (SQL Server)](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [在批量导入期间保留 Null 或使用默认值 (SQL Server)](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)   
 [bcp 实用工具](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  
