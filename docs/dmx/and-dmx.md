---
title: 和（DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea3cacd8fe2d80e6037cf83df9eea1fd112a4b05
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971808"
---
# <a name="and-dmx"></a>AND (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  对两个数值表达式执行逻辑与运算。  
  
## <a name="syntax"></a>语法  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>参数  
 Expression1  
 一个返回数值的有效数据挖掘扩展 (DMX) 表达式。  
  
 Expression2  
 一个返回数值的有效 DMX 表达式。  
  
## <a name="return-value"></a>返回值  
 一个布尔值。如果两个参数的处理结果均为 TRUE，则返回 TRUE；否则返回 FALSE。  
  
## <a name="remarks"></a>备注  
 在运算符执行逻辑与运算之前，两个参数都被视为布尔值（0 为 FALSE；其他为 TRUE）。 下表列出了不同参数值组合的返回值。  
  
|如果 Expression1 为|如果 Expression2 为|则返回值为|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|FALSE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘扩展插件 &#40;DMX&#41; 运算符引用](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [逻辑运算符 &#40;DMX&#41;](../dmx/operators-logical.md)   
 [运算符 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
