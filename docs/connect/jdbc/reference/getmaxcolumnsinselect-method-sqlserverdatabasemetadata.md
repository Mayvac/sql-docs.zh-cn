---
description: getMaxColumnsInSelect 方法 (SQLServerDatabaseMetaData)
title: getMaxColumnsInSelect 方法 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnsInSelect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43c428df-ef91-4f55-81c3-49a4db3379cc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ec0c34e63e75839bcaeeb17119af996fb337e0a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435599"
---
# <a name="getmaxcolumnsinselect-method-sqlserverdatabasemetadata"></a>getMaxColumnsInSelect 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索此数据库在 SELECT 列表中允许的最大列数。  
  
## <a name="syntax"></a>语法  
  
```  
  
public int getMaxColumnsInSelect()  
```  
  
## <a name="return-value"></a>返回值  
 指示允许的最大列数的 int****。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getMaxColumnsInSelect 方法是由 java.sql.DatabaseMetaData 接口中的 getMaxColumnsInSelect 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
