---
description: 参数值检查
title: 参数值检查 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5dac29eea6c9a2b5f178aa233520674ea466cf48
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465949"
---
# <a name="argument-value-checks"></a>参数值检查
驱动程序管理器将检查以下类型的参数。 除非另有说明，否则，驱动程序管理器将为参数值中的错误返回 SQL_ERROR。  
  
-   环境、连接和语句句柄通常不能为 null 指针。 驱动程序管理器在找到 null 句柄时返回 SQL_INVALID_HANDLE。  
  
-   所需的指针自变量（例如**SQLAllocHandle**中的*OutputHandlePtr*和**SQLSetCursorName**中的*CursorName* ）不能为 null 指针。  
  
-   不支持特定于驱动程序的值的选项标志必须是合法值。 例如， **SQLSetPos**中的*操作*必须 SQL_POSITION、SQL_REFRESH、SQL_UPDATE、SQL_DELETE 或 SQL_ADD。  
  
-   驱动程序支持的 ODBC 版本中必须支持选项标志。 例如，在调用 ODBC 2.0 驱动程序时， **SQLGetInfo**中的*InfoType*不能 (SQL_ASYNC_MODE) ODBC 3.0 中引入的。  
  
-   根据函数的不同，列和参数号必须大于0或大于或等于0。 驱动程序必须根据当前结果集或 SQL 语句来检查这些参数值的上限。  
  
-   长度/指示器参数和数据缓冲区长度参数必须包含相应的值。 例如，在**SQLColumns** (*NameLength3*) 中指定表名称长度的参数必须 SQL_NTS 或大于0的值;**SQLDescribeCol**中的*BufferLength*必须大于或等于0。 驱动程序还可能需要检查这些参数。 例如，它可能会检查 *NameLength3* 是否小于或等于数据源中的表名的最大长度。
