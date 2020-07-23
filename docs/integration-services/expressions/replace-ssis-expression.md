---
title: REPLACE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8ef16c9c83419d6b404affc49e7200a739ab65f7
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919049"
---
# <a name="replace-ssis-expression"></a>REPLACE（SSIS 表达式）

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  将表达式中的一个字符串替换为另一个字符串或空字符串后，返回一个字符表达式。  
  
> [!NOTE]  
>  REPLACE 函数经常使用长字符串。 可以适当处理截断的结果，否则会导致警告或错误。 有关详细信息，请参阅[语法 (SSIS)](../../integration-services/expressions/syntax-ssis.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a>参数  
 *character_expression*  
 是函数要搜索的有效字符表达式。  
  
 *searchstring*  
 是函数尝试定位的有效字符表达式。  
  
 *replacementstring*  
 是用作替换表达式的有效字符表达式。  
  
## <a name="result-types"></a>结果类型  
 DT_WSTR  
  
## <a name="remarks"></a>备注  
 *searchstring* 的长度一定不能为零。  
  
 *replacementstring* 的长度可以为零。  
  
 *searchstring* 和 *replacementstring* 参数可以使用变量和列。  
  
 REPLACE 只可用于 DT_WSTR 数据类型。 如果*character_expression1、character_expression2* 和 *character_expression3* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它们在 REPLACE 执行操作前隐式转换为 DT_WSTR 数据类型。 其他数据类型必须显式转换为 DT_WSTR 数据类型。 有关详细信息，请参阅[转换（SSIS 表达式）](../../integration-services/expressions/cast-ssis-expression.md)。  
  
 如果任何参数值为空，则 REPLACE 返回的结果为空。  
  
## <a name="expression-examples"></a>表达式示例  
 此示例使用一个字符串文字。 返回结果为“All Terrain Bike”。  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 此示例删除 **Product** 列中的字符串“Bike”。  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 此示例替换 **DaysToManufacture** 列中的值。 该列具有整数数据类型，且表达式包含将 **DaysToManufacture** 转换为 DT_WSTR 数据类型的转换。  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a>另请参阅  
 [SUBSTRING（SSIS 表达式）](../../integration-services/expressions/substring-ssis-expression.md)   
 [函数（SSIS 表达式）](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
