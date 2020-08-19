---
description: 连接属性
title: 连接属性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a7db2fb6361f114f4864436116f5b0f2f5651e79
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424799"
---
# <a name="connection-attributes"></a>连接属性
连接属性是连接的特征。 例如，因为事务发生在连接级别，所以事务隔离级别就是一个连接属性。 同样，在超时前尝试连接时的登录超时值或等待的秒数是连接属性。  
  
 连接属性通过 **SQLSetConnectAttr** 设置，其当前设置通过 **SQLGetConnectAttr**检索。 如果在加载驱动程序之前调用 **SQLSetConnectAttr** ，则驱动程序管理器会将属性存储在其连接结构中，并在该驱动程序中将它们设置为连接过程的一部分。 不要求应用程序设置任何连接属性;所有连接属性都具有默认值，其中一些属性是特定于驱动程序的。  
  
 连接属性可以在连接之前或之后设置，也可以根据属性和驱动程序设置。 登录超时 (SQL_ATTR_LOGIN_TIMEOUT) 适用于连接过程，并且仅在连接前设置时有效。 指定是否使用 ODBC 游标库 (SQL_ATTR_ODBC_CURSORS) 和网络数据包大小 (SQL_ATTR_PACKET_SIZE) 的属性必须在连接之前设置，因为 ODBC 游标库驻留在驱动程序管理器和驱动程序之间，因此必须在驱动程序之前加载。  
  
 用于指定数据源是只读还是读写 (SQL_ATTR_ACCESS_MODE) 的属性，并且可以在连接之前或之后设置当前目录 (SQL_ATTR_CURRENT_CATALOG) ，具体取决于驱动程序。 但是，在连接之前，可互操作的应用程序将其设置，因为某些驱动程序不支持在连接后更改它们。  
  
 在建立连接之前，某些连接属性具有默认值，而其他属性则不是。 它们 SQL_ATTR_ACCESS_MODE、SQL_ATTR_AUTOCOMMIT、SQL_ATTR_LOGIN_TIMEOUT、SQL_ATTR_ODBC_CURSORS、SQL_ATTR_TRACE 和 SQL_ATTR_TRACEFILE。  
  
 连接后必须设置 SQL_ATTR_TRANSLATE_DLL 和 SQL_ATTR_TRANSLATE_OPTION)  (转换连接属性。  
  
 所有其他连接属性可随时设置。 有关详细信息，请参阅 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) 函数说明。 无法通过调用 **SQLSetEnvAttr**在环境级别设置 (连接属性 ) 
