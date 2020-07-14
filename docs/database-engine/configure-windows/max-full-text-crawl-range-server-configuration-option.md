---
title: max full-text crawl range 服务器配置选项 | Microsoft Docs
description: 了解“max full-text crawl range”选项。 了解它如何优化 SQL Server CPU 利用率，从而提高完全爬网时的爬网性能。
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 73a6223467b2da09d26e351c2cf2eb1a12576d80
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680840"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>max full-text crawl range 服务器配置选项
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  使用 **max full-text crawl range** 选项可以优化 CPU 使用率，从而提高完全爬网时的爬网性能。 使用此选项，可以指定索引完全爬网时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的分区数。 例如，如果有许多 CPU 且它们的使用率并非最佳，则可以增加此选项的最大值。 除了此选项以外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 还使用众多其他因素（如表中的行数和 CPU 数）来确定应该使用的实际分区数。  
  
 此选项的默认值是 4；最小值是 1，最大值是 256。 对此选项所做的更改只会影响后续的爬网。 不会影响正在进行的爬网。  
  
 **max full-text crawl range** 选项是一个高级选项。 如果使用 **sp_configure** 系统存储过程来更改该设置，则仅当 **显示高级选项** 设置为 1 时才能更改 **max full-text crawl range** （全文爬网最大范围）。 该设置将立即生效，无需重新启动服务器。  
  
## <a name="see-also"></a>另请参阅  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
