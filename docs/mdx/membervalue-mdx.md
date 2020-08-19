---
description: MemberValue (MDX)
title: MemberValue (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aaa7592c5f2d3413a63fbc0867bb8857e5d87d73
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483790"
---
# <a name="membervalue-mdx"></a>MemberValue (MDX)


  返回成员的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
Member_Expression.MemberValue  
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 计算结果为成员的有效多维表达式 (MDX)。  
  
## <a name="return-value"></a>返回值  
 返回的成员值包含以下信息（按这些信息在返回值中出现的顺序列出）：  
  
-   值绑定（如果已定义）。  
  
-   原始数据类型的键（如果不存在名称绑定，或者键和标题绑定到同一列）。  
  
-   成员的标题。  
  
## <a name="example"></a>示例  
 下例将返回 Adventure Works 多维数据集 Date 维度中的第一个日期的值绑定、成员键和标题。  
  
```  
WITH MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn}  ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
