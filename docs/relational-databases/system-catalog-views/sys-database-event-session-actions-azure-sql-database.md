---
description: sys.database_event_session_actions（Azure SQL 数据库）
title: database_event_session_actions (Azure SQL 数据库) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 32494df1-7ab7-4b88-a858-6b1021d67433
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1ecfcd40d79e3374663259648fa3447db96e6986
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542623"
---
# <a name="sysdatabase_event_session_actions-azure-sql-database"></a>sys.database_event_session_actions（Azure SQL 数据库）
[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  返回针对事件会话的每个事件执行的每个操作所对应的行。  
  
||  
|-|  
|**适用**于： [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 和任何更高版本。|  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|事件会话的 ID。 不可为 null。|  
|event_id|**int**|事件的 ID。 此 ID 在事件会话对象中是唯一的。 不可为 null。|  
|name|**sysname**|操作的名称。 可以为 Null。|  
|包|**sysname**|包含事件的事件包的名称。 可以为 Null。|  
|name|**sysname**|包含事件的模块的名称。 可以为 Null。|  
  
## <a name="permissions"></a>权限  
 要求对服务器具有 VIEW DATABASE STATE 权限。  
  
## <a name="remarks"></a>备注  
 此视图具有下列关系基数。  
  
| From | 到 | 关系 |
| ---- | -- | ------------ |
|sys. database_event_session_actions event_session_id|sys.sys. database_event_sessions。 event_session_id|多对一|  
|sys. database_event_session_actions event_id<br /><br /> sys. database_event_session_actions event_session_id|sys. database_event_session_events event_session_id<br /><br /> sys. database_event_session_events event_id|多对一|  
  
  
