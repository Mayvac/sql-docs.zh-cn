---
title: 百分比抽样转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.percentagesamplingtrans.f1
- sql13.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba85ead154888f68cab1ed343fc03b643049f91a
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919559"
---
# <a name="percentage-sampling-transformation"></a>百分比抽样转换

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  百分比抽样转换通过选择转换输入行的百分比来创建样本数据集。 样本数据集是从转换输入中随机选择的行，这使得结果样本可以代表输入。  
  
> [!NOTE]  
>  除指定的百分比以外，百分比抽样转换还使用某种算法来决定样本输出中是否应包含某一行。 这意味着样本输出中的行数可能无法精确地反映指定的百分比。 例如，为具有 25000 行的输入数据集指定 10% 可能不会生成具有 2500 行的样本；样本的行数可能略多于或略少于 2500 行。  
  
 百分比抽样转换对数据挖掘尤其有用。 通过使用此转换，您可以将一个数据集随机划分为两个数据集：一个用于定型数据挖掘模型，另一个用于测试模型。  
  
 百分比抽样转换对于创建用于包开发的样本数据集也很有用。 通过对数据流应用百分比抽样转换，可以在保持数据集的数据特性的同时均匀地缩减数据集的大小。 然后，测试包就可以更快地运行，因为它使用小但具有代表性的数据集。  
  
## <a name="configuration-the-percentage-sampling-transformation"></a>百分比抽样转换的配置  
 可以通过指定抽样种子来修改随机数生成器（转换通过随机数生成器来选择行）的行为。 如果使用相同的抽样种子，转换将始终创建相同的样本输出。 如果没有指定种子，转换将使用操作系统的时钟周期数来创建随机数。 因此，在包的开发和测试期间，需要验证转换结果时可选择使用标准种子，然后在包正式投入生产后再改为使用随机种子。  
  
 此转换类似于行抽样转换，后者通过选择指定数量的输入行来创建样本数据集。 有关详细信息，请参阅 [Row Sampling Transformation](../../../integration-services/data-flow/transformations/row-sampling-transformation.md)。  
  
 百分比抽样转换包括 **SamplingValue** 自定义属性。 加载包时，可以通过属性表达式更新此属性。 有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../../integration-services/expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../../integration-services/expressions/use-property-expressions-in-packages.md)和[转换自定义属性](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)。  
  
 该转换有一个输入和两个输出。 它不支持错误输出。  
  
 可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。  
  
 **“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。 有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：  
  
-   [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [转换自定义属性](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)。  
  
## <a name="percentage-sampling-transformation-editor"></a>百分比抽样转换编辑器
  可以使用 **“百分比抽样转换编辑器”** 对话框，使用指定的行百分比将部分输入拆分成样本。 此转换将输入分成两个单独的输出。  
  
### <a name="options"></a>选项  
 **行百分比**  
 指定输入中要用作样本的行百分比。  
  
 此属性的值可以使用属性表达式来指定。  
  
 **样本的输出名称**  
 为包含抽样行的输出提供唯一名称。 所提供的名称将显示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中。  
  
 **未选中部分的输出名称**  
 为包含非抽样行的输出提供唯一名称。 所提供的名称将显示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中。  
  
 **使用以下随机种子**  
 指定随机数生成器的抽样种子，转换将使用该种子来创建样本。 建议只在开发和测试过程中使用此选项。 如果未指定随机种子，转换将使用 Microsoft Windows 的时钟周期计数。  
  
  
