---
description: supportsANSI92EntryLevelSQL 方法 (SQLServerDatabaseMetaData)
title: supportsANSI92EntryLevelSQL 方法 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsANSI92EntryLevelSQL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3fffc08-7254-4af7-bbae-8ff591fbd5ec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed62c28bfd0017e96ca90e9b62189588b01aad7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472079"
---
# <a name="supportsansi92entrylevelsql-method-sqlserverdatabasemetadata"></a>supportsANSI92EntryLevelSQL 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索此数据库是否支持 ANSI92 入门级 SQL 语法。  
  
## <a name="syntax"></a>语法  
  
```  
  
public boolean supportsANSI92EntryLevelSQL()  
```  
  
## <a name="return-value"></a>返回值  
 如果支持，则值为 true****。 否则为 **false**。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 supportsANSI92EntryLevelSQL 方法是由 java.sql.DatabaseMetaData 接口中的 supportsANSI92EntryLevelSQL 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
