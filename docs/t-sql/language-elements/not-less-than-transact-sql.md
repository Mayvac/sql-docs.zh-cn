---
title: '!&lt;（不小于）(Transact SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '!<'
- Not Less
- '!<_TSQL'
- Not Less Than
- Less Than
dev_langs:
- TSQL
helpviewer_keywords:
- '!< (not less than)'
- not less than operator (!<)
ms.assetid: ecbb598e-58a2-4b6c-90b4-3ad5bdfcae39
author: rothja
ms.author: jroth
ms.openlocfilehash: efb3b0d7a6422575df0d13bd15dccdf75834707d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85706279"
---
# <a name="lt-not-less-than-transact-sql"></a>!&lt;（不小于）(Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  比较两个表达式（比较运算符）。 当比较非空表达式时，如果左边操作数的值不小于右边操作数的值，则结果为 TRUE；否则结果为 FALSE。 如果任何一个操作数为 NULL 或两个都为 NULL，则请参阅主题 [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
expression !< expression  
```  
  
## <a name="arguments"></a>参数  
 *expression*  
 为任意有效的[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。 两个表达式都必须包含可隐式转换的数据类型。 转换方式取决于[数据类型优先级](../../t-sql/data-types/data-type-precedence-transact-sql.md)的相关规则。  
  
## <a name="result-types"></a>结果类型  
 **布尔值**  
  
## <a name="see-also"></a>另请参阅  
 [数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [运算符 (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
