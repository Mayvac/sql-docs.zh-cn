---
description: setCharacterStream 方法 (java.lang.String, java.io.Reader)
title: setCharacterStream 方法 (java.lang.String, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 43acac5b-5a8a-4685-bee6-7194d2d03a52
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0d7f8ad0d6ef17da0539983b2da2f67994ee2dca
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432249"
---
# <a name="setcharacterstream-method-javalangstring-javaioreader"></a>setCharacterStream 方法 (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为指定的 Reader 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setCharacterStream(java.lang.String parameterName,  
                                             java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>参数  
 parameterName  
  
 包含参数名称的字符串****。  
  
 reader  
  
 包含 Unicode 数据的 Reader 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 setCharacterStream 方法是由 java.sql.CallableStatement 接口中的 setCharacterStream 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [setCharacterStream 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
