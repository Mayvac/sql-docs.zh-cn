---
title: 默认 SQL Server 网络协议配置 | Microsoft Docs
description: 查看影响 SQL Server 安装期间是打开还是关闭网络协议的因素。 了解如何在安装后配置协议。
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- protocols [SQL Server], default settings
- default protocols, after install
ms.assetid: 635ea361-a797-4971-bd05-e3415862bc5c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9197a6838b62c970f9c8b9fad624a7229766628c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772572"
---
# <a name="default-sql-server-network-protocol-configuration"></a>默认 SQL Server 网络协议配置
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
为了增强安全性， [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 将对某些新的安装禁用网络连接。 如果你使用的是 Enterprise Edition、Standard Edition、Evaluation Edition 或 Workgroup Edition，或者存在以前安装的 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，则不禁用 TCP/IP 网络连接。 对于所有的安装，将启用 shared memory 协议以允许本地到服务器的连接。 根据安装情况和安装选项， [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 浏览器服务可能会停止。

安装之后，使用 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 配置管理器的“ [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 网络配置”节点来配置网络协议。 使用 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 配置管理器的“ [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 服务”节点以将 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 浏览器服务配置为自动启动。 有关详细信息，请参阅 [启用或禁用服务器网络协议](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)。


## <a name="default-configuration"></a>默认配置

下表介绍了安装之后的配置。

|版本 | 存在新安装与以前的安装 | 共享内存 | TCP/IP | Named pipes|
| -------- | -- | -- | -- | --  |  
|Enterprise | 新安装 | 已启用 | 已启用 | 对于网络连接为禁用。|
|Standard | 新安装 | 已启用 | 已启用 | 对于网络连接为禁用。|
|Web | 新安装 | 已启用 | 已启用 | 对于网络连接为禁用。|
|开发人员 | 新安装 | 已启用 | 已禁用 | 对于网络连接为禁用。|
|计算 | 新安装 | 已启用 | 已启用 | 对于网络连接为禁用。|
|SQL Server Express | 新安装 | 已启用 | 已禁用 | 对于网络连接为禁用。|
|所有版本 | 存在以前的安装但未升级。 | 与全新安装相同 | 与全新安装相同 | 与全新安装相同|
|所有版本 | 升级 | 已启用 | 保留以前安装中的设置。 | 保留以前安装中的设置。|


>[!NOTE]
> 如果该实例正在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 故障转移群集上运行，它将在安装 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 的过程中监听为 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 选择的每个 IP 地址的那些端口。
 
>[!NOTE]
> 使用命令提示符安装 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 时，可以使用 `TCPENABLED` 和 `NPENABLED` 参数指定要启用的协议。 有关详细信息，请参阅 [从命令提示符安装 SQL Server](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)。

## <a name="creating-a-connection-string"></a>创建连接字符串

有关连接字符串的示例，请参阅以下主题：
* [使用 Shared Memory 协议创建有效的连接字符串](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)
* [使用 TCP IP 创建有效的连接字符串](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)



## <a name="ssnoversion_md-browser-settings"></a>[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 浏览器设置

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Browser 服务可以配置为在安装过程中自动启动。 默认设置是在下列条件下自动启动：

* 升级安装时。
* 当与其他 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 实例并行安装时。
* 在群集上安装时。
* 安装包括所有 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Express 实例的数据库引擎的命名实例时。
* 安装 Analysis Services 的命名实例时。

## <a name="see-also"></a>另请参阅

[安装 SQL Server 2016 的硬件和软件要求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)

[外围应用配置器](../../relational-databases/security/surface-area-configuration.md)  



