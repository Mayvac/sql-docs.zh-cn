---
description: 级别 2 接口一致性
title: 2级接口一致性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31b7148b05d3870a7f23a51167fffeb1860c26d8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476559"
---
# <a name="level-2-interface-conformance"></a>级别 2 接口一致性
2级接口一致性级别包括第1级接口一致性级别功能以及以下功能：  
  
|功能编号|说明|  
|-|-|  
|201|使用数据库表和视图的由三部分构成的名称。  (有关详细信息，请参阅 [第1级接口一致性](../../../odbc/reference/develop-app/level-1-interface-conformance.md)中的两部分命名支持功能101。 ) |  
|202|通过调用 **SQLDescribeParam**描述动态参数。|  
|203|不仅可以使用输入参数，还可以使用输出和输入/输出参数以及存储过程的结果值。|  
|204|通过在列号0上调用 **SQLDescribeCol** 和 **SQLColAttribute** ，使用书签，包括检索书签;基于书签提取，方法是调用 **SQLFetchScroll** ，并将 *FetchOrientation* 参数设置为 SQL_FETCH_BOOKMARK;通过调用 **SQLBulkOperations** ，并将 *操作* 参数设置为 SQL_UPDATE_BY_BOOKMARK、SQL_DELETE_BY_BOOKMARK 或 SQL_FETCH_BY_BOOKMARK，使用书签操作来更新、删除和提取。|  
|205|通过调用 **SQLColumnPrivileges**、 **SQLForeignKeys**和 **SQLTablePrivileges**检索有关数据字典的高级信息。|  
|206|使用 ODBC 函数而不是 SQL 语句来执行其他数据库操作，方法是调用带有 SQL_ADD 的 **SQLBulkOperations** 或使用 SQL_DELETE 或 SQL_UPDATE 的 **SQLSetPos** 。  (支持对使用*LockType*参数设置为 SQL_LOCK_EXCLUSIVE 或 SQL_LOCK_UNLOCK 的**SQLSetPos**的调用，但这是一项可选功能。 ) |  
|207|为指定的单个语句启用 ODBC 函数的异步执行。|  
|208|通过调用 **SQLSpecialColumns**获取表的 SQL_ROWVER 行标识列。  (有关详细信息，请参阅*IdentifierType*参数设置为的对**SQLSpecialColumns**的支持与[核心接口一致性](../../../odbc/reference/develop-app/core-interface-conformance.md)中的功能 20 SQL_BEST_ROWID。 ) |  
|209|将 SQL_ATTR_CONCURRENCY 语句特性设置为至少一个除 SQL_CONCUR_READ_ONLY 之外的值。|  
|210|SQL_ATTR_LOGIN_TIMEOUT 和 SQL_ATTR_QUERY_TIMEOUT)  (的登录请求和 SQL 查询的超时时间。|  
|211|更改默认隔离级别的功能;能够执行具有 "可序列化" 隔离级别的事务。|
