---
description: SSTRANSTIGHTLYCPLD 字段 (SQLServerXAResource)
title: SSTRANSTIGHTLYCPLD 字段 (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f3161ceb41586e330bee39206700702cf3d36239
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431549"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>SSTRANSTIGHTLYCPLD 字段 (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  用于允许使用紧密结合的 XA 事务，这些事务具有不同的 XA 分支事务 ID (XID)，但具有相同的全局事务 ID (GTRID)。  
  
## <a name="syntax"></a>语法  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>字段值  
 一个 int**** 值：32768。  
  
## <a name="remarks"></a>注解  
 每个事务都由一个 XA 分支事务 ID (XID) 和全局事务 ID (GTRID) 标识。 为了允许应用程序使用紧密结合的 XA 事务，这些事务具有不同的 XID 但具有相同的 GTRID，你必须在 XAResource.start 方法的 flags 参数上设置 [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)。 有关如何使用此标志的详细信息，请参阅[了解 XA 事务](../../../connect/jdbc/understanding-xa-transactions.md)。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerXAResource 字段](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource 成员](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource 类](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
