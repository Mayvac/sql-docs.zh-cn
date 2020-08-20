---
description: 支持的数据类型（Visual FoxPro ODBC 驱动程序）
title: " (Visual FoxPro ODBC 驱动程序) 支持的数据类型 |Microsoft Docs"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 04f2039d18f134fe2c48397f6c0dc987e97bf47d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471519"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>支持的数据类型（Visual FoxPro ODBC 驱动程序）
驱动程序支持的数据类型列表通过 ODBC API 和 Microsoft Query 提供。  
  
## <a name="data-types-in-c-applications"></a>C 应用程序中的数据类型  
 可以使用 C 或 c + + 应用程序中的 [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) 函数获取 VISUAL FoxPro ODBC 驱动程序支持的数据类型列表。  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>使用 Microsoft Query 的应用程序中的数据类型  
 如果您的应用程序使用 Microsoft Query 在 Visual FoxPro 数据源上创建新表，则 Microsoft Query 将显示 " **新建表定义** " 对话框。 在 " **字段说明**" 下，" **类型** " 框会列出以单个字符表示的 [视觉 FoxPro 字段数据类型](../../odbc/microsoft/visual-foxpro-field-data-types.md)。
