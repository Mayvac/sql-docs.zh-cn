---
description: 除 MDX 运算符引用
title: " (除以)  (MDX) |Microsoft Docs"
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a0d6947e1e0b4dc45d56980b734c2de98d8ad24c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484020"
---
# <a name="divide---mdx-operator-reference"></a>除 MDX 运算符引用


  执行算术运算，将一个数除以另一个数。  
  
## <a name="syntax"></a>语法  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>参数  
 *被除数*  
 返回数值的有效多维表达式 (MDX) 表达式。  
  
 *除数*  
 返回数值的有效 MDX 表达式。  
  
## <a name="return-value"></a>返回值  
 具有与优先级较高的参数相同的数据类型的值。  
  
## <a name="remarks"></a>备注  
 **/ (相除) **运算符返回的实际值表示第一个表达式除以第二个表达式所得的商。  
  
 两个表达式必须具有相同的数据类型，或者其中一个表达式必须能够隐式转换为另一个表达式的数据类型。 如果 *除数* 的计算结果为 null 值，则该运算符将引发错误。 如果 *除数* 和被 *除数* 的计算结果均为 null 值，则该运算符将返回 null 值。  
  
## <a name="examples"></a>示例  
 下面的示例演示了此运算符的用法。  
  
```  
-- This query returns the freight cost per user,  
-- for products, averaged by month.   
With Member [Measures].[Freight Per Customer] as  
    [Measures].[Internet Freight Cost]  
    /   
    [Measures].[Customer Count]  
  
SELECT   
    [Ship Date].[Calendar].[Calendar Year] Members ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
 非零或非 null 值除以零或 null 将返回无穷大值，该值在查询结果中显示为“1.#INF”值。 在大多数情况下，应检查是否被零除，以避免出现这种情况。 以下示例说明具体情况：  
  
 `//Returns 1.#INF when Internet Sales Amount is zero or null`  
  
 `Member [Measures].[Reseller to Internet Ratio] AS`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `//Traps the division by zero scenario and returns null instead of 1.#INF`  
  
 `Member [Measures].[Reseller to Internet Ratio With Error Handling] AS`  
  
 `IIF([Measures].[Internet Sales Amount]=0, NULL,`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount])`  
  
 `SELECT`  
  
 `{[Measures].[Reseller to Internet Ratio],[Measures].[Reseller to Internet Ratio With Error Handling]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
## <a name="see-also"></a>另请参阅  
 [IIf &#40;MDX&#41;](../mdx/iif-mdx.md)   
 [Mdx 运算符引用 &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
