---
title: 连接和检索数据
description: 了解如何使用 Microsoft JDBC Driver for SQL Server 和这些代码示例来连接到 SQL 数据库并检索数据。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92565d42605b67f61d3ab5e3842e3fb9f110b626
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922883"
---
# <a name="connecting-and-retrieving-data"></a>连接和检索数据

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

使用 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 时，与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库建立连接的方法主要有两种。 一种方法是在连接 URL 中设置连接属性，然后调用 DriverManager 类的 getConnection 方法来返回 [SQLServerConnection](reference/sqlserverconnection-class.md) 对象。

> [!NOTE]
> 有关 JDBC 驱动程序支持的连接属性的列表，请参阅[设置连接属性](setting-the-connection-properties.md)。

第二种方法涉及到使用 [SQLServerDataSource](reference/sqlserverdatasource-class.md) 类的 setter 方法设置连接属性，然后调用 [getConnection](reference/getconnection-method-sqlserverdatasource.md) 方法来返回 SQLServerConnection 对象。

此部分中的主题介绍了各种用于连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的方法，以及各种用于检索数据的技术。

## <a name="in-this-section"></a>在本节中

| 主题                                             | 说明                                                                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [连接 URL 示例](connection-url-sample.md) | 介绍了如何先使用连接 URL 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，再使用 SQL 语句来检索数据。 |
| [数据源示例](data-source-sample.md)       | 说明如何先使用数据源来连接 SQL Server，然后再使用存储过程来检索数据。                                                 |

## <a name="see-also"></a>另请参阅

[示例 JDBC 驱动程序应用程序](sample-jdbc-driver-applications.md)
