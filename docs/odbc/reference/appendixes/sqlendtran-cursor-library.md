---
description: SQLEndTran（游标库）
title: SQLEndTran (游标库) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25584f19a885580be24b2681ccd639de285fb4b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466029"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran（游标库）
> [!IMPORTANT]  
>  此功能将在 Windows 的将来版本中删除。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 本主题讨论如何在游标库中使用 **SQLEndTran** 函数。 有关 **SQLEndTran**的常规信息，请参阅 [SQLEndTran 函数](../../../odbc/reference/syntax/sqlendtran-function.md)。  
  
 游标库不支持事务，并将对 **SQLEndTran** 的调用直接传递给驱动程序。 但是，游标库支持使用 SQL_CURSOR_ROLLBACK_BEHAVIOR 和 SQL_CURSOR_COMMIT_BEHAVIOR 信息类型由数据源返回的游标提交和回滚行为：  
  
-   对于跨事务保留游标的数据源，在数据源中回滚的更改不会在游标库的缓存中回滚。 若要使缓存与数据源中的数据匹配，则应用程序必须关闭并重新打开光标。  
  
-   对于在事务边界关闭游标的数据源，游标库关闭游标，并删除连接上的所有语句的缓存。  
  
-   对于删除事务边界预定义语句的数据源，应用程序必须在 reexecuting 之前 reprepare 连接上的所有已准备语句。
