---
description: Members（字符串）(MDX)
title: " (字符串) 的成员 (MDX) |Microsoft Docs"
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 95e90f488f4b9182fc237045b570bc9da02f47e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483820"
---
# <a name="members-string-mdx"></a>Members（字符串）(MDX)


  返回字符串表达式所指定的成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>参数  
 *Member_Name*  
 指定成员名称的有效字符串表达式。  
  
## <a name="remarks"></a>备注  
 ** (String) **函数的成员返回指定了名称的单个成员。 通常，使用 **成员 (字符串) ** 函数与外部函数，为 **成员 (string) ** 函数指定标识成员的字符串， **成员 (string) ** 函数返回此指定成员的值。  
  
## <a name="example"></a>示例  
 下面的示例使用 **成员 (String) ** 函数将指定的字符串转换为有效的成员，然后返回字符串中指定的成员的默认度量值。 指定的字符串用单引号引起来。 默认度量值为 Reseller Sales Amount 度量值。  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
