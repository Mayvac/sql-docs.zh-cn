---
description: 语句的批处理
title: 语句的批处理 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9d0842a0cc4c38c25af9dc3bdf334f846993f480
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867306"
---
# <a name="batches-of-statements"></a>语句的批处理
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  一批 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句包含两个或多个语句，这些语句由分号分隔 (; ) ，内置于传递到 **SQLExecDirect** 或 [SQLPrepare 函数](../../../odbc/reference/syntax/sqlprepare-function.md)的单个字符串。 例如：  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 批处理通常可减少网络流量，因而比单个提交语句效率更高。 完成当前结果集后，使用 [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) 定位到下一个结果集。  
  
 当 ODBC 游标属性设置为行集大小为 1 的只进只读游标的默认值时，始终可以使用批处理。  
  
 如果在针对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用服务器游标时执行批处理，则服务器游标会隐式转换为默认结果集。 **SQLExecDirect** 或 **SQLExecute** 返回 SQL_SUCCESS_WITH_INFO，对 **SQLGetDiagRec** 的调用返回：  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>另请参阅  
 [&#40;ODBC&#41;执行语句 ](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
