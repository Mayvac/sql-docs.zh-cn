---
title: RangeMax （DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 08882071e142fa97139dc2a89adffaa8e5d5f738
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970656"
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  返回为离散化列发现的预测存储桶的高端值。  
  
## <a name="syntax"></a>语法  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>应用到  
 标量列。  
  
## <a name="return-type"></a>返回类型  
 一个标量值。  
  
## <a name="remarks"></a>备注  
 **RangeMax**函数可在[SELECT 不同于 &#60;模型 &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)查询中使用。 与这种类型的查询一起使用时，标量列引用可以包含连续或离散的可预测列或输入列。  
  
 与[SELECT FROM &#60;模型一起使用时&#62; 预测联接 &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)， **RangeMin**、 **RangeMid**和**RangeMax**函数返回指定 bucket 的实际边界值。 例如，如果对一个离散化列执行预测，查询将返回该离散化列中存储桶数的预测值。 **RangeMin**、 **RangeMid**和**RangeMax**函数描述了预测指定的存储桶。 当**RangeMax**函数与预测联接语句一起使用时，标量列引用只能包含离散的可预测列。  
  
## <a name="examples"></a>示例  
 以下示例返回 Decision Tree 挖掘模型中“年收入”连续列的最小值、最大值和平均值。  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘扩展插件 &#40;DMX&#41; 函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [函数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [&#40;DMX&#41;的常规预测函数](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
