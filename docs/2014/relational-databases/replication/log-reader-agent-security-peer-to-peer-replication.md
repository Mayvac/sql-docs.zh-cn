---
title: 日志读取器代理安全性（对等复制）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae5c8d56c1d51290c35a04c22474fcc04ddff61d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065911"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a>日志读取器代理的安全性（对等复制）
  可以使用“日志读取器代理安全性”**** 页，指定日志读取器代理在各对等方运行和建立连接时使用的帐户。 有关代理要求的权限及复制安全的最佳做法的信息，请参阅[复制代理安全模型](security/replication-agent-security-model.md)和[复制安全最佳做法](security/replication-security-best-practices.md)。  
  
> [!NOTE]  
>  对于使用事务复制发布的每个数据库，都有一个日志读取器代理。 如果已经配置数据库的日志读取器代理（不管是在上一次运行此向导时针对发布配置的，还是针对同一数据库中另一个事务发布配置的），则不能在此向导中更改该代理使用的凭据。 如果指定新凭据，它们将被忽略。 若要更改凭据，请使用 **“发布属性”** 对话框。 有关详细信息，请参阅[查看和修改复制安全设置](security/view-and-modify-replication-security-settings.md)。  
  
## <a name="options"></a>选项  
 在各对等方的行中单击属性按钮 (**...**)，可以访问 **“日志读取器代理安全性”** 对话框。 若要了解有关代理所使用帐户需要的权限的详细信息，请在 **“日志读取器代理安全性”** 对话框启动后单击其中的 **“帮助”** 。  
  
 在对话框中输入设置之后，网格中将显示订阅服务器的连接信息。  
  
 **发布服务器的代理**  
 每个对等服务器实例的名称。  
  
 **对等数据库**  
 各对等方上用作发布数据库和订阅数据库的数据库。  
  
 **与分发服务器的连接**  
 连接到分发服务器时所处的上下文。 与分发服务器的本地连接始终使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 运行代理的 Windows 帐户的上下文建立，因此，此字段将始终显示 "**模拟" \<Domain> \\<登录名 \> ** "或 **" 模拟 " \<Computer> \\<登录名 \> "**。  
  
 **与发布服务器的连接**  
 与发布服务器建立连接时所处的上下文。 可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名或使用运行代理的 Windows 帐户的上下文来建立与发布服务器的连接。 此字段显示以下内容之一： "**使用登录名 ' \<Login> "**、 **"模拟 ' \<Domain> \\<登录名 \> "** 或 **"模拟 ' \<Computer> \\<登录名 \> '**"。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建议使用 Windows 帐户的上下文建立所有连接。  
  
## <a name="see-also"></a>另请参阅  
 [&#40;复制 Transact-sql 编程来管理对等拓扑&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [对等事务复制](transactional/peer-to-peer-transactional-replication.md)  
  
  
