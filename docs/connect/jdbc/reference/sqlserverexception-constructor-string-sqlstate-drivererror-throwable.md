---
description: SQLServerException 构造函数 (java.lang.String, SQLState, DriverError, java.lang.Throwable)
title: SQLServerException 构造函数 (java.lang.String, SQLState, DriverError, java.lang.Throwable) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b25231da75962e6705d5a3fb0b620a39407034b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450454"
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>SQLServerException 构造函数 (java.lang.String, SQLState, DriverError, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  当 string**** 对象、sqlstate**** 对象、drivererror**** 对象和 throwable**** 对象给定时，初始化[ SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) 类的新实例。

## <a name="syntax"></a>语法  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>参数  
 *errText*  
  
 包含错误文本的字符串。
  
 *sqlState*  
  
 保留 SQL 状态的枚举对象。
 
 driverError**  
  
 保留驱动程序错误的枚举对象。
 
 *cause*  
  
 保留异常引发原因的 throwable 对象。
  
## <a name="see-also"></a>另请参阅  
 [SQLServerException 构造函数](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException 成员](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException 类](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
