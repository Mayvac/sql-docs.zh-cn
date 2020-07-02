---
title: 事务生存期 |Microsoft Docs
description: 了解 SQL Server CLR 集成中的事务生存期。 在 Transact-sql 存储过程中启动的事务与在托管代码中启动的事务不同。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a9783922f2e1e908ee13efb97512b4c16135341
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765390"
---
# <a name="transaction-lifetimes"></a>事务生存期
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程中启动的事务与在托管代码中启动的事务之间存在一个重大区别：公共语言运行时 (CLR) 代码在进入或退出 CLR 调用时不能使事务状态取消均衡。 注意此区别的以下含义：  
  
-   必须提交或回滚在 CLR 框架内启动的事务，否则在退出该框架时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将产生错误。  
  
-   在 CLR 代码内不能提交或回滚外部事务。  
  
-   尝试提交不在同一过程中启动的事务将导致运行时错误。  
  
-   如果尝试回滚不是在同一过程中启动的事务，则会导致事务停止响应（防止任何其他副作用的操作发生）。 事务将断开连接，直到 CLR 代码离开作用域。 请注意当您在过程内检测到错误并想确保终止整个事务时，这可能很有用。  
  
## <a name="see-also"></a>另请参阅  
 [CLR 集成和事务](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
