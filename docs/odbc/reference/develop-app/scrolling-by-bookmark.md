---
description: 按书签滚动
title: 按书签滚动 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 52ef0813f3f9fd3f2d139a2549000c629943109e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476469"
---
# <a name="scrolling-by-bookmark"></a>按书签滚动
使用 **SQLFetchScroll**提取行时，应用程序可以使用书签作为选择起始行的基础。 这是一种绝对寻址的格式，因为它不依赖于当前游标位置。 若要滚动到带有书签的行，应用程序将调用 **SQLFetchScroll** ，并将 *FetchOrientation* SQL_FETCH_BOOKMARK。 此操作使用 SQL_ATTR_FETCH_BOOKMARK_PTR 语句特性指向的书签。 它将返回以该书签标识的行开始的行集。 应用程序可以在调用**SQLFetchScroll**的*FetchOffset*参数中指定此操作的偏移量。 指定偏移量后，通过将 *FetchOffset* 自变量中的数字添加到书签所标识的行号来确定返回的行集的第一行。 与 ODBC 2 一起使用时，不支持使用 *FetchOffset* 参数。*x* 驱动程序;当应用程序在 ODBC 2 中调用 **SQLFetchScroll** 时。*x* 驱动程序， *FetchOrientation* 设置为 SQL_FETCH_BOOKMARK， *FetchOffset* 参数必须设置为0。
