---
description: 显式分配的描述符
title: 显式分配的描述符 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7215d17a7156419f08bbd73528c468d7b6355b94
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461479"
---
# <a name="explicitly-allocated-descriptors"></a>显式分配的描述符
应用程序可以在连接到数据库时，在该连接上显式分配应用程序描述符。 通过使用 **SQLSetStmtAttr**将该描述符句柄指定为语句句柄的属性，应用程序将指示该驱动程序使用该描述符来替换相应的隐式分配的应用程序描述符。 应用程序无法指定替代实现描述符。  
  
 应用程序可将显式分配的描述符与多个语句相关联。 仅当应用程序实际连接到数据库时，描述符才能是显式分配的描述符。 应用程序可以显式释放此类描述符，也可以通过释放其连接来隐式释放它。
