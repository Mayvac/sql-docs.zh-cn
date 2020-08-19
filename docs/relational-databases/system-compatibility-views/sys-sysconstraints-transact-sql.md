---
description: sys.sysconstraints (Transact-SQL)
title: Transact-sql)  (sys.sys约束 |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a50f67470a91af617ae76baadf1a029bfa56b59
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423331"
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  包含约束映射，映射到数据库中拥有该约束的对象。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|约束号。|  
|**id**|**int**|拥有该约束的表 ID。|  
|**colid**|**smallint**|在其中定义约束的列 ID。<br /><br /> 0 = 表约束|  
|**spare1**|**tinyint**|保留|  
|**status**|**int**|Pseudo-bit-mask 指示状态。 可能的值如下所示：<br /><br /> 1 = PRIMARY KEY 约束<br /><br /> 2 = UNIQUE KEY 约束<br /><br /> 3 = FOREIGN KEY 约束<br /><br /> 4 = CHECK 约束<br /><br /> 5 = DEFAULT 约束<br /><br /> 16 = 列级约束<br /><br /> 32 = 表级约束|  
|**actions**|**int**|保留|  
|**error**|**int**|保留|  
  
## <a name="see-also"></a>另请参阅  
 [将系统表映射到系统视图 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
