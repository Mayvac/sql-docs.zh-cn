---
title: 默认跟踪日志文件已禁用 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 2e8335f3fa61cc446db748a4913d6eaa22388659
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749466"
---
# <a name="default-trace-log-files-disabled"></a>默认跟踪日志文件已禁用
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  此规则检查 sp_configure 存储过程 default trace enabled 选项的值，以确定默认跟踪是设置成了 ON (1) 还是设置成了 OFF (0)。 启用此选项后，默认跟踪提供有关对 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]进行的配置和 DDL 更改的信息。 在某些情况下，当客户和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户服务与支持部门解决 [!INCLUDE[ssDE](../../includes/ssde-md.md)]问题时，此信息对他们可能会有所帮助。  
  
## <a name="best-practices-recommendations"></a>最佳做法建议  
 使用 sp_configure 存储过程通过将 default trace enabled 的值设置为 1 来启用跟踪。  
  
## <a name="for-more-information"></a>有关详细信息  
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>另请参阅  
 [使用基于策略的管理来监视和强制执行最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
