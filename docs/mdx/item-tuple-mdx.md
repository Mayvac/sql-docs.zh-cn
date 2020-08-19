---
description: Item（元组）(MDX)
title: 项 (元组)  (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1e98e6901c018a6c8be5187024e5462cc8d19547
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483950"
---
# <a name="item-tuple-mdx"></a>Item（元组）(MDX)


  返回某个集中的元组。  
  
## <a name="syntax"></a>语法  
  
```  
  
Index syntax  
Set_Expression.Item(Index)  
  
String expression syntax  
Set_Expression.Item(String_Expression1 [ ,String_Expression2,...n])  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
 *String_Expression1*  
 通常是以字符串表示的元组的有效字符串表达式。  
  
 *String_Expression2*  
 通常是以字符串表示的元组的有效字符串表达式。  
  
 *索引*  
 根据集中位置指定要返回的特定元组的有效数值表达式。  
  
## <a name="remarks"></a>备注  
 **Item**函数返回指定集中的元组。 可以通过三种方式调用 **Item** 函数：  
  
-   如果指定了单个字符串表达式，则 **Item** 函数返回指定的元组。 例如，"([2005].Q3, [Store05])"。  
  
-   如果指定了多个字符串表达式，则 **Item** 函数将返回由指定坐标定义的元组。 字符串数必须与轴数一致，而且每个字符串都必须标识一个唯一的层次结构。 例如，"[2005].Q3", "[Store05]"。  
  
-   如果指定了整数，则 **Item** 函数将返回在 *Index*指定的从零开始的位置中的元组。  
  
## <a name="examples"></a>示例  
 下面的示例返回 ([1996],Sales)：  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 下面的示例使用一个级别表达式，并返回 Australia 中每个 State-Province 的 Internet Sales Amount 及其占 Australia 总 Internet Sales Amount 的百分比。 此示例使用 Item 函数从 **上级** 函数返回的集中提取第一个 (和仅元组) 。  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],    
      Ancestors   
      ( [Customer].[Customer Geography].CurrentMember,  
        [Customer].[Customer Geography].[Country]  
      ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{ Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],  
     [Customer].[Customer Geography].[State-Province], SELF   
   )   
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
