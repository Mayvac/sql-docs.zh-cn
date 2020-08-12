---
title: 通过添加带状线突出显示图表数据（报表生成器）| Microsoft Docs
description: 在水平或垂直范围内使用带状线可提高可读性、突出显示日期或突出显示报表生成器中的特定键范围。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: addd6137-4b6e-4e88-a7e8-9600fcd1ccce
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b06345fef2d2bc813cfd146c8b31a53b54451859
ms.sourcegitcommit: f898aa83561e94626024916932568ab05e73b656
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84011695"
---
# <a name="highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs"></a>通过添加条带线突出显示图表数据（报表生成器和 SSRS）
  条带线（或条带）是按固定或自定义间隔使图表背景带有阴影的水平或垂直区域。 可以使用条带线执行以下操作：  
  
-   提高在图表上查找各个值时的可读性。 指定固定间隔的条带线有助于读取该图表时分离数据点。  
  
-   突出显示定期出现的日期。 例如，在销售报表中，可能会使用条带线标识周末数据点。  
  
-   突出显示特定键范围。 在上一示例中，可以使用一根条带线突出显示 80-100 美元之间的最高销售额区域。  
  
 条带线不适用于极坐标图或形状图类型。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-interlaced-strip-lines-at-regular-intervals-on-a-chart"></a>在图表上按固定间隔显示交错条带线  
  
1.  若要显示水平带状线，请右键单击垂直图表轴，然后单击“垂直轴属性”。  
  
     若要显示垂直带状线，请右键单击水平图表轴，然后单击“水平轴属性”。  
  
2.  选择 **“使用交错”** 选项。 图表上将显示灰色条带线。  
  
3.  （可选）使用相邻的“颜色”下拉列表指定带状线的颜色。  
  
### <a name="to-display-interlaced-strip-lines-at-custom-intervals-on-a-chart"></a>在图表上按自定义间隔显示交错条带线  
  
1.  若要显示水平带状线，请右键单击垂直图表轴，然后单击“垂直轴属性”。  
  
     若要显示垂直带状线，请右键单击水平图表轴，然后单击“水平轴属性”。  
  
     轴属性将显示在“属性”窗口中。  
  
2.  在“属性”窗格的“外观”部分的 StripLines 属性中，单击“编辑集合(…)”按钮打开“ChartStripLine 集合编辑器” 。  
  
3.  单击 **“添加”** 向集合中添加一个新条带线。  
  
4.  单击 StripWidth 可指定报表上带状线的宽度（以英寸为单位）。 如果是突出显示日期或时间，请单击 StripWidthType，然后选择一个时间间隔。  
  
5.  键入 Interval 的值或表达式以指定带状线的重复显示频率。  例如，如果指定间隔为 10，条带线宽度为 5，则条带线将在 0 到 5、15 到 20、30 到 35 等处显示。  
  
> [!NOTE]  
>  默认情况下，Interval 设置为“自动”，这表示图表将不计算自定义带状线的间隔。 仅当设置间隔值后图表才计算条带线的间隔。  
  
## <a name="see-also"></a>另请参阅  
 [设置图表上轴标签的格式（报表生成器和 SSRS）](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [设置图表格式（报表生成器和 SSRS）](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [向图表添加移动平均线（报表生成器和 SSRS）](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
  
  
