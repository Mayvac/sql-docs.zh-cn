---
description: getParameterMetaData 方法 (SQLServerPreparedStatement)
title: getParameterMetaData 方法 (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.getParameterMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c2876dec-ce29-4b61-9d74-ec3173b8cba5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a5de2959f5c3116b3023499fbc2600256ad57d4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435029"
---
# <a name="getparametermetadata-method-sqlserverpreparedstatement"></a>getParameterMetaData 方法 (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索此 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 对象的参数的个数、类型及属性。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final java.sql.ParameterMetaData getParameterMetaData()  
```  
  
## <a name="return-value"></a>返回值  
 [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getParameterMetaData 方法是由 java.sql.PreparedStatement 接口中的 getParameterMetaData 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement 类](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
