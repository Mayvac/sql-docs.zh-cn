---
description: 数据缓冲区地址
title: 数据缓冲区地址 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 301202933ae9cb0206100b6bbf10dda305495be1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429379"
---
# <a name="data-buffer-address"></a>数据缓冲区地址
应用程序将数据缓冲区的地址作为参数传递给驱动程序，该参数通常名为 *将 valueptr* 或类似名称。 例如，在以下对 **SQLBindCol**的调用中，应用程序指定 *Date* 变量的地址：  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 如在 " [分配和释放缓冲区](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) " 部分中所述，延迟缓冲区的地址必须保持有效，直到缓冲区未绑定。  
  
 除非明确禁止，否则数据缓冲区的地址可以是 null 指针。 对于用于将数据发送到驱动程序的缓冲区，这将导致驱动程序忽略通常包含在缓冲区中的信息。 对于用于从驱动程序检索数据的缓冲区，这将导致驱动程序不返回值。 在这两种情况下，驱动程序将忽略相应的数据缓冲区长度参数。
