---
description: setClob 方法 (int, java.io.Reader, long)
title: setClob 方法 (int, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 157882dd-1a96-4501-a895-46e88a49266e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5967971a6e7c5c9de773a93695b60ffcbc3d240
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432169"
---
# <a name="setclob-method-int-javaioreader-long"></a>setClob 方法 (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为具有给定字符数的指定 Reader 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.io.Reader reader,  
                          long length)  
```  
  
#### <a name="parameters"></a>参数  
 parameterIndex**  
  
 指示参数索引的 int****。  
  
 reader  
  
 Reader 对象。  
  
 *length*  
  
 指示参数值中字符数的 long****。  
  
## <a name="remarks"></a>注解  
 此 setClob 方法是由 java.sql.PreparedStatement 接口中的 setClob 方法指定的。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>另请参阅  
 [setClob 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
