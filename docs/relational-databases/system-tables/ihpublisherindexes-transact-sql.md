---
title: IHpublisherindexes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fc84090e08c3c8890a4613e6f73e1914209c0ba7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750173"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  使用当前分发服务器从非 SQL Server 发布服务器复制的每个索引在**IHpublisherindexes**系统表中各占一行。 此表存储在分发数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|标识已发布的索引。|  
|table_id****|**int**|标识索引所属的[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)中的表。|  
|**publisher_id**|**smallint**|标识从中发布索引的非 SQL Server 发布服务器。|  
|name|**sysname**|已发布的索引的名称。|  
|**type**|**nvarchar(255)**|[IHindextypes](../../relational-databases/system-tables/ihindextypes-transact-sql.md)系统表中支持的索引类型。|  
  
## <a name="see-also"></a>另请参阅  
 [异类数据库复制](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Transact-sql&#41;&#40;复制表](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
