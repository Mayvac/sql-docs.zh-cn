---
description: MSpublicationthresholds (Transact-SQL)
title: MSpublicationthresholds (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8f43705f8fec92e39e55a4fa4f62cf24aa9f25be
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540290"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSpublicationthresholds**表用于跟踪发布的复制性能指标，其中每一行对应于所监视的每个阈值。 此表存储在分发数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|标识已为其设置阈值的发布。|  
|**metric_id**|**int**|标识按 [MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) 系统表中的定义监视的复制性能指标。|  
|**value**|**sql_variant**|受监视的跃点的阈值。|  
|**shouldalert**|**bit**|值为 **1** 表示当指标超出定义的阈值时，应生成警报。|  
|**isenabled**|**bit**|如果值为 **1** ，则表示为此复制性能指标启用了监视。|  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;复制表 ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
