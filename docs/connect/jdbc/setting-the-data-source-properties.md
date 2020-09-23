---
title: 设置数据源属性
description: 了解 JDBC 中的数据源，以及如何设置它们的属性来使用 Java 配置数据库访问。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a2a9964b592fc1bcb8c41cf0c5b8de67a2d5a18
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411333"
---
# <a name="setting-the-data-source-properties"></a>设置数据源属性

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

数据源是在 Java Platform, Enterprise Edition (Java EE) 环境中创建 JDBC 连接的首选机制。 数据源可提供连接、池化连接和分布式连接，并且无需将连接属性硬编码到 Java 代码中。 所有 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 数据源都可以分别使用相应的 setter 和 getter 方法来设置或获取任何属性的值。

通过使用 Java EE 产品（例如应用程序服务器和 servlet/JSP 引擎），通常可配置数据库访问的数据源。 配置允许通过“属性=值”对来输入属性时，可以指定[设置连接属性](../../connect/jdbc/setting-the-connection-properties.md)主题中列出的任何属性。

有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据源的详细信息，请参阅 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) 类。 有关如何使用 SQLServerDataSource 类来建立到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的连接的示例，请参阅[数据源示例](../../connect/jdbc/data-source-sample.md)。

## <a name="see-also"></a>另请参阅

[通过 JDBC 驱动程序连接到 SQL Server](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
