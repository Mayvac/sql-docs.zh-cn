---
title: 访问扩展事件日志中的诊断信息
description: 了解如何在服务器上访问与 Microsoft JDBC Driver for SQL Server 中的事件相关的扩展事件。
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a79e9468-2257-4536-91f1-73b008c376c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6d9b75ea8c722ca753e831811226b8128df15266
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725502"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>访问扩展事件日志中的诊断信息
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  在 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 中，更新了跟踪功能（[跟踪驱动程序操作](../../connect/jdbc/tracing-driver-operation.md)），以便更易于将客户端事件与诊断信息关联，如服务器连接环形缓冲区中的连接故障，以及扩展事件日志中的应用程序性能信息。 有关读取扩展事件日志的信息，请参阅[扩展事件](../../relational-databases/extended-events/extended-events.md)。  
  
## <a name="details"></a>详细信息  
 对于连接操作，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 将发送一个客户端连接 ID。 如果连接失败，可以访问连接环形缓冲区（[在 SQL Server 2008 中使用连接环形缓冲区解决连接问题](/archive/blogs/sql_protocols/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer)），查找 ClientConnectionID 字段并获取有关连接失败的诊断信息  。 仅当发生错误时，才在环形缓冲区中记录客户端连接 ID。 （如果在发送预登录数据包之前连接失败，将不会生成客户端连接 ID。）客户端连接 ID 是 16 字节的 GUID。 如果将 client_connection_id 操作添加到扩展事件会话中的事件，则还可以在扩展事件目标输出中找到客户端连接 ID  。 如果需要进一步的客户端驱动程序诊断帮助，可以启用跟踪并重新运行连接命令，查看跟踪中的 ClientConnectionID 字段  。  
  
 可以使用 [ISQLServerConnection 接口](../../connect/jdbc/reference/isqlserverconnection-interface.md)以编程方式获取客户端连接 ID。 该连接 ID 还存在于任何与连接相关的异常中。  
  
 存在连接错误时，服务器的 Built In Diagnostics (BID) 跟踪信息和连接环形缓冲区中的客户端连接 ID 可以帮助将客户端连接与服务器上的连接关联。 有关服务器上的 BID 跟踪的详细信息，请参阅[数据访问跟踪](/previous-versions/sql/sql-server-2008/cc765421(v=sql.100))。 请注意，数据访问跟踪文章还介绍了数据访问跟踪，但并不适用于 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]；若要了解如何使用 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 执行数据访问跟踪，请参阅[跟踪驱动程序操作](../../connect/jdbc/tracing-driver-operation.md)。  
  
 JDBC Driver 还会发送特定于线程的活动 ID。 如果开始会话时启用了 TRACK_CAUSAILITY 选项，则会在扩展的事件会话中捕获活动 ID。 对于与活动连接有关的性能问题，你可以从客户端的跟踪中获取活动 ID（ActivityID 字段），然后在扩展事件输出中找到该活动 ID。 扩展事件中的活动 ID 是一个 16 字节 GUID（与客户端连接 ID 的 GUID 不同），附有一个 4 字节的序列号。 序列号代表线程内某个请求的顺序。 ActivityId 会为 SQL 批处理语句和 RPC 请求发送。 为了能将 ActivityId 发送到服务器，您首先需要在 Logging.Properties 文件中指定以下键值对：  
  
```
com.microsoft.sqlserver.jdbc.traceactivity = on  
```  
  
 `on`（区分大小写）之外的值都将禁止发送 ActivityId。  
  
 有关详细信息，请参阅[跟踪驱动程序操作](../../connect/jdbc/tracing-driver-operation.md)。 跟踪标志与对应的 JDBC 对象记录程序一起使用，以决定是否在 JDBC 驱动程序中跟踪和发送 ActivityId。 除了更新 Logging.Properties 文件以外，还需要在 FINER 或更高级别启用 com.microsoft.sqlserver.jdbc 记录程序。 如果想为特定类发出的请求将 ActivityId 发送到服务器，则需要在 FINER 或 FINEST 级别启用对应的类记录程序。 例如，如果类是 SQLServerStatement，则启用 com.microsoft.sqlserver.jdbc.SQLServerStatement 记录程序。  
  
 以下示例使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 来启动将存储于环形缓冲区中并记录从 RPC 上的客户端发送的活动 ID 和批处理操作的扩展事件会话：  
  
```sql
create event session MySession on server  
add event connectivity_ring_buffer_recorded,  
add event sql_statement_starting (action (client_connection_id)),  
add event sql_statement_completed (action (client_connection_id)),  
add event rpc_starting (action (client_connection_id)),  
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## <a name="see-also"></a>另请参阅

[诊断 JDBC 驱动程序问题](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)