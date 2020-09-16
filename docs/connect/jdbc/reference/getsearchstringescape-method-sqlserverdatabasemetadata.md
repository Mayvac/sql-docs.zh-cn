---
description: getSearchStringEscape 方法 (SQLServerDatabaseMetaData)
title: getSearchStringEscape 方法 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5801a6a971a0714af8408fa15c206770b9101bd5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434629"
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>getSearchStringEscape 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索可用于转义通配符的 String**** 值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>返回值  
 包含转义通配符字符串的 String****。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getSearchStringEscape 方法是由 java.sql.DatabaseMetaData 接口中的 getSearchStringEscape 方法指定的。  
  
 此方法仅用于元数据模式搜索。 它返回“\\”。 String**** 搜索模式可以对通配符（“%”和“_”）进行转义，并通过在这些通配符之前加反斜杠将其作为文字提供。 这样可将“\\%”转换为“[%]”，将“\\\_”转换为“[\_]”。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
