---
description: getRef 方法 (int)
title: getRef 方法 (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getRef (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 905dd02a-0c7f-475b-8be4-341b4359c766
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0afbd40e226ff0f2c15c9d666b09f2c7b6873712
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434889"
---
# <a name="getref-method-int"></a>getRef 方法 (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根据给定的参数索引，检索指定参数作为 Java 编程语言中的 Ref 对象的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.Ref getRef(int i)  
```  
  
#### <a name="parameters"></a>参数  
 *i*  
  
 指示参数索引的 int****。  
  
## <a name="return-value"></a>返回值  
 Ref 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getRef 方法是由 java.sql.CallableStatement 接口中的 getRef 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [getRef 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getref-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 类](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
