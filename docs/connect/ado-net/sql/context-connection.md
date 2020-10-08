---
title: 上下文连接
description: 介绍了上下文连接。
ms.date: 08/15/2019
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: b8d98dc60d40d40041375370b04c698768d0f324
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725661"
---
# <a name="the-context-connection"></a>上下文连接

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

内部数据访问问题是一种非常常见的情况。 即您希望访问正在执行公共语言运行时 (CLR) 存储过程或函数的相同服务器。 一种选择是使用 <xref:Microsoft.Data.SqlClient.SqlConnection> 创建连接，指定指向本地服务器的连接字符串，然后打开该连接。 这要求指定登录凭据。 连接与存储过程或函数处于不同的数据库会话中，它可能具有不同的 `SET` 选项，位于单独的事务中，找不到临时表等等。 如果托管存储过程或函数代码正在 SQL Server 进程中执行，则是因为有人连接到了该服务器并执行了 SQL 语句调用它。 您可能希望在该连接上下文中执行存储过程或函数，以及其事务、`SET` 选项等。 这称为上下文连接。  
  
利用上下文连接，您可以在首先调用代码的同一上下文中执行 Transact-SQL 语句。 如需了解更多详情，请参阅 SQL Server 联机丛书中的[上下文连接](/previous-versions/sql/sql-server-2008/ms131053(v=sql.100))。