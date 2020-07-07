---
title: 断开与数据源的连接 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6c7c429b230c068cd2d6b134036ffd1e40053f45
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86005869"
---
# <a name="disconnecting-from-a-data-source"></a>与数据源断开连接
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  当应用程序使用完数据源后，它将调用**SQLDisconnect**。 **SQLDisconnect**释放在连接上分配的所有语句，并断开驱动程序与数据源的连接。 断开连接后，应用程序可以调用[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)来释放连接句柄。 在退出之前，应用程序还会调用**SQLFreeHandle**来释放环境句柄。  
  
 断开连接后，应用程序可以重用分配的连接句柄，以连接到其他数据源或重新连接到同一个数据源。 如果决定保持连接，而不是断开连接后重新连接，则要求应用程序编写人员考虑每种选择的相对成本。 连接到数据源并保持连接状态的开销可能相对较大，具体取决于连接介质。 权衡利弊时，应用程序还必须就同一数据源上存在其他操作的可能性以及这些操作的时间安排情况做出假设。 应用程序可能还必须使用多个连接。  
  
## <a name="see-also"></a>另请参阅  
 [与 SQL Server &#40;ODBC&#41;通信](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
