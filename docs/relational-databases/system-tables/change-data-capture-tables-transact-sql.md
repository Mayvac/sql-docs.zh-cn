---
description: 变更数据捕获表 (Transact-SQL)
title: 更改数据捕获表 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a4372d0b-50ca-4e58-80f6-2ed3cb52a84a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 38f2be3efcb798897849f249e63287ed6c49e496
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469056"
---
# <a name="change-data-capture-tables-transact-sql"></a>变更数据捕获表 (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  更改数据捕获时会对表启用更改跟踪，这样，对表所做的数据操作语言 (DML) 和数据定义语言 (DDL) 更改就可以增量加载到数据仓库中。 本节中的主题介绍存储变更数据捕获操作所用的信息的系统表。  
  
## <a name="in-this-section"></a>本节内容  
 [cdc. <capture_instance>_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
 为对关联源表中的已捕获列所做的每项更改返回一行。  
  
 [cdc.captured_columns](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
 为在捕获实例中跟踪的每一列返回一行。  
  
 [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
 为数据库中的每个更改表返回一行。  
  
 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)  
 为对启用了变更数据捕获的表所做的每一项数据定义语言 (DDL) 更改返回一行。  
  
 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)  
 为每个在更改表中存在行的事务返回一行。 该表用于在日志序列号 (LSN) 提交值和提交事务的时间之间建立映射。  
  
 [cdc.index_columns](../../relational-databases/system-tables/cdc-index-columns-transact-sql.md)  
 为与更改表关联的每个索引列返回一行。  
  
 [cdc_jobs &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
 返回变更数据捕获代理作业的配置参数。  
  
## <a name="see-also"></a>另请参阅  
 [更改数据捕获存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [变更数据捕获函数 (Transact-SQL)](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)  
  
  
