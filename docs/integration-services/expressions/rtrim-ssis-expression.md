---
title: RTRIM（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c58da8b33c431f62f4567379beca8b5b12beea4f
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914939"
---
# <a name="rtrim-ssis-expression"></a>RTRIM（SSIS 表达式）

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  返回删除了尾随空格的字符表达式。  
  
> [!NOTE]  
>  RTRIM 不删除空格字符，如制表符或换行符字符。 Unicode 针对许多不同类型的空格提供了码位，但是该函数仅识别 Unicode 码位 0x0020。 双字节字符集 (DBCS) 字符串转换为 Unicode 时，它们可能包含 0x0020 之外的空格字符，而该函数无法删除此类空格。 若要删除所有类型的空格，您可以在基于脚本组件运行的脚本中使用 Microsoft Visual Basic .NET RTrim 方法。  
  
## <a name="syntax"></a>语法  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a>参数  
 *character_expression*  
 要从中删除空格的字符表达式。  
  
## <a name="result-types"></a>结果类型  
 DT_WSTR  
  
## <a name="remarks"></a>备注  
 RTRIM 只用于 DT_WSTR 数据类型。 如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 RTRIM 执行操作前隐式转换为 DT_WSTR 数据类型。 其他数据类型必须显式转换为 DT_WSTR 数据类型。 有关详细信息，请参阅 [Integration Services 数据类型](../../integration-services/data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](../../integration-services/expressions/cast-ssis-expression.md)。  
  
 如果该参数为空，则 RTRIM 返回的结果为空。  
  
## <a name="expression-examples"></a>表达式示例  
 此示例删除字符串文字中的尾随空格。 返回结果为“Hello”。  
  
```  
RTRIM("Hello   ")  
```  
  
 此示例删除 **FirstName** 和 **LastName** 列的串联中的尾随空格。  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 此示例删除 **FirstName** 变量中的尾随空格。  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>另请参阅  
 [LTRIM（SSIS 表达式）](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [TRIM（SSIS 表达式）](../../integration-services/expressions/trim-ssis-expression.md)   
 [函数（SSIS 表达式）](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
