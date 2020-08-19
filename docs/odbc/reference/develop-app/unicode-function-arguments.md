---
description: Unicode 函数自变量
title: Unicode 函数参数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d2d59cad60855c670f7c7e2b189ad3c97a3027b9
ms.sourcegitcommit: 19ae05bc69edce1e3b3d621d7fdd45ea5f74969d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88564035"
---
# <a name="unicode-function-arguments"></a>Unicode 函数自变量
ODBC 3.5 (或更高版本) 驱动程序管理器支持在其参数中接受指向字符串或 SQLPOINTER 的指针的所有函数的 ANSI 和 Unicode 版本。 Unicode 函数作为函数实现， (后缀为 *W*) ，而不是宏。 ANSI 函数 (在) 的后缀与当前 ODBC API 函数相同的情况下，可以使用或 *不使用后缀* 调用。  
  
## <a name="remarks"></a>备注  
 对于始终返回字符串或长度参数的 Unicode 函数，这些参数将作为字符计数传递。 对于返回服务器数据的长度信息的函数，将以字符数描述显示大小和精度。 如果数据) 的数据 (传输大小可能引用 string 或非字符串数据，则会在八位字节长度中描述长度。 例如， **SQLGetInfoW** 仍采用长度作为字节计数，但 **SQLExecDirectW** 将使用字符数。  
  
 字符计数指的是 ANSI 函数 (八进制数) 的字节数，以及 UNICODE 函数)  (16 位字的数目。 具体而言，双字节字符序列 (DBCS) 或多字节字符序列 (MBCS) 可以由多个字节组成。 UTF-16 Unicode 字符序列可以由多个 WCHARs 组成。  
  
 下面列出了同时支持 Unicode (W) 和 ANSI () 版本的 ODBC API 函数：  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagRec**|  
|**SQLColAttribute**|**SQLGetInfo**|  
|**SQLColAttributes**|**SQLGetStmtAttr**|  
|**SQLColumnPrivileges**|**SQLGetTypeInfo**|  
|**SQLColumns**|**SQLNativeSql**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 下面列出了 ODBC 安装程序和 ODBC 转换器函数，它们支持 Unicode (W) 和 ANSI () 版本：  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  弃用的函数具有 Unicode 到 ANSI 的映射支持，因为 ODBC 2.x 驱动程序管理器支持使用 UNICODE **#define**重新*编译 ODBC 2.x* *应用程序。*  
  
 本部分包含以下主题。  
  
-   [Unicode 应用程序](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Unicode 驱动程序](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [驱动程序管理器中的函数映射](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
