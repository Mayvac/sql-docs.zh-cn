---
description: RollupChildren (MDX)
title: RollupChildren (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fb4e3552b5c5f5a708a70754d816ab1a78008248
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341313"
---
# <a name="rollupchildren-mdx"></a>RollupChildren (MDX)


  使用指定的一元运算符，通过汇总指定成员的子成员的值，从而返回所生成的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
RollupChildren(Member_Expression, Unary_Operator)   
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
 *Unary_Operator*  
 指定一元运算符的有效字符串表达式。  
  
## <a name="remarks"></a>备注  
 **RollupChildren**函数使用指定的一元运算符对指定成员的子级的值进行汇总。  
  
 下表说明了可用于此函数的有效一元运算符。  
  
|运算符|结果|  
|--------------|------------|  
|**+**|total = total + current child|  
|**-**|总额 = 总额 - 当前子级|  
|**\***|total = total * current child|  
|**/**|total = total / current child|  
|**%**|total = (total / current child) * 100|  
|**~**|不在汇总结果中使用子成员。 子成员的值将被忽略。|  
  
 如果成员属性中的运算符未显示在列表中，则会发生错误。 求值顺序取决于同级的顺序，而不是运算符的优先顺序。  
  
## <a name="example"></a>示例  
 下例使用名为“Alternate Rollup Operator”的成员属性（包含一元运算符的备用值）以备用方式汇总 Account（帐户）维度中 Net Profit（净利润）层次结构的子成员。 该成员属性不在 Adventure Works 多维数据集中，但是可以创建。 使用 **RollupChildren** 函数可以在预算应用程序中用于假设分析。  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
