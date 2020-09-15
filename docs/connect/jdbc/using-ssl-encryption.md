---
description: 使用加密
title: 使用加密
ms.custom: Learn how to establish secure communication channels using TLS encryption with your SQL database connections.
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: vanto
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86a36cec5930630c00501796e9c2340106cfa6c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414573"
---
# <a name="using-encryption"></a>使用加密

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

借助传输层安全性 (TLS) 加密，可以通过网络在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例与客户端应用程序之间传输加密数据。  
  
传输层安全性 (TLS) 是一种协议，用于建立安全通信通道，以防止截获通过网络传输的重要信息或敏感信息以及其他 Internet 通信。 TLS 使客户端和服务器可以验证彼此的身份。 在参与方的身份获得验证之后，TLS 在两者之间提供加密连接，以进行安全的消息传输。  
  
[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 提供了一个基础结构，以便根据用户指定的连接属性以及服务器和客户端设置，在特定的连接上启用和禁用加密。 用户可以指定证书存储区位置和密码、要用于验证证书的主机名以及何时对通信通道进行加密。  
  
启用 TLS 加密将增强通过网络在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例与应用程序之间传输的数据的安全性。 但是，启用加密的确会降低性能。  
  
本节中的各个主题介绍此 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 版本如何支持 TLS 加密（包括新的连接属性）以及如何在客户端配置信任存储区。  
  
> [!NOTE]  
> 建议使用 hostNameInCertificate  连接属性验证 TLS 证书。  

## <a name="in-this-section"></a>在本节中  

| 主题                                                                                                        | 说明                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [了解加密支持](../../connect/jdbc/understanding-ssl-support.md)                                 | 介绍 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 如何支持 TLS 加密。                                              |
| [使用加密进行连接](../../connect/jdbc/connecting-with-ssl-encryption.md)                       | 介绍如何使用 TLS 特定的新连接属性连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。 |
| [为加密配置客户端](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md) | 描述如何在客户端配置默认的信任存储区以及如何将私钥证书导入到客户端计算机的信任存储区中。   |
  
## <a name="see-also"></a>另请参阅

[保护 JDBC 驱动程序应用程序](../../connect/jdbc/securing-jdbc-driver-applications.md)  
