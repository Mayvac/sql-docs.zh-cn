---
description: 设置描述符字段
title: 设置描述符字段 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6625db69709098f3a3db1a1d40f9ab583eee4030
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476429"
---
# <a name="setting-descriptor-fields"></a>设置描述符字段
若要修改描述符的字段，应用程序可以调用 **SQLSetDescField**。 某些字段是只读的，不能进行设置。  (参阅 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) 函数说明。 )   
  
 描述符记录字段设置为 (*RecNumber*) 为1或更高的记录号，而描述符标头字段的记录号为0。 如果记录号为0，则还会根据书签在列0中包含的约定来设置书签字段。 这可能会使书签字段包含在描述符标头中，但这种情况并非如此。 书签字段不同于标题字段。  
  
 当单独设置字段时，应用程序应遵循 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)中定义的顺序。 设置某些字段将导致驱动程序设置其他字段。 这可确保在应用程序指定了数据类型后，描述符始终可以使用。 当应用程序设置 "SQL_DESC_TYPE" 字段时，驱动程序将检查指定类型的其他字段是否有效和一致。  
  
 如果要设置描述符字段的函数调用失败，则在函数调用失败后，描述符字段的内容将不确定。
