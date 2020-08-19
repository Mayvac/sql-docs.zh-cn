---
description: SQLGetInfo（Visual FoxPro ODBC 驱动程序）
title: SQLGetInfo (Visual FoxPro ODBC 驱动程序) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: fbc39e3d-67d9-4331-bf5f-76dbd74c4c45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 370661a9a0ade5c5159f93a9af37c17b675032c3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421671"
---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo（Visual FoxPro ODBC 驱动程序）
> [!NOTE]  
>  本主题包含特定于 Visual FoxPro ODBC 驱动程序的信息。 有关此函数的常规信息，请参阅 [ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)中的相应主题。  
  
 支持：完全  
  
 ODBC API 一致性：级别1  
  
 返回有关 Visual FoxPro ODBC 驱动程序的常规信息以及与连接句柄 *hdbc*关联的数据源。 以下列表显示了 Visual FoxPro ODBC 驱动程序为每个 *fInfoType* 参数返回的值，以及有关返回值的注释。  
  
 有关详细信息，请参阅*ODBC 程序员参考*中的[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md) 。  
  
## <a name="a"></a>A  
 SQL_ACCESSIBLE_PROCEDURES 返回 "N"。  
  
 SQL_ACCESSIBLE_TABLES 返回 "Y"。  
  
 SQL_ACTIVE_CONNECTIONS 返回0。  
  
 SQL_ACTIVE_STATEMENTS 返回0。  
  
 SQL_ALTER_TABLE 返回 SQL_AT_ADD_COLUMN 或 SQL_AT_DROP_COLUMN。  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCE 返回 SQL_BP_SCROLL。  
  
## <a name="c"></a>C  
 SQL_COLUMN_ALIAS 返回 "Y"。  
  
 SQL_CONCAT_NULL_BEHAVIOR 返回 SQL_CB_NULL。  
  
 SQL_CONVERT_BIGINT 返回0。 Visual FoxPro ODBC 驱动程序不支持 *BigInt*。  
  
 SQL_CONVERT_BINARY 返回0。  
  
 SQL_CONVERT_BIT 返回0。  
  
 SQL_CONVERT_CHAR 返回0。  
  
 SQL_CONVERT_DATE 返回0。  
  
 SQL_CONVERT_DECIMAL 返回0。  
  
 SQL_CONVERT_DOUBLE 返回0。  
  
 SQL_CONVERT_FLOAT 返回0。  
  
 SQL_CONVERT_INTEGER 返回0。  
  
 SQL_CONVERT_LONGVARBINARY 返回0。  
  
 SQL_CONVERT_LONGVARCHAR 返回0。  
  
 SQL_CONVERT_NUMERIC 返回0。  
  
 SQL_CONVERT_REAL 返回0。  
  
 SQL_CONVERT_SMALLINT 返回0。  
  
 SQL_CONVERT_TIME 返回0。  
  
 SQL_CONVERT_TIMESTAMP 返回0。  
  
 SQL_CONVERT_TINYINT 返回0。  
  
 SQL_CONVERT_VARBINARY 返回0。  
  
 SQL_CONVERT_VARCHAR 返回0。  
  
 SQL_CONVERT_FUNCTIONS 返回0。  
  
 SQL_CORRELATION_NAME 返回 SQL_CN_ANY。  
  
 SQL_CURSOR_COMMIT_BEHAVIOR 返回 SQL_CB_PRESERVE。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR 返回 SQL_CB_PRESERVE。  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAME 返回作为 DSN 传递到 [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)或 [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)的值。如果未指定任何 DSN，则返回空字符串。  
  
 SQL_DATA_SOURCE_READ_ONLY 返回 "N"。  
  
 如果数据源是 [数据库](../../odbc/microsoft/visual-foxpro-terminology.md)，SQL_DATABASE_NAME 将返回当前数据库的完整 UNC 路径。 如果数据源连接到 [表](../../odbc/microsoft/visual-foxpro-terminology.md)的某个目录，则该函数将返回该目录的路径。  
  
 SQL_DBMS_NAME 返回 "Visual FoxPro"。  
  
 SQL_DBMS_VER 将返回 "03.00.0000"。  
  
 SQL_DEFAULT_TXN_ISOLATION 返回 SQL_TXN_READ_COMMITTED。 不可能进行脏读，但不可重复读取和幻像是可能的。  
  
 SQL_DRIVER_HDBC 由驱动程序管理器实现。  
  
 SQL_DRIVER_HENV 由驱动程序管理器实现。  
  
 SQL_DRIVER_HLIB 由驱动程序管理器实现。  
  
 SQL_DRIVER_HSTMT 由驱动程序管理器实现。  
  
 SQL_DRIVER_NAME 返回 "vfpodbc.dll"。  
  
 SQL_DRIVER_ODBC_VER 返回 "02.50" (SQL_SPEC_MAJOR SQL_SPEC_MINOR) 。  
  
 SQL_DRIVER_VER 将返回 "01.00.0000"。  
  
