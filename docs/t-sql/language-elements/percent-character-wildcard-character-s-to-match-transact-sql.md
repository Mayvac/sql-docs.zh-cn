---
title: 通配符搜索 (%)
ms.custom: seo-lt-2019
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '%'
- '%_TSQL'
- wildcard
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], wildcards
- '% (wildcard - character(s) to match)'
- matching conditions [SQL Server]
- wildcard characters [SQL Server]
- characters [SQL Server], wildcard
ms.assetid: d4cbc1a9-37e1-4101-97fb-e6ac30c1223e
author: rothja
ms.author: jroth
ms.openlocfilehash: 156ee6ad9860838b1d750f523cd936cbce15e0fb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736327"
---
# <a name="percent-character-wildcard---characters-to-match-transact-sql"></a>百分比字符（通配符 - 需匹配的字符）(Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  匹配包含零个或多个字符的任意字符串。 此通配符既可以用作前缀也可以用作后缀。  
  
## <a name="examples"></a>示例  
 下面的示例返回 `Person` 的 `AdventureWorks2012` 表中所有以 `Dan` 开头的人员名字。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Dan%';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [运算符 (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [表达式 (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
 [[ ]（通配符 - 需匹配的字符）](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
  [[^]（通配符 - 无需匹配的字符）](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [_（通配符 - 匹配一个字符）](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
