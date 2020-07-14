---
title: 日志读取器代理安全性 (SSMS)
description: 介绍 SQL Server Management Studio (SSMS) 中事务和对等发布的“日志读取器代理安全性”页面。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef28a7831ad5d4c63b450da177037d55534b5f63
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716766"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a>日志读取器代理的安全性（对等复制）
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  可以使用 **“日志读取器代理安全性”** 页，指定日志读取器代理在各对等方运行和建立连接时使用的帐户。 有关代理要求的权限及复制安全的最佳做法的信息，请参阅[复制代理安全模型](../../relational-databases/replication/security/replication-agent-security-model.md)和[复制安全最佳做法](../../relational-databases/replication/security/replication-security-best-practices.md)。  
  
> [!NOTE]  
>  对于使用事务复制发布的每个数据库，都有一个日志读取器代理。 如果已经配置数据库的日志读取器代理（不管是在上一次运行此向导时针对发布配置的，还是针对同一数据库中另一个事务发布配置的），则不能在此向导中更改该代理使用的凭据。 如果指定新凭据，它们将被忽略。 若要更改凭据，请使用 **“发布属性”** 对话框。 有关详细信息，请参阅 [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)。  
  
## <a name="options"></a>选项  
 在各对等方的行中单击属性按钮 ( **...** )，可以访问 **“日志读取器代理安全性”** 对话框。 若要了解有关代理所使用帐户需要的权限的详细信息，请在 **“日志读取器代理安全性”** 对话框启动后单击其中的 **“帮助”** 。  
  
 在对话框中输入设置之后，网格中将显示订阅服务器的连接信息。  
  
 **发布服务器的代理**  
 每个对等服务器实例的名称。  
  
 **对等数据库**  
 各对等方上用作发布数据库和订阅数据库的数据库。  
  
 **与分发服务器的连接**  
 连接到分发服务器时所处的上下文。 与分发服务器的本地连接始终是使用运行代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户的上下文建立的，因此，此字段将始终显示“模拟‘\<Domain>\\<登录名\>’”或“模拟‘\<Computer>\\<登录名\>’”。  
  
 **与发布服务器的连接**  
 与发布服务器建立连接时所处的上下文。 通过使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名，或使用运行代理的 Windows 帐户的上下文，可以与发布服务器建立连接。 该字段显示下列选项之一：使用登录名“\<Login>”、模拟“\<Domain><登录名\>”或模拟“\<Computer>\\<登录名\>” **\\** 。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建议使用 Windows 帐户的上下文建立所有连接。  
  
## <a name="see-also"></a>另请参阅  
 [管理对等拓扑（复制 Transact-SQL 编程）](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [@loopback_detection](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
