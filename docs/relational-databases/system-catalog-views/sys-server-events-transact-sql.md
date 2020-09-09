---
description: sys.server_events (Transact-SQL)
title: sys. server_events (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_events_TSQL
- sys.server_events_TSQL
- server_events
- sys.server_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_events catalog view
ms.assetid: 996f6c9b-6426-4847-95d9-6b77541422be
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f451456320e7248f48be5a9b7233f1a6cf5b2968
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551366"
---
# <a name="sysserver_events-transact-sql"></a>sys.server_events (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  包含的每一行都对应于要为其激发服务器级事件通知或服务器级 DDL 触发器的一个事件。 **Object_id**和**类型**的列唯一标识服务器事件。  

  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|object_id|**int**|要激发的服务器级事件通知或服务器级 DDL 触发器的 ID。|  
|type|**int**|导致激发事件通知或 DDL 触发器的事件的类型。|  
|**type_desc**|**nvarchar(60)**|对导致激发 DDL 触发器或事件通知的事件的说明。|  
|**event_group_type**|**int**|要对其创建触发器或事件通知的事件组，如果未对事件组中创建触发器或事件通知，则为 Null。|  
|**event_group_type_desc**|**nvarchar(60)**|要对其创建触发器或事件通知的事件组的说明，如果未对事件组创建触发器或事件通知，则为 Null。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [对象目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
