---
description: 连接到服务器 (Oracle)，连接属性
title: 连接到服务器 (Oracle)，连接属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d6a5c942305252f8e694042633651baf981032c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455609"
---
# <a name="connect-to-server-oracle-connection-properties"></a>连接到服务器 (Oracle)，连接属性
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  可以使用 **“连接到服务器”** 对话框的 **“连接属性”** 选项卡指定 **“网关”** 或 **“完整”** 发布选项。 标识发布服务器后，除非删除并重新配置发布服务器，否则无法更改此选项。 有关详细信息，请参阅[配置 Oracle 发布服务器](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)。  
  
## <a name="options"></a>选项  
 **发布者类型**  
 选择 **“网关”** 或 **“完整”**。 **“完整”** 选项用于为快照和事务发布提供所支持的完整的 Oracle 发布功能集。 **“网关”** 选项提供特定的设计优化，以提高复制作为系统间的网关时的性能。 如果计划在多个事务发布中发布同一个表，则无法使用 **“网关”** 选项。 如果选择 **“网关”** ，则一个表可以最多出现在一个事务发布中或出现在任意数量的快照发布中。  
  
 **超时值**  
 指定在发生超时错误之前，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分发服务器尝试连接到 Oracle 发布服务器的时间。  
  
## <a name="see-also"></a>另请参阅  
 [有关 Oracle 发布的术语词汇表](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Oracle 发布服务器的性能优化](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
