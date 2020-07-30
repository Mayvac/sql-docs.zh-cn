---
title: 将 TCP IP 端口映射到 NUMA 节点 (SQL Server) | Microsoft Docs
description: 了解如何使用 SQL Server 配置管理器将 TCP/IP 端口映射到非一致性内存访问 (NUMA) 节点。 了解如何创建节点标识位图。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 055821c4d005c52ff20b79967fca35ac2994ff9f
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362605"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a>将 TCP IP 端口映射到 NUMA 节点 (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器来将 TCP/IP 端口映射到非一致性内存访问 (NUMA) 节点。 启动时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 会将节点信息写入错误日志中。  
  
 若要确定要使用的节点编号，请参阅错误日志或 **sys.dm_os_schedulers** 视图中的节点信息。 若要将 TCP/IP 地址和端口设置到一个或多个节点，请在端口号后用括号追加一个节点标识位图（关联掩码）。 可以按十进制格式或十六进制格式指定节点。 若要创建位图，请先从右到左且以零开头为节点编号，例如 76543210。 创建节点列表的二进制表示形式，要使用的节点用 1 表示，而不使用的节点用 0 表示。 例如，若要使用 0、2 和 5 NUMA 节点，请指定 00100101。  
  
```text
NUMA node number                            76543210
Mask for 0, 2, and 5 counting from right    00100101
```
  
 将二进制表示形式 (00100101) 转换为十进制 `[37]`或十六进制 `[0x25]`。 若要侦听所有节点，则不提供任何节点标识符。  
  
 如果一个端口映射到多个 NUMA 节点，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以循环的方式将连接分配到各节点，而不会试图平衡节点之间的负载。  
  
> [!NOTE]  
>  若要允许 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听每个 IP 地址的多个 TCP 端口，请参阅 [将数据库引擎配置为侦听多个 TCP 端口](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)。  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> 使用 SQL Server 配置管理器  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a>将 TCP/IP 端口映射到 NUMA 节点  
  
1.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server 网络配置”，然后单击“\<instance name> 的协议” 。  
  
2.  在详细信息窗格中，双击“TCP/IP”。  
  
3.  在 **“IP 地址”** 选项卡（要配置的 IP 地址的相应部分）的 **“TCP 端口”** 框中，在端口号后面的方括号里添加 NUMA 节点标识符。 例如，对于 TCP 端口 1500 和节点 0、2 和 5，使用 **1500[37]** 或 **1500[0x25]** 。  
  
## <a name="see-also"></a>另请参阅  
 [软件 NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
