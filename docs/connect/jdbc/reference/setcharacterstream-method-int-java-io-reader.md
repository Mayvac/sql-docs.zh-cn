---
description: setCharacterStream 方法 (int, java.io.Reader)
title: setCharacterStream 方法 (int, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cd2b09810329bc79f74616fc964eb18c2efd803
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432319"
---
# <a name="setcharacterstream-method-int-javaioreader"></a>setCharacterStream 方法 (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为指定的 java.io.Reader 对象。  
  
> [!NOTE]
>  此功能是从 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 2.0 版开始引入的。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>参数  
 parameterIndex**  
  
 指示参数编号的 int****。  
  
 reader  
  
 包含 Unicode 数据的 java.io.Reader 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 setCharacterStream 方法是由 java.sql.PreparedStatement 接口中的 setCharacterStream 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [setCharacterStream 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
