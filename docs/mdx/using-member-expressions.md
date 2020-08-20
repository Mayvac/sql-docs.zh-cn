---
description: 使用成员表达式
title: 使用成员表达式 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e833d8d579841a3fc15aad89612a1d25b71fd0f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494821"
---
# <a name="using-member-expressions"></a>使用成员表达式


  成员表达式包含成员标识符、成员函数或可转换为成员的表达式。  
  
 成员标识符可以有许多不同的格式。 成员标识符的最简单形式由成员的名称组成。 例如：  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 但是，如果不同层次结构上有多个名称相同的成员，则没有方法能够确定查询将返回哪个成员。 例如，以下查询为名称为 [CY 2004] 的成员请求数据。 查询成功执行，但 Adventure Works 多维数据集中至少有六个具有该名称的成员：  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 因此，成员标识符的最可靠形式是成员的唯一名称，该名称保证能够标识多维数据集中的特定成员。 Analysis Services 可以通过多种方式生成唯一名称，但唯一名称始终至少由两个标识符组成：维度名称和成员名称或成员键。 唯一名称的格式如下：  
  
```  
  
Dimension_Name  
.[Hierarchy_Name.] [[{Member_Name | &Member_Key}.]... ] {Member_Name | &Member_Key}  
  
```  
  
 以下是 Adventure Works 多维数据集中成员唯一名称的一些示例：  
  
```  
[Measures].[Amount]  
[Date].[Calendar Year].&[2004]  
[Date].[Calendar].[Calendar Quarter].&[2004]&[1]  
[Employee].[Employees].&[112]  
[Product].[Product Categories].[All Products]  
  
```  
  
 存在返回成员的许多 MDX 函数。 有关完整列表，请参阅 mdx [函数引用 &#40;mdx&#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  有关成员名称和成员键的详细信息，请参阅 [使用成员、元组和集 &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx)。  
  
## <a name="see-also"></a>另请参阅  
 [MDX&#41;&#40;表达式 ](../mdx/expressions-mdx.md)  
  
  
