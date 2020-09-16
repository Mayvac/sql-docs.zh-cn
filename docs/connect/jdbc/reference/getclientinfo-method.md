---
description: getClientInfo 方法 ()
title: getClientInfo 方法 () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31c88ff13769c192c9fdc468cd21d2b3f2a12dbe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436679"
---
# <a name="getclientinfo-method-"></a>getClientInfo 方法 ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索一个列表，其中包含 JDBC 驱动程序支持的每个客户端信息属性的名称和当前值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>返回值  
 包含驱动程序支持的每个客户端信息属性的名称和当前值的 Properties 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getClientInfo 方法是由 java.sql.Connection 接口中的 getClientInfo 方法指定的。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 不支持任何客户端信息属性。 因此，此方法返回空的 Properties 对象。  
  
 与此类似，应用程序可以使用 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 类中的 [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) 方法来检索驱动程序支持的客户端信息属性列表。 [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) 方法返回空结果集。  
  
## <a name="see-also"></a>另请参阅  
 [getClientInfo 方法 &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection 成员](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 类](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
