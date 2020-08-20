---
description: SetToStr (MDX)
title: SetToStr (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0317de06f3d68388fac5be752d26e27f0d373a89
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500440"
---
# <a name="settostr-mdx"></a>SetToStr (MDX)


  返回多维表达式 (MDX) 格式的字符串，它对应于指定的集合。  
  
## <a name="syntax"></a>语法  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>备注  
 该函数用于将某集的字符串表示形式传输到外部函数，以进行分析。 返回的字符串括在大括号中 {} ，其中的每一项都由逗号分隔。  
  
## <a name="example"></a>示例  
 下面的示例将返回包含 Geography.Country 属性层次结构的所有成员的字符串。  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
