---
description: getLockTimeout 方法 (SQLServerDataSource)
title: getLockTimeout 方法 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f714a04f9e20254af91787867cc74e18218d2aa7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435749"
---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>getLockTimeout 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回指示数据库在报告锁定超时之前要等待的毫秒数的 int**** 值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>返回值  
 包含数据库要等待的毫秒数的 int**** 值。  
  
## <a name="remarks"></a>注解  
 锁定超时是指在等待多少毫秒后数据库报告锁定超时。默认值 -1 表示无限期等待。 如果指定，该值将成为此连接上所有语句的默认值。  
  
> [!NOTE]  
>  值为 0 表示不等待。 如果未设置 lockTimeout 属性，getLockTimeout 方法将返回默认值 -1。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
