---
title: ft crawl bandwidth 服务器配置选项 | Microsoft Docs
description: 了解“ft crawl bandwidth”选项。 了解它如何影响 SQL Server 在大型内存缓冲区池中维护的缓冲区数量。
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
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 59caa1e868c4caab24afd17909c34f57c96f0005
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789791"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a>ft crawl bandwidth 服务器配置选项
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  使用 **ft crawl bandwidth** 选项可指定较大内存缓冲池可增长到多大。 较大内存缓冲区的大小为 4 MB。 **max** 参数值可指定全文内存管理器应在较大缓冲池中保持的最大缓冲区数。 如果 **max** 的值为零，则较大缓冲池中可以保持的缓冲区数没有上限。  
  
 **min** 参数可指定较大内存缓冲池中必须保持的最小内存缓冲区数。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内存管理器发出请求后，将释放所有额外的缓冲池，但将保留该最低数量的缓冲区。 不过，如果指定的 **min** 值为零，则释放所有内存缓冲区。  
  
 在某些情况下，当前分配的缓冲区数会小于 **min** 参数指定的值。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ft notify bandwidth 服务器配置选项](../../database-engine/configure-windows/ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
