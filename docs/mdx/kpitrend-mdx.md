---
description: KPITrend (MDX)
title: KPITrend (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cc672146a8f00902012f21f48cbfed460eb48690
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483910"
---
# <a name="kpitrend-mdx"></a>KPITrend (MDX)


  返回表示指定关键绩效指标 (KPI) 走向部分的规范化值。  
  
## <a name="syntax"></a>语法  
  
```  
  
KPITrend(KPI_Name)  
```  
  
## <a name="arguments"></a>参数  
 *KPI_Name*  
 指定 KPI 名称的有效字符串表达式。  
  
## <a name="remarks"></a>备注  
 走向值通常为介于 -1 到 1 之间的规范化值。  
  
## <a name="example"></a>示例  
 下例将返回 Fiscal Year 属性层次结构中三个成员后代的渠道收入度量值的 KPI 值、KPI 目标、KPI 状态和 KPI 走向：  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
