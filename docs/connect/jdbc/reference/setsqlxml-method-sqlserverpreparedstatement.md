---
description: setSQLXML 方法 (SQLServerPreparedStatement)
title: setSQLXML 方法 (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 70bbdde0-75f7-4169-88c5-dbbe2c4bcd03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 352f46f4cbe8387aaffbf0eb0f13d6046c1db5b8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458289"
---
# <a name="setsqlxml-method-sqlserverpreparedstatement"></a>setSQLXML 方法 (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为指定的 SQLXML 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setSQLXML(int parameterIndex,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>参数  
 parameterIndex**  
  
 指示参数索引的 int****。  
  
 xmlObject**  
  
 包含参数值的 SQLXML 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 setSQLXML 方法是由 java.sql.PreparedStatement 接口中的 setSQLXML 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
