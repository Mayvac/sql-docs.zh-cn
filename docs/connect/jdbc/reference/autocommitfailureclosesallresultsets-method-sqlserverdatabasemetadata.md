---
description: autoCommitFailureClosesAllResultSets 方法 (SQLServerDatabaseMetaData)
title: JDBC 驱动程序是否关闭打开的结果集 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e0fb75b6124947cd32656d081d0c3a29c327b63b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438209"
---
# <a name="autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata"></a>autoCommitFailureClosesAllResultSets 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  启用自动提交并引发异常时，指示 JDBC 驱动程序是否关闭所有打开的结果集，包括可保持的结果集。  
  
## <a name="syntax"></a>语法  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## <a name="return-value"></a>返回值  
 启用自动提交并引发异常时，如果关闭所有打开的结果集，包括可保留的结果集，则为 true****。 否则为 **false**。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 autoCommitFailureClosesAllResultSets 方法是由 java.sql.DatabaseMetaData 接口中的 autoCommitFailureClosesAllResultSets 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
