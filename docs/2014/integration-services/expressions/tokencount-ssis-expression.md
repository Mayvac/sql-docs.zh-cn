---
title: TOKENCOUNT（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: df34c21e200f5a9f4a9242a3280913acf14adf76
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968968"
---
# <a name="tokencount-ssis-expression"></a>TOKENCOUNT（SSIS 表达式）
  返回包含指定分隔符分隔的标记的字符串中的标记数目。  
  
## <a name="syntax"></a>语法  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a>参数  
 *character_expression*  
 包含分隔符分隔的标记的字符串。  
  
 *delimiter_string*  
 包含分隔符字符的字符串。 例如，”; ,”包含三个分隔符字符，即一个分号、一个空白空间和一个逗号。  
  
## <a name="result-types"></a>结果类型  
 DT_I4  
  
## <a name="remarks"></a>备注  
 下面的备注适用于 TOKEN 函数：  
  
-   分隔符字符串可以包含一个或多个分隔符字符。  
  
-   前导分隔符将被跳过。  
  
-   TOKENCOUNT 只可用于 DT_WSTR 数据类型。 如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 TOKEN 执行操作前将隐式转换为 DT_WSTR 数据类型。 其他数据类型必须显式转换为 DT_WSTR 数据类型。  
  
-   如果 character_expression 为 Null，TOKENCOUNT 将返回 0（零）。  
  
-   您可以使用变量和列作为此表达式的参数。  
  
## <a name="expression-examples"></a>表达式示例  
 在下面的示例中，TOKENCOUNT 函数返回 3，因为该字符串包含三个标记：“01”、“12”、“2011”。  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 在下面的示例中，TOKENCOUNT 函数返回 4，因为存在四个标记（“a”、“little”、“white”、“dog”）。  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 在下面的示例中，TOKENCOUNT 函数返回 1。 该函数对分隔符的输入字符串进行分析，因为该字符串中没有任何内容，所以它只是将整个字符串作为第一个标记添加。  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 在下面的示例中，TOKENCOUNT 函数返回 4。 此示例中的分隔符字符串包含 5 个分隔符。 输入字符串包含 4 个标记：“a”、“little”、“white”、“dog”。  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 在下面的示例中，TOKENCOUNT 函数返回 4。 它将忽略所有前导空格字符。  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a>另请参阅  
 [函数（SSIS 表达式）](functions-ssis-expression.md)  
  
  