## <a name="e"></a>E  
 SQL_EXPRESSIONS_IN_ORDERBY 返回 "N"。  
  
## <a name="f"></a>F  
 SQL_FETCH_DIRECTION 返回：  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK。  
  
 对于数据库 ( dbc 文件) ，SQL_FILE_USAGE 返回 SQL_FILE_QUALIFIER，并为免费表 ( 文件) 数据源。  
  
## <a name="g-h"></a>G-H  
 SQL_GETDATA_EXENSIONS 返回：  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BY 返回 SQL_GB_NO_RELATION。  
  
## <a name="i-j"></a>I-J  
 SQL_IDENTIFIER_CASE 返回 SQL_IC_MIXED。  
  
 SQL_IDENTIFIER_QUOTE_CHAR 返回 ""。  
  
## <a name="k"></a>K  
 SQL_KEYWORDS 返回 ""。  
  
## <a name="l"></a>L  
 SQL_LIKE_ESCAPE_CLAUSE 返回 "N"。  
  
 SQL_LOCK_TYPES 返回 SQL_LCK_NO_CHANGE。  
  
## <a name="m"></a>M  
 SQL_MAX_BINARY_LITERAL_LEN 返回0。  
  
 SQL_MAX_CHAR_LITERAL_LEN 返回254。  
  
 SQL_MAX_COLUMN_NAME_LEN 返回128。  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY 返回16。  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY 返回16。  
  
 SQL_MAX_COLUMNS_IN_INDEX 返回0。  
  
 SQL_MAX_COLUMNS_IN_SELECT 返回254。  
  
 SQL_MAX_COLUMNS_IN_TABLE 返回254。  
  
 SQL_MAX_CURSOR_NAME_LEN 返回254。  
  
 SQL_MAX_INDEX_SIZE 返回0。  
  
 SQL_MAX_OWNER_NAME_LEN 返回0。  
  
 SQL_MAX_PROCEDURE_NAME_LEN 返回0。 Visual FoxPro ODBC 驱动程序不允许直接访问 Visual FoxPro 存储过程。  
  
 SQL_MAX_QUALIFIER_NAME_LEN 返回最大操作系统路径长度。  
  
 SQL_MAX_ROW_SIZE 返回 254 ^ 2。  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG 返回 "N"。  
  
 SQL_MAX_STATEMENT_LEN 返回8192。  
  
 SQL_MAX_TABLE_NAME_LEN 返回128。  
  
 SQL_MAX_TABLES_IN_SELECT 返回16。  
  
 SQL_MAX_USER_NAME_LEN 返回0。  
  
 SQL_MULT_RESULT_SETS 返回 "Y"。  
  
 SQL_MULTIPLE_ACTIVE_TXN 返回 "Y"。 多个连接可以同时打开多个事务。  
  
