---
title: XTP 垃圾回收 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a064fec82054d434cc0ca577bc1dd013f3d16f2f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "85016842"
---
# <a name="xtp-garbage-collection"></a>XTP 垃圾收集
  XTP 垃圾收集性能对象包含与 XTP 引擎的垃圾收集器相关的计数器。  
  
 下表介绍了**XTP 垃圾回收**计数器。  
  
|计数器|说明|  
|-------------|-----------------|  
|**灰尘角扫描重试次数/秒（垃圾收集器发出）**|在垃圾收集器发出的灰尘角扫描期间，由于写冲突而进行的每秒扫描重试次数（平均值）。 此为非常低级的计数器，不适合客户使用。|  
|**主垃圾收集器工作项数/秒**|主垃圾收集器线程处理的工作项数。|  
|**并行垃圾收集器工作项数/秒**|并行线程执行垃圾收集器工作项的次数。|  
|**处理的行数/秒**|垃圾收集器每秒处理的行数（平均值）。|  
|**处理的行数/秒（桶中的第一行并能删除）**|垃圾收集器每秒处理的、在相应哈希桶中是第一行并能立即删除的行数（平均值）。|  
|**处理的行数/秒（桶中的第一行）**|垃圾收集器每秒处理的、在相应哈希桶中是第一行的行数（平均值）。|  
|**处理的行数/秒（标记为取消链接）**|垃圾收集器每秒处理的、已标记为取消链接的行数（平均值）。|  
|**处理的行数/秒（无需扫描）**|垃圾收集器每秒处理的、无需灰尘角扫描的行数（平均值）。|  
|**扫描中删除的过期行数/秒**|灰尘角扫描期间每秒删除的过期行数（平均值）。|  
|**扫描中接触的过期行数/秒**|灰尘角扫描期间每秒接触的过期行数（平均值）。|  
|**扫描中接触的即将到期的行数/秒**|灰尘角扫描期间每秒接触的即将到期的行数（平均值）。|  
|**扫描中接触的行数/秒**|灰尘角扫描期间每秒接触的行数（平均值）。|  
|**启动的扫描数/秒**|每秒启动的灰尘角扫描数（平均值）。|  
  
## <a name="see-also"></a>另请参阅  
 [XTP &#40;内存中 OLTP&#41; 性能计数器](../../integration-services/performance/performance-counters.md)  
  
  
