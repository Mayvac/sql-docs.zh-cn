---
title: JDBC 驱动程序对高可用性和灾难恢复的支持
description: 本主题介绍了 Microsoft JDBC Driver for SQL Server 对高可用性、灾难恢复（AlwaysOn 可用性组）的支持。
ms.custom: ''
ms.date: 07/13/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3a79f3f47db8bfa048ecb5b910bcb4946cf7a7c
ms.sourcegitcommit: e08d28530e0ee93c78a4eaaee8800fd687babfcc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301816"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>JDBC 驱动程序对高可用性和灾难恢复的支持

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  本主题介绍 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 对于高可用性和灾难恢复的支持 -- [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]。 有关 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]的详细信息，请参阅 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 联机丛书。  
  
 从 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 4.0 版本开始，可以在连接属性中指定（高可用性、灾难恢复）可用性组 (AG) 的可用性组侦听器。 如果 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 应用程序连接到进行故障转移的 AlwaysOn 数据库，则原始连接断开，且应用程序必须建立新的连接，以便在故障转移后继续运行。 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 中新增了以下[连接属性](setting-the-connection-properties.md)：  
  
- **multiSubnetFailover**  
  
- **applicationIntent**

在连接到可用性组的可用性组侦听程序或故障转移群集实例时可指定 multiSubnetFailover=true。 请注意，默认情况下 multiSubnetFailover  为 false。 使用 applicationIntent  声明应用程序工作负载类型。 有关详细信息，请参阅以下部分。

自 Microsoft JDBC Driver for SQL Server 版本 6.0 起，新增了连接属性 transparentNetworkIPResolution  (TNIR)，用于与 AlwaysOn 可用性组或关联有多个 IP 地址的服务器进行透明连接。 当 transparentNetworkIPResolution  为 true 时，驱动程序将尝试连接到可用的第一个 IP 地址。 如果第一次尝试失败，驱动程序将尝试并行连接到所有 IP 地址，直到超过超时时间，如果其中一次尝试成功，则放弃所有挂起的连接尝试。

请注意：

- transparentNetworkIPResolution 默认情况下为 true
- 如果 multiSubnetFailover 为 true，则忽略 transparentNetworkIPResolution  
- 如果使用数据库镜像，则忽略 transparentNetworkIPResolution  
- 如果 IP 地址数超过 64 个，则忽略 transparentNetworkIPResolution  
- 如果 transparentNetworkIPResolution 为 true，首次连接尝试使用 500 毫秒作为超时值。 其余的连接尝试将遵循与 multiSubnetFailover 功能相同的逻辑。  

> [!NOTE]
> 如果使用的是 Microsoft JDBC Driver 4.2 for SQL Server（或更低版本），并且 multiSubnetFailover  为 false，则 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 将尝试连接到第一个 IP 地址。 如果 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 无法建立与第一个 IP 地址的连接，则连接将失败。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 将不会尝试连接到与此服务器关联的任何后续 IP 地址。

> [!NOTE]
> 增大连接超时值和实现连接重试逻辑将增加应用程序连接到可用性组的概率。 此外，由于可用性组进行故障转移而可能使连接失败，您应实现连接重试逻辑，重试失败的连接，直至重新连接。  

## <a name="connecting-with-multisubnetfailover"></a>使用 multiSubnetFailover 进行连接  

 在连接到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可用性组或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 故障转移群集实例的可用性组侦听程序时，应始终指定 multiSubnetFailover=true  。 multiSubnetFailover 可加快 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中所有可用性组和故障转移群集实例的故障转移速度，并且将显著缩短单子网和多子网 AlwaysOn 拓扑的故障转移时间  。 在多子网故障转移过程中，客户端将尝试并行进行连接。 子网故障转移期间，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 将积极地重试 TCP 连接。  
  
 multiSubnetFailover 连接属性指示应用程序正部署在某一可用性组或故障转移群集实例中，并且 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 将尝试通过试图连接到所有 IP 地址来连接到主 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的数据库  。 如果对连接指定的是 MultiSubnetFailover=true  ，客户端重试 TCP 连接尝试的速度快于操作系统的默认 TCP 重传间隔。 这种行为可以在 AlwaysOn 可用性组或 AlwaysOn 故障转移群集实例进行故障转移后更快地进行重新连接，并同时适用于单子网和多子网可用性组和故障转移群集实例。  
  
 有关 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 中的连接字符串关键字的详细信息，请参阅[设置连接属性](setting-the-connection-properties.md)。  
  
 如果在连接到非可用性组侦听程序或故障转移群集实例时指定 multiSubnetFailover=true，则可能会对性能造成负面影响，因此不支持这样做  。  
  
 如果未安装安全管理器，默认情况下，Java 虚拟机将缓存虚拟 IP 地址 (VIP) 一段时间（由您的 JDK 实现和 Java 属性 networkaddress.cache.ttl 和 networkaddress.cache.negative.ttl 定义）。 如果已安装 JDK 安全管理器，默认情况下，Java 虚拟机将缓存 VIP 且不会刷新缓存。 您应将 Java 虚拟机缓存的“生存时间”(networkaddress.cache.ttl) 设置为“一天”。 如果未将默认值更改为“一天（左右）”，则添加或更新 VIP 后，不会清除 Java 虚拟机缓存中的旧值。 有关 networkaddress.cache.ttl 和 networkaddress.cache.negative.ttl 的详细信息，请参阅 [https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html)。  
  
 使用以下准则可以连接到可用性组或故障转移群集实例中的服务器：  
  
