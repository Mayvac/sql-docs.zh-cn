---
description: Lead (MDX)
title: 潜在 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ca78bdeca6103758d5d102ed8b85eb00b3138e18
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387323"
---
# <a name="lead-mdx"></a>Lead (MDX)


  返回在成员级别中比指定成员位置靠后且靠后位数为指定位数的成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
 *索引*  
 指定成员位置位数的有效数值表达式。  
  
## <a name="remarks"></a>备注  
 级别内的成员位置由属性层次结构的自然顺序决定。 位置的编号从零开始。  
  
 如果指定的 lead 为零 (0) ，则 **导引** 函数返回指定的成员。  
  
 如果指定的 lead 为负数，则该 **lead** 函数将返回前面的成员。  
  
 `Lead(1)` 等效于 [NextMember](../mdx/nextmember-mdx.md) 函数。 `Lead(-1)` 等效于 [PrevMember](../mdx/prevmember-mdx.md) 函数。  
  
 **导引**函数与[lag](../mdx/lag-mdx.md)函数类似，只不过**lag**函数与**导引**函数的方向相反。 也就是说，`Lead(n)` 等效于 `Lag(-n)`。  
  
## <a name="example"></a>示例  
 下例将返回 2001 年 12 月的值：  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(-2) ON 0  
FROM [Adventure Works]  
  
```  
  
 下例将返回 2002 年 3 月的值：  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
