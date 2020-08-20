---
description: SQLBindParameter（游标库）
title: SQLBindParameter (游标库) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96fb4f3390b062a4b86f7a7b7f457c43c476c26c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466069"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter（游标库）
> [!IMPORTANT]  
>  此功能将在 Windows 的将来版本中删除。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 本主题讨论如何在游标库中使用 **SQLBindParameter** 函数。 有关 **SQLBindParameter**的常规信息，请参阅 [SQLBindParameter 函数](../../../odbc/reference/syntax/sqlbindparameter-function.md)。  
  
 应用程序可以调用 **SQLBindParameter** 来重新绑定参数，只要绑定列的 C 数据类型、列大小和小数位数保持不变。  
  
 游标库支持将 SQL_ATTR_ROW_BIND_OFFSET_PTR 语句特性设置为使用绑定偏移量。 无需调用 (**SQLBindParameter** 即可进行此重新绑定。 )   
  
 游标库支持绑定执行时数据参数。
