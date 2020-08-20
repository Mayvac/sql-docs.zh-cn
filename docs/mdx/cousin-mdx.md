---
description: Cousin (MDX)
title: 同级 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eff78bb06f935311f178d2e39be11bec3e959776
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500540"
---
# <a name="cousin-mdx"></a>Cousin (MDX)


  返回与指定的子成员在父成员下方具有相同的相对位置的子成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
Cousin( Member_Expression , Ancestor_Member_Expression )  
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
 *Ancestor_Member_Expression*  
 返回祖先成员的有效多维表达式 (MDX) 成员表达式。  
  
## <a name="remarks"></a>备注  
 此函数按各级别内的成员的顺序和位置进行操作。 如果有两个层次结构，第一个层次结构有四个级别，第二个层次结构有五个级别，则第一个层次结构的第三个级别与第二个层次结构的第三个级别是同级。  
  
## <a name="examples"></a>示例  
 下面的示例根据 2002 会计年度第四季度在 2003 会计年度中年级别上的祖先检索它的同级。 检索到的同级是 2003 会计年度第四季度。  
  
```  
SELECT Cousin   
   ( [Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002],  
     [Date].[Fiscal].[FY 2003]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
 下面的示例根据 2002 会计年度 7 月在 2004 会计年度第二季度中季度级别上的祖先检索它的同级。 检索到的同级是 2003 年 10 月。  
  
```  
SELECT Cousin   
   ([Date].[Fiscal].[Month].[July 2002] ,  
    [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2004]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
