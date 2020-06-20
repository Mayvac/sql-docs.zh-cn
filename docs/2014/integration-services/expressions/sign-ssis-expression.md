---
title: SIGN（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 42b0e1d2c91bf7c66065fc8c5a3bcee03e8475c6
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966577"
---
# <a name="sign-ssis-expression"></a>SIGN（SSIS 表达式）
  返回数值表达式的符号：正号 (+1)、负号 (-1) 或零 (0)。  
  
## <a name="syntax"></a>语法  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>参数  
 *numeric_expression*  
 是一个有效的有符号数值表达式。 有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>结果类型  
 DT_I4  
  
## <a name="remarks"></a>备注  
 如果该参数为空，SIGN 返回的结果为空。  
  
## <a name="expression-examples"></a>表达式示例  
 此示例返回数值的符号。 返回结果为 -1。  
  
```  
SIGN(-123.45)  
```  
  
 此示例返回从 **DealerPrice** 列减去 **StandardCost** 列的结果的符号。  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>另请参阅  
 [函数（SSIS 表达式）](functions-ssis-expression.md)  
  
  
