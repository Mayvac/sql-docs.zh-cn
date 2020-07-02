---
title: 将结果集发送到服务器（扩展存储过程 API）
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: c0ba957f0cde17f7accfeee66952fe2488a854bd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767750"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>将结果集发送到服务器（扩展存储过程 API）
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 请改用 CLR 集成。  
  
 将结果集发送到时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，扩展存储过程应调用相应的 API，如下所示：  
  
-   使用**srv_sendrow**发送所有行（如果有）之前或之后，可以按任意顺序调用**srv_sendmsg**函数。 在向客户端发送完成状态之前，必须将所有消息发送到客户端**srv_senddone**。  
  
-   对于发送到客户端的每行调用一次 srv_sendrow 函数****。 必须先将所有行发送到客户端，然后才能将任何消息、状态值或完成状态与**srv_sendmsg**、 **srv_pfield**的**srv_status**参数或**srv_senddone**一起发送。  
  
-   如果发送的行尚未使用**srv_describe**定义其所有列，则会导致应用程序引发信息性错误消息并向客户端返回失败消息。 在此情况下，将不发送该行。  
  
## <a name="see-also"></a>另请参阅  
 [创建扩展存储过程](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
