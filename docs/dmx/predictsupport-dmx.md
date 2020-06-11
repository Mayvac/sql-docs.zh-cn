---
title: PredictSupport （DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7a6509980065c2293a0b2697beacae1ba2d4b0d1
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83667195"
---
# <a name="predictsupport-dmx"></a>PredictSupport (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  返回指定状态的支持值。  
  
## <a name="syntax"></a>语法  
  
```  
  
PredictSupport(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>应用于  
 标量列。  
  
## <a name="return-type"></a>返回类型  
 标量列引用指定的类型的标量值 *\<* *>* 。  
  
## <a name="remarks"></a>注解  
 如果未提供预测状态，将使用具有最大可预测概率的状态，不包括缺少状态存储桶。 若要包含缺少的状态存储桶，请将 \< 预测状态> 设置为**INCLUDE_NULL**。  
  
 若要返回对缺少状态的支持，请将 \< 预测状态> 设置为 NULL。  
  
> [!NOTE]  
>  支持值都以不同方式计算，或可能有不同的解释，具体取决于所查询的模型类型。 有关如何为任何特定模型类型计算支持的详细信息，请参阅挖掘模型内容中的单个算法类型[&#40;Analysis Services-数据挖掘&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining)。  
  
## <a name="examples"></a>示例  
 以下示例根据 TM Decision Tree 挖掘模型，使用单独查询预测某个人是否购买自行车，并且还确定对该预测的支持。  
  
```  
SELECT  
  [Bike Buyer],  
  PredictSupport([Bike Buyer]) AS [Support],  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘扩展插件 &#40;DMX&#41; 函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [函数 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [&#40;DMX&#41;的常规预测函数](../dmx/general-prediction-functions-dmx.md)  
  
  
