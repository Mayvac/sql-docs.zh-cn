---
description: 目录和架构使用情况
title: 目录和架构使用情况 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2506810c477e9d75e1d3b38f38185d22edf9d010
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494687"
---
# <a name="catalog-and-schema-usage"></a>目录和架构使用情况
数据源不一定支持在所有 SQL 语句中作为对象名称标识符的目录和架构名称。 数据源可能支持以下一个或多个 SQL 语句类中的目录和架构名称：数据操作语言 (DML) 语句、过程调用、表定义语句、索引定义语句和特权定义语句。 若要确定可在其中使用目录和架构名称的 SQL 语句的类，应用程序需要使用 SQL_CATALOG_USAGE 和 SQL_SCHEMA_USAGE 选项调用 **SQLGetInfo** 。