- 如果在与 multiSubnetFailover  连接属性相同的连接字符串中使用 instanceName  连接属性，驱动程序将生成一个错误。 此错误反映了在可用性组中没有使用 SQL Browser 这一事实。 但如果另外指定了 portNumber  连接属性，驱动程序将忽略 instanceName  而使用 portNumber  。  
  
- 连接到单子网或多子网时使用 multiSubnetFailover 连接属性，这二者的性能都会得到改进  。  
  
- 若要连接到某一可用性组，请在您的连接字符串中将该可用性组的可用性组侦听器指定为服务器。 例如，jdbc:sqlserver://VNN1。  
  
- 连接到配置有超过 64 个 IP 地址的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例将导致连接失败。  
  
- 基于以下身份验证类型，使用 multiSubnetFailover  连接属性的应用程序的行为将不会受到影响：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证、Kerberos 身份验证或 Windows 身份验证。  
  
- 增加 loginTimeout 的值，以延长故障转移时间并减少应用程序连接重试次数  。  
  
- 不支持分布式事务。  
  
如果只读路由不起作用，则连接到可用性组中的辅助副本位置在以下情况下将失败：  
  
1. 如果未将辅助副本位置配置为接受连接。  
  
2. 如果应用程序使用 applicationIntent=ReadWrite（将在下文中介绍）并且次要副本位置被配置为只读访问  。  
  
如果将主副本配置为拒绝只读工作负荷且连接字符串包含 **ApplicationIntent=ReadOnly**，连接将失败。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>从数据库镜像升级到使用多子网群集  

如果将当前使用数据库镜像的 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 应用程序升级到多子网方案，应删除 failoverPartner  连接属性，并将它替换为已设置为“true”  的 multiSubnetFailover  ，同时将连接字符串中的服务器名称替换为可用性组侦听程序。 如果连接字符串使用 failoverPartner 和 multiSubnetFailover=true，驱动程序将生成一个错误   。 但是，如果连接字符串使用 failoverPartner 和 multiSubnetFailover=false（或 ApplicationIntent=ReadWrite），则此应用程序将使用数据库镜像    。  
  
如果数据库镜像在 AG 中的主数据库上使用，并且如果 multiSubnetFailover=true 用于连接到主数据库（而非可用性组侦听程序）的连接字符串中，驱动程序则将返回一个错误  。  

[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]

## <a name="connection-pooling"></a>连接池

将 Microsoft JDBC Driver for SQL Server 与连接池库结合使用时，应考虑以下几点：

- 如果你已配置只读路由，并且拥有一个想要在其中分配负载的只读服务器池，则连接池将减少新连接在目标服务器上分配的机会数。
- 若要避免池中任何单个服务器上的负载较高，请选择可促进在池中均匀分布连接的池选项。
- 确保连接池已配置了一个连接生存期。 如果在建立只读连接时一个只读副本不可用，该配置应确保连接最终被关闭，并且在只读副本再次可用时重新与它建立连接。

## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>支持 multiSubnetFailover 和 applicationIntent 的新方法  

使用以下方法，可以编程方式访问 multiSubnetFailover  、applicationIntent  和 transparentNetworkIPResolution  连接字符串关键字：  
  
- [SQLServerDataSource.getApplicationIntent](reference/getapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setApplicationIntent](reference/setapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.getMultiSubnetFailover](reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setMultiSubnetFailover](reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDriver.getPropertyInfo](reference/getpropertyinfo-method-sqlserverdriver.md)  

- SQLServerDataSource.setTransparentNetworkIPResolution

- SQLServerDataSource.getTransparentNetworkIPResolution
  
另外，getMultiSubnetFailover  、setMultiSubnetFailover  、getApplicationIntent  、setApplicationIntent  、getTransparentNetworkIPResolution  和 setTransparentNetworkIPResolution  方法也添加到 [SQLServerDataSource 类](reference/sqlserverdatasource-class.md)、[SQLServerConnectionPoolDataSource 类](reference/sqlserverconnectionpooldatasource-class.md)和 [SQLServerXADataSource 类](reference/sqlserverxadatasource-class.md)中。  
  
## <a name="tlsssl-certificate-validation"></a>TLS/SSL 证书验证  

可用性组包含多个物理服务器。 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 添加了对 TLS/SSL 证书中“使用者可选名称 (SAN)”的支持，因此可以将多个主机与统一证书关联  。 有关 TLS 的详细信息，请参阅[了解加密支持](understanding-ssl-support.md)。  
  
## <a name="see-also"></a>另请参阅  

[通过 JDBC 驱动程序连接到 SQL Server](connecting-to-sql-server-with-the-jdbc-driver.md)  
[设置连接属性](setting-the-connection-properties.md)  
