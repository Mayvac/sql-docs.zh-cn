---
title: 更改单元中的项（报表生成器）| Microsoft Docs
description: 在报表生成器中使用新的报表项替换非容器项（例如文本框、线条或图像）。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c262d1c3b84f65c80897c28e6fa4de826aeb3a30
ms.sourcegitcommit: 93e4fd75e8fe0cc85e7949c9adf23b0e1c275465
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84255640"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>更改单元中的项（报表生成器和 SSRS）
在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 分页报表中，只有非容器项（例如文本框、线条或图像）才可以用新的报表项替换。 例如，可以将一个表拖到文本框中来用该表替换文本框。  
  
 如果单元中包含容器项（如矩形、列表、表或矩阵），新项则会添加到该容器项中，而不是替换容器项。 若要用新项替换容器项，则需要先删除该容器。 删除容器项将使该容器项替换为文本框，之后即可用其他项来替换该文本框。  
  
 默认情况下，表、矩阵或列表数据区域中的所有单元都包含文本框。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-an-item-within-a-cell"></a>更改单元中的项  
  
-   在 **“插入”** 选项卡的 **“数据区域”** 或 **“报表项”** 组中，单击要添加到报表的项，然后单击报表。 该项将添加到报表。  
  
> [!NOTE]  
>  在将某一图像报表项拖到单元中时，“图像属性”**** 对话框将打开，从中可以设置图像添加到单元前的属性，例如图像的源。  
  
## <a name="see-also"></a>另请参阅  
 [图像、文本框、矩形和线条（报表生成器和 SSRS）](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md)   
 [表、矩阵和列表（报表生成器和 SSRS）](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
