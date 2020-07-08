---
title: GETANSINULL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GETANSINULL
- GETANSINULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], default
- GETANSINULL function
- default nullability
- database nullability [SQL Server]
ms.assetid: 189399e4-428d-4902-b3a8-94f07fdefc6a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d67d058e089ce00308382d0b52ecc102b062cba2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85631594"
---
# <a name="getansinull-transact-sql"></a>GETANSINULL (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  返回此会话的数据库的默认为 Null 性。  
  
 ![文章链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
GETANSINULL ( [ 'database' ] )  
```  
  
## <a name="arguments"></a>参数  
 'database'   
 为其返回为空性信息的数据库的名称。 *database 可以是 char  ，也可以是 nchar  。 如果是 char，则数据库隐式转换为 nchar    。  
  
## <a name="return-types"></a>返回类型  
 **int**  
  
## <a name="remarks"></a>备注  
如果数据库的为 Null 性允许 NULL 值，GETANSINULL 返回 1。 此返回值还要求不显式定义列或数据类型为 Null 性。 ANSI NULL 默认值为 1。 
  
 若要启用 ANSI NULL 默认行为，则必须设置下列条件之一:  
  
-   ALTER DATABASE database_name SET ANSI_NULL_DEFAULT ON   
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET ANSI_NULL_DFLT_OFF OFF  
  
## <a name="examples"></a>示例  
 以下示例将返回 `AdventureWorks2012` 数据库的默认为空性。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT GETANSINULL('AdventureWorks2012')  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------  
1  

(1 row(s) affected)
 ```  
  
## <a name="see-also"></a>另请参阅  
 [系统函数 (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
