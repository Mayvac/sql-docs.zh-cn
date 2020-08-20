---
description: ODBC 函数和游标库
title: ODBC 函数和游标库 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c609d0fb-787a-4b39-9673-332d411b3d63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6aa156a1fe4a6ebecb33b0c0401ae116226a80e9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466122"
---
# <a name="odbc-functions-and-the-cursor-library"></a>ODBC 函数和游标库
> [!IMPORTANT]  
>  此功能将在 Windows 的将来版本中删除。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 为连接启用 ODBC 游标库时，驱动程序管理器将调用游标库中的函数，而不是在驱动程序中。 游标库执行该函数或在指定的驱动程序中调用它。  
  
 本部分包含以下主题。  
  
-   [由游标库执行的 ODBC 函数](../../../odbc/reference/appendixes/odbc-functions-executed-by-the-cursor-library.md)  
  
-   [不是由游标库执行的 ODBC 函数](../../../odbc/reference/appendixes/odbc-functions-not-executed-by-the-cursor-library.md)  
  
-   [SQLBindCol（游标库）](../../../odbc/reference/appendixes/sqlbindcol-cursor-library.md)  
  
-   [SQLBindParameter（游标库）](../../../odbc/reference/appendixes/sqlbindparameter-cursor-library.md)  
  
-   [SQLBulkOperations (游标库) ](../../../odbc/reference/appendixes/sqlbulkoperations-and-the-cursor-library.md)  
  
-   [SQLCloseCursor (游标库) ](../../../odbc/reference/appendixes/sqlclosecursor-odbc.md)  
  
-   [SQLEndTran（游标库）](../../../odbc/reference/appendixes/sqlendtran-cursor-library.md)  
  
-   [SQLExtendedFetch（游标库）](../../../odbc/reference/appendixes/sqlextendedfetch-cursor-library.md)  
  
-   [SQLFetch（游标库）](../../../odbc/reference/appendixes/sqlfetch-cursor-library.md)  
  
-   [SQLFetchScroll（游标库）](../../../odbc/reference/appendixes/sqlfetchscroll-cursor-library.md)  
  
-   [SQLFreeStmt（游标库）](../../../odbc/reference/appendixes/sqlfreestmt-cursor-library.md)  
  
-   [SQLGetData（游标库）](../../../odbc/reference/appendixes/sqlgetdata-cursor-library.md)  
  
-   [SQLGetDescField 和 SQLGetDescRec（游标库）](../../../odbc/reference/appendixes/sqlgetdescfield-and-sqlgetdescrec-cursor-library.md)  
  
-   [SQLGetFunctions（游标库）](../../../odbc/reference/appendixes/sqlgetfunctions-cursor-library.md)  
  
-   [SQLGetInfo（游标库）](../../../odbc/reference/appendixes/sqlgetinfo-cursor-library.md)  
  
-   [SQLGetStmtAttr（游标库）](../../../odbc/reference/appendixes/sqlgetstmtattr-cursor-library.md)  
  
-   [SQLGetStmtOption（游标库）](../../../odbc/reference/appendixes/sqlgetstmtoption-cursor-library.md)  
  
-   [SQLNativeSql（游标库）](../../../odbc/reference/appendixes/sqlnativesql-cursor-library.md)  
  
-   [SQLRowCount（游标库）](../../../odbc/reference/appendixes/sqlrowcount-cursor-library.md)  
  
-   [SQLSetConnectAttr（游标库）](../../../odbc/reference/appendixes/sqlsetconnectattr-cursor-library.md)  
  
-   [SQLSetDescField 和 SQLSetDescRec（游标库）](../../../odbc/reference/appendixes/sqlsetdescfield-and-sqlsetdescrec-cursor-library.md)  
  
-   [SQLSetEnvAttr (游标库) ](../../../odbc/reference/appendixes/sqlsetenvattr-and-the-cursor-library.md)  
  
-   [SQLSetPos（游标库）](../../../odbc/reference/appendixes/sqlsetpos-cursor-library.md)  
  
-   [SQLSetScrollOptions（游标库）](../../../odbc/reference/appendixes/sqlsetscrolloptions-cursor-library.md)  
  
-   [SQLSetStmtAttr（游标库）](../../../odbc/reference/appendixes/sqlsetstmtattr-cursor-library.md)
