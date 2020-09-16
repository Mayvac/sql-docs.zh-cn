---
description: getFunctions 方法 (SQLServerDatabaseMetaData)
title: getFunctions 方法 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 517cafe5157848948f0a6ffa9005a255510556a7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435939"
---
# <a name="getfunctions-method-sqlserverdatabasemetadata"></a>getFunctions 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索系统函数和用户函数的说明。  
  
## <a name="syntax"></a>语法  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### <a name="parameters"></a>参数  
 *catalog*  
  
 数据库中的目录名称。 如果该名称为空字符串 ""，则结果将包括无目录的函数。 如果此字符串为“null”，目录名称则不可用于搜索  。  
  
 schemaPattern  
  
 架构的名称。 如果该名称为空字符串 ""，则结果将包括无架构的函数。 如果此字符串为“null”，架构名称则不可用于搜索  。  
  
 functionNamePattern  
  
 函数的名称。  
  
## <a name="return-value"></a>返回值  
 一个 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 getFunctions 方法是由 java.sql.DatabaseMetaData 接口中的 getFunctions 方法指定的。  
  
 此方法只返回与指定架构和函数名称匹配的系统函数和用户函数。  
  
> [!IMPORTANT]  
>  返回的结果集可包含调用用户无权执行的函数。  
  
 每个函数说明都包括以下列：  
  
|名称|类型|说明|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**字符串**|函数所在的数据库的名称。|  
|FUNCTION_SCHEM|**字符串**|函数所在的架构的名称。|  
|FUNCTION_NAME|**字符串**|函数的名称。|  
|NUM_INPUT_PARAMS|**int**|保留以供将来使用，当前返回 -1 值。|  
|NUM_OUTPUT_PARAMS|**int**|保留以供将来使用，当前返回 -1 值。|  
|NUM_RESULT_SETS|**int**|保留以供将来使用，当前返回 -1 值。|  
|REMARKS|**字符串**|有关函数的注释。|  
|FUNCTION_TYPE|**short**|函数的类型。 可以为下列值之一：<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 返回的结果集中的所有说明都按 FUNCTION_CAT、FUNCTION_SCHEM、FUNCTION_NAME 和 SPECIFIC_NAME 排序。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
