---
description: isFirst 方法 (SQLServerResultSet)
title: isFirst 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ff94b95-32ad-4378-8bb1-970030527bb2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 05892bce86471733edca6a19a163603dc2a6bbce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433569"
---
# <a name="isfirst-method-sqlserverresultset"></a>isFirst 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索游标是否位于此 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象的第一行上。  
  
## <a name="syntax"></a>语法  
  
```  
  
public boolean isFirst()  
```  
  
## <a name="return-value"></a>返回值  
 如果游标在第一行，则为 true****。 如果游标在任何其他位置或结果集不包含任何行，则为 false****。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 isFirst 方法是由 java.sql.ResultSet 接口中的 isFirst 方法指定的。  
  
 如果将此方法用于前进游标和动态游标，则将引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
