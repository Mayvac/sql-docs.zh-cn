---
description: IHconstrainttypes (Transact-SQL)
title: IHconstrainttypes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHconstrainttypes_TSQL
- IHconstrainttypes
dev_langs:
- TSQL
helpviewer_keywords:
- IHconstrainttypes system table
ms.assetid: 955d6fa9-0b31-4335-a3cd-e4c4d90ad308
author: markingmyname
ms.author: maghan
ms.openlocfilehash: eaa7ef45e9e6b9ae71eceee558af116fe3314449
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540369"
---
# <a name="ihconstrainttypes-transact-sql"></a>IHconstrainttypes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  对于非 SQL Server 发布服务器所支持的每种类型的非 SQL Server 约束， **IHconstrainttypes** 系统表中各占一行。 此表存储在分发数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|type|**nvarchar(255)**|受支持的非 SQL Server 约束类型的名称。|  
  
## <a name="see-also"></a>另请参阅  
 [异类数据库复制](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Transact-sql&#41;&#40;复制表 ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
