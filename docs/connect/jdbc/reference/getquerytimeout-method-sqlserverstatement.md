---
description: getQueryTimeout 方法 (SQLServerStatement)
title: getQueryTimeout 方法 (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: efc25cfa3b1a43f8c818e66007245853d8159e24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434909"
---
# <a name="getquerytimeout-method-sqlserverstatement"></a>getQueryTimeout 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 等待此 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 对象运行的秒数。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>返回值  
 指示 JDBC 驱动程序将等待秒数的 int****，如果没有限制，则为 0。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getQueryTimeout 方法是由 java.sql.Statement 接口中的 getQueryTimeout 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerStatement 成员](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 类](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
