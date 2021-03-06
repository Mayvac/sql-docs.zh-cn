---
description: sys.database_event_session_events（Azure SQL 数据库）
title: database_event_session_events (Azure SQL 数据库) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: f4c9eb0a-173c-4c66-8dd8-6f7176b2657f
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d116c44d686398f4cb76d3443f10c8a85309727f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542564"
---
# <a name="sysdatabase_event_session_events-azure-sql-database"></a>sys.database_event_session_events（Azure SQL 数据库）
[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  返回事件会话中每个事件所对应的行。  
  
||  
|-|  
|**适用**于： [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 和任何更高版本。|  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|事件会话的 ID。 不可为 null。|  
|event_id|**int**|事件的 ID。 此 ID 在事件会话对象中是唯一的。 不可为 null。|  
|name|**sysname**|事件的名称。 不可为 null。|  
|包|**sysname**|包含事件的事件包的名称。 不可为 null。|  
|name|**sysname**|包含事件的模块的名称。 不可为 null。|  
|predicate|**nvarchar (3000) **|应用于事件的谓词表达式。 可以为 Null。|  
|predicate_xml|**nvarchar (3000) **|应用于事件的 XML 谓词表达式。 可以为 Null。|  
  
## <a name="permissions"></a>权限  
 要求对服务器具有 VIEW DATABASE STATE 权限。  
  
## <a name="remarks"></a>备注  
 此视图具有下列关系基数。  
  
| From | 到 | 关系 |
| ---- | -- | ------------ |
|sys. database_event_session_events event_session_id|sys. database_event_sessions event_session_id|多对一|  
  
## <a name="see-also"></a>另请参阅  
 [扩展事件](../../relational-databases/extended-events/extended-events.md)  
  
  