## <a name="n"></a>N  
 SQL_NEED_LONG_DATA_LEN 返回 "N"。  
  
 SQL_NON_NULLABLE_COLUMNS 返回 SQL_NNC_NON_NULL。  
  
 SQL_NULL_COLLATION 返回 SQL_NC_LOW。  
  
 SQL_NUMERIC_FUNCTIONS 返回除 SQL_FN_NUM_POWER 之外的所有函数，Visual FoxPro ODBC 驱动程序不支持此功能。 支持以下函数：  
  
-   SQL_FN_NUM_ABS  
  
-   SQL_FN_NUM_ACOS  
  
-   SQL_FN_NUM_ASIN  
  
-   SQL_FN_NUM_ATAN  
  
-   SQL_FN_NUM_ATAN2  
  
-   SQL_FN_NUM_CELING  
  
-   SQL_FN_NUM_COS  
  
-   SQL_FN_NUM_COT  
  
-   SQL_FN_NUM_DEGREES  
  
-   SQL_FN_NUM_EXP  
  
-   SQL_FN_NUM_FLOOR  
  
-   SQL_FN_NUM_LOG  
  
-   SQL_FN_NUM_LOG10  
  
-   SQL_FN_NUM_MOD  
  
-   SQL_FN_NUM_PI  
  
-   SQL_FN_NUM_RADIANS  
  
-   SQL_FN_NUM_RAND  
  
-   SQL_FN_NUM_ROUND  
  
-   SQL_FN_NUM_SIGN  
  
-   SQL_FN_NUM_SIN  
  
-   SQL_FN_NUM_SQRT  
  
-   SQL_FN_NUM_TAN  
  
## <a name="o"></a>O  
 SQL_ODBC_API_CONFORMANCE 返回 SQL_OAC_LEVEL1。  
  
 SQL_ODBC_SAG_CLI_CONFORMANCE 返回 SQL_OSCC_COMPLIANT。  
  
 SQL_ODBC_SQL_CONFORMANCE 返回 SQL_OSC_MINIMUM。 支持最小 SQL 语法。  
  
 SQL_ODBC_SQL_OPT_IEF 返回 "N"。  
  
 SQL_ODBC_VER 由驱动程序管理器实现。  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT 返回 "N"。  
  
 SQL_OUTER_JOINS 返回 "N"。  
  
 SQL_OWNER_TERM 返回 ""。 Visual FoxPro ODBC 驱动程序不支持其对象的所有者。  
  
 SQL_OWNER_USAGE 返回0。 Visual FoxPro ODBC 驱动程序不支持其对象的所有者。  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONS 返回 SQL_POS_POSITION。  
  
 SQL_POSITIONED_STATEMENTS 返回0。  
  
 SQL_PROCEDURE_TERM 返回 ""。  
  
 SQL_PROCEDURES 返回 "N"。  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATION 返回 SQL_QL_START。  
  
 SQL_QUALIFIER_NAME_SEPARATOR 返回 "！" 或 " \\ "。 对于连接到 [数据库](../../odbc/microsoft/visual-foxpro-terminology.md)的数据源，数据库和表之间的分隔符为 "！"; \\ 对于作为 [自由表](../../odbc/microsoft/visual-foxpro-terminology.md)目录的数据源，则为 ""。  
  
 SQL_QUALIFIER_TERM 返回 "database" 或 "directory"。 限定符是连接到 [数据库](../../odbc/microsoft/visual-foxpro-terminology.md)的数据源的 "数据库"，而 "目录" 用于作为 [自由表](../../odbc/microsoft/visual-foxpro-terminology.md)目录的数据源。  
  
 SQL_QUALIFIER_USAGE 不支持 SQL_QU_PRIVILEGE_DEFINITION;它将返回 SQL_QU_DML_STATEMENT 或 SQL_QU_TABLE_DEFINITION。  
  
 SQL_QUOTED_IDENTIFIER_CASE 返回 SQL_IC_MIXED。  
  
