---
title: 设置仪表范围格式（报表生成器）| Microsoft Docs
description: 使用仪表范围，能以可见方式指示指针值何时进入报表生成器中的某个值范围。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2b8962eb617538a44e66ba98533cd00947e29272
ms.sourcegitcommit: 93e4fd75e8fe0cc85e7949c9adf23b0e1c275465
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84255488"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a>设置仪表上范围的格式（报表生成器和 SSRS）
 在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 分页报表中，仪表范围是仪表刻度上的带区或区域，用于指示仪表上一段重要的值。 使用仪表范围，能以可见方式指示指针值何时进入某个值范围。 范围由开始值和结束值定义。  
  
 还可以使用范围来定义仪表的各个不同分段。 例如，在值从 0 到 10 的仪表上，可以定义从 0 到 3 的值为红色范围，从 4 到 7 的值为黄色范围，从 8 到 10 的值为绿色范围。 如果指定的开始值大于指定的结束值，则值将交换，以使开始值成为结束值，而结束值成为开始值。  
  
 可以使用在刻度上放置指针的相同方式来设置范围。 **“位置”** 和 **“到刻度的距离”** 属性可确定范围的位置。 有关详细信息，请参阅 [仪表（报表生成器和 SSRS）](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [设置仪表上刻度的格式（报表生成器和 SSRS）](../../reporting-services/report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [设置仪表上指针的格式（报表生成器和 SSRS）](../../reporting-services/report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [设置仪表的最小值或最大值（报表生成器和 SSRS）](../../reporting-services/report-design/set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)   
 [教程：向报表添加 KPI（报表生成器）](../../reporting-services/tutorial-adding-a-kpi-to-your-report-report-builder.md)   
 [仪表（报表生成器和 SSRS）](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  
