---
description: getRowIdLifetime 方法 (SQLServerDatabaseMetaData)
title: getRowIdLifetime 方法 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c67c88abc02faccc1b6a4e391eee674e7d99112f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434709"
---
# <a name="getrowidlifetime-method-sqlserverdatabasemetadata"></a>getRowIdLifetime 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回一种状态，该状态指示 SQL RowId 数据类型是否受支持。 如果受支持，则返回 RowId 对象保持有效的生存期。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## <a name="return-value"></a>返回值  
 RowIdLifetime 对象。  
  
> [!NOTE]  
>  在 JDBC 驱动程序版本 2.0 中，此方法将返回 java.sql.RowIdLifetime.ROWID_UNSUPPORTED 值。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getRowIdLifetime 方法是由 java.sql.DatabaseMetaData 接口中的 getRowIdLifetime 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