## <a name="r"></a>R  
 SQL_ROW_UPDATES 返回 "N"。 Visual FoxPro ODBC 驱动程序仅支持静态和正向游标。  
  
## <a name="s"></a>S  
 SQL_SCROLL_CONCURRENCY 返回 SQL_SCCO_READ_ONLY。  
  
 SQL_SCROLL_OPTIONS 返回 SQL_SO_STATIC 或 SQL_SO_READONLY。  
  
 SQL_SEARCH_PATTERN_ESCAPE 返回 " \\ "。  
  
 SQL_SERVER_NAME 返回 ""。  
  
 SQL_SPECIAL_CHARACTERS 返回 "~ @ # $% ^"。  
  
 SQL_STATIC_SENSITIVITY 返回0。 Visual FoxPro ODBC 驱动程序不支持位置更新。  
  
 SQL_STRING_FUNCTIONS 不支持 SQL_FN_STR_INSERT、SQL_FN_STR_LOCATE、SQL_FN_STR_LOCATE_2 或 SQL_FN_STR_SOUNDEX。  
  
 将返回：  
  
-   SQL_FN_STR_ASCII  
  
-   SQL_FN_STR_CHAR  
  
-   SQL_FN_STR_CONCAT  
  
-   SQL_FN_STR_DIFFERENCE  
  
-   SQL_FN_STR_LCASE  
  
-   SQL_FN_STR_LEFT  
  
-   SQL_FN_STR_LENGTH  
  
-   SQL_FN_STR_LTRIM  
  
-   SQL_FN_STR_REPEAT  
  
-   SQL_FN_STR_REPLACE  
  
-   SQL_FN_STR_RIGHT  
  
-   SQL_FN_STR_RTRIM  
  
-   SQL_FN_STR_SUBSTRING  
  
-   SQL_FN_STR_UCASE  
  
-   SQL_FN_STR_SPACE。  
  
 SQL_SUBQUERIES 返回：  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED。  
  
 SQL_SYSTEM_FUNCTIONS 返回：  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 但不能：  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERM 返回 "TABLE"。  
  
 SQL_TIMEDATE_ADD_INTERVALS 返回：  
  
-   SQL_FN_TSI_ 秒  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 但不能：  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 SQL_TIMEDATE_DIFF_INTERVALS 返回：  
  
-   SQL_FN_TSI_ 秒  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_TIMEDATE_FUNCTIONS 不支持 SQL_FN_TD_QUARTER、SQL_FN_TD_TIMESTAMPADD、SQL_FN_TD_DAYOFYEAR 或 SQL_FN_TD_WEEK。  
  
 将返回：  
  
-   SQL_FN_TD_CURDATE  
  
-   SQL_FN_TD_CURTIME  
  
-   SQL_FN_TD_DAYNAME  
  
-   SQL_FN_TD_DAYOFMONTH  
  
-   SQL_FN_TD_DAYOFWEEK  
  
-   SQL_FN_TD_HOUR  
  
-   SQL_FN_TD_MINUTE  
  
-   SQL_FN_TD_MONTH  
  
-   SQL_FN_TD_MONTHNAME  
  
-   SQL_FN_TD_NOW  
  
-   SQL_FN_TD_SECOND  
  
-   SQL_FN_TD_TIMESTAMPDIFF  
  
-   SQL_FN_TD_YEAR。  
  
 SQL_TXN_CAPABLE 返回 SQL_TC_DML。  
  
 SQL_TXN_ISOLATION_OPTION 返回 SQL_TXN_READ_COMMITTED。  
  
## <a name="u-z"></a>U-Z  
 SQL_UNION 返回 SQL_U_UNION 或 SQL_U_UNION_ALL。  
  
 SQL_USER_NAME 返回 \<blank> 。
