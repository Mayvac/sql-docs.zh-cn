---
title: LOWER（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55474bb9c52acea8c6c3fe091874f46f4e7c61de
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437244"
---
# <a name="lower-ssis-expression"></a>LOWER（SSIS 表达式）
  返回将大写字符转换为小写字符后得到的字符表达式。  
  
## <a name="syntax"></a>语法  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a>参数  
 *character_expression*  
 是要转换为小写字符的字符表达式。  
  
## <a name="result-types"></a>结果类型  
 DT_WSTR  
  
## <a name="remarks"></a>备注  
 LOWER 只可用于 DT_WSTR 数据类型。 如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 LOWER 执行操作前隐式转换为 DT_WSTR 数据类型。 其他数据类型必须显式转换为 DT_WSTR 数据类型。 有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。  
  
 如果该参数为空，则 LOWER 返回的结果为空。  
  
## <a name="expression-examples"></a>表达式示例  
 此示例将字符串文字转换为小写字符。 返回结果为“new york”。  
  
```  
LOWER("New York")  
```  
  
 此示例将 **Color** 输入列中除第一个字符外的所有字符转换为小写字符。 如果 Color 为 YELLOW，则返回结果为“Yellow”。 有关详细信息，请参阅 [SUBSTRING（SSIS 表达式）](substring-ssis-expression.md)。  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 此示例将 **CityName** 变量中的值转换为小写字符。  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a>另请参阅  
 [UPPER（SSIS 表达式）](upper-ssis-expression.md)   
 [函数（SSIS 表达式）](functions-ssis-expression.md)  
  
  
