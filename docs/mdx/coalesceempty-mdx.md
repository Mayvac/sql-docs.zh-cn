---
description: CoalesceEmpty (MDX)
title: CoalesceEmpty (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4fd02400d6b560e1cc0b21908b788a257f56b26c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487580"
---
# <a name="coalesceempty-mdx"></a>CoalesceEmpty (MDX)


  将空单元值转换为指定的非空单元值，该值可以是数字或字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
Numeric syntax  
CoalesceEmpty( Numeric_Expression1 [ ,Numeric_Expression2,...n] )  
  
String syntax  
CoalesceEmpty(String_Expression1 [ ,String_Expression2,...n] )  
```  
  
## <a name="arguments"></a>参数  
 *Numeric_Expression1*  
 返回数字的有效数值表达式，通常为单元坐标的多维表达式 (MDX)。  
  
 *Numeric_Expression2*  
 有效数值表达式，通常为指定的数值。  
  
 *String_Expression1*  
 有效字符串表达式，通常为返回字符串的单元坐标的多维表达式 (MDX)。  
  
 *String_Expression2*  
 有效字符串表达式，通常为指定的字符串值（该值被第一个字符串表达式返回的 NULL 代替）。  
  
## <a name="remarks"></a>备注  
 如果指定了一个或多个数值表达式，则 **CoalesceEmpty** 函数将返回第一个数值表达式的数值， (从左到右) 可解析为非空值。 如果指定的所有数值表达式都不能被解析为非空值，则此函数返回空单元值。 通常情况下，第二个数值表达式的值是被第一个数值表达式返回的 NULL 代替的数值。  
  
 如果指定了一个或多个字符串表达式，此函数将返回可被解析为非空值的第一个（从左向右）字符串表达式的值。 如果指定的所有字符串表达式都不能被解析为非空值，则此函数返回空单元值。 通常情况下，第二个字符串表达式的值是被第一个字符串表达式返回的 NULL 代替的字符串值。  
  
 **CoalesceEmpty**函数只能接受相同类型的值。 也就是说，指定的所有值表达式的值都必须为数值数据类型或空单元值，或者，指定的所有值表达式的值都必须为字符串数据类型或空单元值。 对此函数的一次调用不能同时包括数值表达式和字符串表达式。  
  
 有关空单元的详细信息，请参阅 OLE DB 文档。  
  
## <a name="example"></a>示例  
 下面的示例查询 **艾德工作** 多维数据集。 此示例将返回每个产品的订单数量以及按类别排列的订单数量百分比。 **CoalesceEmpty**函数确保在对计算成员进行格式设置时，将 null 值表示为零 (0) 。  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
