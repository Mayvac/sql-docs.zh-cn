---
title: 从饼图顶部开始绘制饼图值（报表生成器）| Microsoft Docs
description: 了解如何从图表顶部开始绘制饼图值，而不是从与顶部成 90 度的默认位置开始绘制。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: dfdd7600a08a78baa0b70f2048423f1632ebe2db
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83689435"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>从饼图顶部开始绘制饼图值（报表生成器和 SSRS）
默认情况下，在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 分页报表的饼图中，数据集中的第一个值从与饼顶部成 90 度的位置开始绘制。 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*图表值从 90 度的位置开始绘制。*

也许你希望从顶部开始绘制第一个值。 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*图表值从图表的顶部开始绘制。*
  
## <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>从饼顶部开始绘制饼图  
  
1.  单击饼图本身。  
  
2.  如果 **“属性”** 窗格未打开，请单击 **“视图”** 选项卡上的 **“属性”** 。  
  
3.  在 **“属性”** 窗格中，在 **“自定义属性”** 下，将 **PieStartAngle** 从 **0** 更改为 **270**。  
  
4.  单击 **“运行”** 以预览报表。  
  
 第一个值现在将从饼图顶部开始绘制。  
  
## <a name="see-also"></a>另请参阅  
 [设置图表格式（报表生成器和 SSRS）](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [饼图&#40;报表生成器和 SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  
