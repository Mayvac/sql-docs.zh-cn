---
description: 集合运算符
title: 设置运算符 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb4434c9fe1991e1398baaa9c7bfd9602995652d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341233"
---
# <a name="set-operators"></a>集合运算符


  在多维表达式 (MDX) 中，集运算符对成员或集进行运算并返回一个集。 通常用集运算符替换 MDX 表达式中的多个集函数。  
  
 MDX 支持下表中列出的集运算符。  
  
|操作员|描述|  
|--------------|-----------------|  
|[-（排除）](../mdx/except-mdx-operator.md)|返回两个集之间的不同项，并删除重复的成员。<br /><br /> 此运算符在功能上等效于 [Except](../mdx/except-mdx-function.md) 函数。|  
|[*（叉积）](../mdx/crossjoin-mdx-operator-reference.md)|返回两个集的叉积。<br /><br /> 此运算符在功能上等效于 [交叉结合](../mdx/crossjoin-mdx.md) 函数。|  
|[： (范围) ](../mdx/range-mdx.md)|返回自然排序的集，并将两个指定的成员作为终结点，这两个指定成员之间的所有成员都作为集的成员包括在其中。|  
|[+（并集）](../mdx/union-mdx-operator-reference.md)|返回两个集的并集，不包括重复的成员。<br /><br /> 此运算符在功能上等效于 [联合 &#40;MDX&#41;](../mdx/union-mdx.md) 函数。|  
  
## <a name="see-also"></a>另请参阅  
 [Mdx 函数引用 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Mdx 运算符引用 &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [运算符 &#40;MDX 语法&#41;](../mdx/operators-mdx-syntax.md)  
  
  
