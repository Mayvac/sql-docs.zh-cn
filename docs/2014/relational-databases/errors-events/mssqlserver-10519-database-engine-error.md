---
title: MSSQLSERVER_10519 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c4468770227fff4915ed701f6973baeee3cc251
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552372"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
    
## <a name="details"></a>详细信息  
  
|Attribute|值|  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|10519|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|消息正文|无法创建计划指南 '%.\*ls'，因为 `@hints` 中指定的提示无法应用于 `@stmt` 或 `@statement_start_offset` 指定的语句。 请确保提示可以应用于该语句。|  
  
## <a name="explanation"></a>说明  
 `@hints` 中指定的语句无法应用于 `@stmt` 或 `@statement_start_offset` 指定的语句。  
  
## <a name="user-action"></a>用户操作  
 请指定可以应用于该语句的提示。  
  
## <a name="see-also"></a>另请参阅  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [计划指南](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
