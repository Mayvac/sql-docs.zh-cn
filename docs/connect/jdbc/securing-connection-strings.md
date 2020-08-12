---
title: 保护连接字符串
description: 了解如何在使用 JDBC Driver for SQL Server 时保护连接字符串信息。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 69ce8557-5260-4ea4-81b8-d0c5481f0868
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8fc42c778e0a8971ea36b8c0588765e82ee8fd2
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391142"
---
# <a name="securing-connection-strings"></a>保护连接字符串

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

帮助保护应用程序的最重要目标之一是保护对数据源的访问。 要限制对数据源的访问，必须采取防范措施（例如用户 ID、密码和数据源名称）来帮助保护连接信息。 以纯文本的形式存储用户 ID 和密码（例如在源代码中）会造成严重的安全问题。 即使你提供的包含外部源中的用户 ID 和密码信息的代码是已编译版本，但已编译代码还是可能遭拆解，从而泄露用户 ID 和密码。 因此，请勿在代码中包含用户 ID 和密码之类的重要信息。

建议忽略在应用程序源代码中存储密码和连接 URL。 而是考虑将密码存储在限制访问的单独文件中。 可以向应用程序的运行上下文授予该文件的访问权限。

另一种方法将经过加密的密码存储在一个文件中。 确保使用的加密 API 不需要在其他位置存储密钥，并且不是由用户的密码派生而来。 例如，可以考虑使用基于证书的公钥/私钥对，或使用以下方法：双方使用密钥一致协议（Diffie-Hellman 算法）生成相同的加密密钥，从而无需传输密钥。

如果从外部源（例如用户提供的用户 ID 和密码）获取连接字符串信息，则必须验证来自该源的所有输入，以确保这些信息遵循正确的格式，并且不包含影响连接的其他参数。

## <a name="see-also"></a>另请参阅

[保护 JDBC 驱动程序应用程序](../../connect/jdbc/securing-jdbc-driver-applications.md)
