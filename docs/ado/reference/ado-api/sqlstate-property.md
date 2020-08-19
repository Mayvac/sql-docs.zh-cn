---
description: SQLState 属性
title: SQLState 属性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords:
- SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4216b6ce215db761c95bb830f7fdf26a05174b40
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442009"
---
# <a name="sqlstate-property"></a>SQLState 属性
指示给定 [错误](../../../ado/reference/ado-api/error-object.md) 对象的 SQL 状态。  
  
## <a name="return-value"></a>返回值  
 返回一个包含五个字符的字符串值，该 **字符串** 值遵循 ANSI SQL 标准并指示错误代码。  
  
## <a name="remarks"></a>备注  
 使用 **SQLState** 属性可读取在处理 SQL 语句期间出错时提供程序返回的五个字符的错误代码。 例如，将 Microsoft OLE DB Provider for ODBC 与 Microsoft SQL Server 数据库一起使用时，SQL 状态错误代码是从 ODBC 开始，基于特定于 ODBC 的错误或源自 Microsoft SQL Server 的错误，然后映射到 ODBC 错误。 ANSI SQL 标准中记录了这些错误代码，但不同的数据源可能以不同的方式实现这些错误代码。  
  
## <a name="applies-to"></a>适用于  
 [Error 对象](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>另请参阅  
 [Description、HelpContext、"帮助"、"NativeError"、"Number"、"Source" 和 "SQLState Properties" 示例 (VB) ](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、"帮助"、"NativeError"、"Number"、"Source" 和 "SQLState Properties" 示例 (VC + +) ](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
