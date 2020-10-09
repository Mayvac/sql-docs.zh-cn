---
title: SQL Server 内存中 OLTP 内部组件
description: 了解 SQL Server 内存中 OLTP 技术的实现，该技术将表声明为内存优化来实现内存中 OLTP 功能。
ms.custom: seo-dt-2019
ms.date: 09/14/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b14da361-a6b8-4d85-b196-7f2f13650f44
author: jodebrui
ms.author: jodebrui
ms.openlocfilehash: 4f9b1e77d082ad5e42a9818272fc1c4a48b44968
ms.sourcegitcommit: d56a834269132a83e5fe0a05b033936776cda8bb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91529378"
---
# <a name="sql-server-in-memory-oltp-internals-for-sql-server-2016"></a>SQL Server 2016 的 SQL Server 内存中 OLTP 内部组件
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

**摘要：** SQL Server 2014 中引入了内存中 OLTP，通常以其代号“Hekaton”相称。
采用这种功能强大的技术，可以充分利用大量的内存以及几十个内核，将 OLTP 操作的性能提高 30 至 40 倍！ SQL Server 2016 消除了 SQL Server 2014 中发现的许多限制，继续投资于内存中 OLTP，同时增强内部处理算法，以便内存中 OLTP 可以实现更卓越的改进。 本文介绍了自 SQL Server 2016 RTM 起 SQL Server 2016 内存中 OLTP 技术的实施。 使用内存中 OLTP，可将表声明为“内存优化”，以启用内存中 OLTP 的功能。 内存优化表是完全事务性的，并可以通过 Transact-SQL 访问。 Transact-SQL 存储过程、触发器和标量 UDF 可编译为机器代码，以进一步提升内存优化表的性能。 该引擎专门针对高并发操作，不会发生阻塞。    
  
**作者：** Kalen Delaney  
  
**技术评审员：** Sunil Agarwal 和 Jos de Bruijn  
  
**发布时间：** 2016 年 6 月  
  
**适用于：** SQL Server 2016  
  
要查看文档，请下载 [SQL Server 2016 的 SQL Server 内存中 OLTP 内部组件](https://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf)文档。   
