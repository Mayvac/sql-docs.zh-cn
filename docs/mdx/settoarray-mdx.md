---
description: SetToArray (MDX)
title: SetToArray (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f5b0c4b39761e25065b2c262943b4ce335fccf6e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386973"
---
# <a name="settoarray-mdx"></a>SetToArray (MDX)


  将一个或多个集转换为数组，以便在用户定义函数中使用。  
  
## <a name="syntax"></a>语法  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression1*  
 返回集的有效多维表达式 (MDX)。  
  
 *Set_Expression2*  
 返回集的有效多维表达式 (MDX)。  
  
 *Numeric_Expression*  
 返回数字的有效数值表达式，通常为单元坐标的多维表达式 (MDX)。  
  
## <a name="remarks"></a>备注  
 **SetToArray**函数将一个或多个集转换为数组，以便在用户定义函数中使用。 所得到的数组中的维度数与指定的集数相同。  
  
 可选的数值表达式可以为数组单元提供值。 如果未指定数值表达式，则在当前上下文中对集的交叉联接求值。  
  
 所得到的数组中的单元坐标与各个集在列表中的位置相对应。 例如，有三个集，`SA`、`SB` 和 `SC`。 其中每个集都有两个元素。 则 MDX 语句 `SetToArray(SA, SB, SC)` 创建以下三维数组：  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  **SetToArray**函数的返回类型是 VT_ARRAY 的变量类型。 因此， **SetToArray** 函数的输出应仅用作用户定义函数的输入。  
  
## <a name="example"></a>示例  
 下例将返回一个数组。  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
