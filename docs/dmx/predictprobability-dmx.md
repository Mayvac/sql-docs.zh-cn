---
description: PredictProbability (DMX)
title: PredictProbability (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 778c3539061f8739872ff9164f000118b1996215
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426139"
---
# <a name="predictprobability-dmx"></a>PredictProbability (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  返回指定状态的概率。  
  
## <a name="syntax"></a>语法  
  
```  
  
PredictProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>适用于  
 标量列。  
  
## <a name="return-type"></a>返回类型  
 一个标量值。  
  
## <a name="remarks"></a>备注  
 如果省略预测状态，则将使用概率最大的状态，不包括“缺失状态”存储桶。 若要包含缺少的状态存储桶，请将设置 \<predicted state> 为 **INCLUDE_NULL**。 若要返回缺少状态的概率，请将设置 \<predicted state> 为 NULL。  
  
> [!NOTE]  
>  某些挖掘模型不提供概率值，因此不能使用此函数。 此外，任何特定目标值的概率值都以不同方式计算，或可能有不同的解释，具体取决于所查询的模型类型。 有关如何为特定模型类型计算概率的详细信息，请参阅挖掘模型内容中的单个算法主题 [&#40;Analysis Services-数据挖掘&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining)。  
  
## <a name="examples"></a>示例  
 以下示例根据 TM Decision Tree 挖掘模型，使用自然预测联接确定某个人是否可能购买自行车，并且还确定该预测的概率。 在此示例中，有两个 PredictProbability 函数，分别用于每个可能的值。 如果省略此参数，则函数将返回最可能的值的概率。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictProbability([Bike Buyer], 1) AS [Bike Buyer = Yes],  
  PredictProbability([Bike Buyer], 0) AS [Bike Buyer = No]  
FROM [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 示例结果：  
  
|Bike Buyer|Bike Buyer = Yes|Bike Buyer = No|  
|----------------|-----------------------|----------------------|  
|1|0.867074195848097|0.132755556974282|  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘扩展插件 &#40;DMX&#41; 函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [函数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [&#40;DMX&#41;的常规预测函数 ](../dmx/general-prediction-functions-dmx.md)  
  
  
