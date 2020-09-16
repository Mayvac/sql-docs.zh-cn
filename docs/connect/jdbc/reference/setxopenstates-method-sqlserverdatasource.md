---
description: setXopenStates 方法 (SQLServerDataSource)
title: setXopenStates 方法 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 345f243f6fb712208df336207ee408cd7596b296
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450607"
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>setXopenStates 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  设置指示是否启用了将 SQL 状态转换为 XOPEN 兼容状态的**** Boolean 值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>参数  
 *xopenStates*  
  
 如果启用了将 SQL 状态转换为 XOPEN 兼容状态，则为 **** true。 否则为 **false**。  
  
## <a name="remarks"></a>备注  
 如果将 xopenStates 属性设置为 true****，则 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 会将 SQL 状态转换为 XOPEN 兼容状态。 默认为 false****，这将导致 JDBC 驱动程序生成 SQL 99 状态代码。 如果未设置 xopenStates，则 [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md) 方法会返回默认值 false****。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
