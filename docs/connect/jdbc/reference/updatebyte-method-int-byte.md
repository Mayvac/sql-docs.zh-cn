---
description: updateByte 方法 (int, byte)
title: updateByte 方法 (int, byte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateByte (int, byte)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e635d789-9218-488e-a213-2e3e09635acc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 00a7eea10e4ded2bcac76b0825f6ba33722d5795
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462241"
---
# <a name="updatebyte-method-int-byte"></a>updateByte 方法 (int, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根据给定的列索引使用 byte **** 值更新指定的列。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void updateByte(int index,  
                       byte x)  
```  
  
#### <a name="parameters"></a>参数  
 *index*  
  
 指示列索引的 int  。  
  
 *x*  
  
 一个 byte 值****。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 updateByte 方法是由 java.sql.ResultSet 接口中的 updateByte 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [updateByte 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)   
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
