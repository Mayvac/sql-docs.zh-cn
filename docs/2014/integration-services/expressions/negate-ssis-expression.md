---
title: '- （负号）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ac803cb797644d47c6bc5ee4fcee99e14ba88a4c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969187"
---
# <a name="--negate-ssis-expression"></a>-（负号）（SSIS 表达式）
  对一个数值表达式求反。  
  
## <a name="syntax"></a>语法  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>参数  
 *numeric_expression*  
 任何数值数据类型的有效表达式。 仅支持有符号数值数据类型。 有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>结果类型  
 返回 *numeric_expression*的数据类型。  
  
## <a name="expression-examples"></a>表达式示例  
 以下示例对 **Counter** 变量的值求反，并加上数值 50。  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>另请参阅  
 [运算符优先级和结合性](operator-precedence-and-associativity.md)   
 [运算符（SSIS 表达式）](operators-ssis-expression.md)  
  
  
