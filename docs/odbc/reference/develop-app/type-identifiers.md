---
description: 类型标识符
title: 类型标识符 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ed41716cd351631578d01027663aa9e0f028c7d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487440"
---
# <a name="type-identifiers"></a>类型标识符
为了描述 SQL 和 C 数据类型，ODBC 定义了两个 *类型标识符*集。 类型标识符描述 SQL 列或 C 缓冲区的类型。 它是 **#define** 值，通常作为函数参数传递，或在元数据中返回。  
  
 例如，以下对 **SQLBindParameter** 的调用将类型 SQL_DATE_STRUCT 的变量绑定到 SQL 语句中的 DATE 参数。 C 类型标识符 SQL_C_TYPE_DATE 指定 *日期* 变量的类型，SQL 类型标识符 SQL_TYPE_DATE 指定动态参数的类型。  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
