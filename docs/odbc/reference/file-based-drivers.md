---
description: 基于文件的驱动程序
title: 基于文件的驱动程序 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 770e8560c540e8423aebf0a79c0e8ee5c124c8e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429079"
---
# <a name="file-based-drivers"></a>基于文件的驱动程序
基于文件的驱动程序与数据源（如 dBASE）一起使用，这些数据源不提供独立的数据库引擎供驱动程序使用。 这些驱动程序直接访问物理数据，必须实现数据库引擎才能处理 SQL 语句。 作为标准做法，基于文件的驱动程序中的数据库引擎实现由最低 SQL 一致性级别定义的 ODBC SQL 子集;有关此一致性级别中的 SQL 语句的列表，请参阅 [附录 C： Sql 语法](../../odbc/reference/appendixes/appendix-c-sql-grammar.md)。  
  
 在比较基于文件的驱动程序和基于 DBMS 的驱动程序时，基于文件的驱动程序更难写入，这是因为数据库引擎组件、配置不太复杂，因为没有网络片段，而且功能更强大，因为很少有用户编写的数据库引擎的功能与数据库公司生成的功能功能强大。  
  
 下图显示了基于文件的驱动程序的两种不同配置，其中的数据存放在一个本地，另一个位于网络文件服务器上。  
  
 ![基于文件&#45;的驱动程序的两种配置](../../odbc/reference/media/pr06.gif "pr06")
