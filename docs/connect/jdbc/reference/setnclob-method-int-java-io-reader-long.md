---
description: setNClob 方法 (int, java.io.Reader, long)
title: setNClob 方法 (int, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 11071f8f-0e9b-45f0-b600-aaef7e2815d8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8c2a96bd9d2d114ce148e51f0728e9409cb4915
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431609"
---
# <a name="setnclob-method-int-javaioreader-long"></a>setNClob 方法 (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为具有指定字符数长度的指定 Reader 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader,  
                    long length)  
```  
  
#### <a name="parameters"></a>参数  
 parameterIndex**  
  
 指示参数索引的 int****。  
  
 reader  
  
 指示参数值的 Reader 对象。  
  
 *length*  
  
 指示参数值中字符数的 long****。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 setNClob 方法是由 java.sql.PreparedStatement 接口中的 setNClob 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [setNClob 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
