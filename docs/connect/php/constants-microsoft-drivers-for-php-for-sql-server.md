---
title: 常量 (Microsoft Drivers for PHP for SQL Server)
description: 了解在 Microsoft SQLSRV 和 PDO_SQLSRV Drivers for PHP for SQL Server 中定义的常量。
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- constants
ms.assetid: 9727c944-b645-48d6-9012-18dbde35ee3c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 771a14e8705af72f57571503c2dba9012c2e9879
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435250"
---
# <a name="constants-microsoft-drivers-for-php-for-sql-server"></a>常量 (Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

本主题将讨论 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]定义的常量。  
  
## <a name="pdo_sqlsrv-driver-constants"></a>PDO_SQLSRV 驱动程序常量  
[PDO 网站](https://php.net/manual/book.pdo.php) 上列出的常量在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]中有效。  
  
下面介绍 PDO_SQLSRV 驱动程序中的 Microsoft 特定常量。  
  
### <a name="transaction-isolation-level-constants"></a>事务隔离级别常量  
可与 **PDO::__construct** 结合使用的 [TransactionIsolation](../../connect/php/pdo-construct.md)键接受以下常量之一：  
  
-   PDO::SQLSRV_TXN_READ_UNCOMMITTED  
  
-   PDO::SQLSRV_TXN_READ_COMMITTED  
  
-   PDO::SQLSRV_TXN_REPEATABLE_READ  
  
-   PDO::SQLSRV_TXN_SNAPSHOT  
  
-   PDO::SQLSRV_TXN_SERIALIZABLE  
  
有关 **TransactionIsolation** 键的详细信息，请参阅 [Connection Options](../../connect/php/connection-options.md)。  
  
### <a name="encoding-constants"></a>编码常量  
PDO::SQLSRV_ATTR_ENCODING 属性可传递给 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md)、[PDO::setAttribute](../../connect/php/pdo-setattribute.md)、[PDO::prepare](../../connect/php/pdo-prepare.md)、[PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) 和 [PDOStatement::bindParam](../../connect/php/pdostatement-bindparam.md)。  
  
传递给 PDO::SQLSRV_ATTR_ENCODING 的可用值如下  
  
|PDO_SQLSRV 驱动程序常量|说明|  
|-------------------------------|---------------|  
|PDO::SQLSRV_ENCODING_BINARY|数据是来自服务器的原始字节流，无需执行编码或转换。<br /><br />对 PDO::setAttribute 无效。|  
|PDO::SQLSRV_ENCODING_SYSTEM|数据是 8 位字符，该格式如在系统上设置的 Windows 区域设置的代码页中所指定。 任何多字节字符或未映射到此代码页中的字符都会替换为单字节问号 (?) 字符。|  
|PDO::SQLSRV_ENCODING_UTF8|数据采用 UTF-8 编码。 这是默认编码。|  
|PDO::SQLSRV_ENCODING_DEFAULT|使用 PDO::SQLSRV_ENCODING_SYSTEM（如果在连接过程中已指定）。<br /><br />使用连接的编码（如果已在准备语句中指定）。|  
  
### <a name="query-timeout"></a>查询超时  
PDO::SQLSRV_ATTR_QUERY_TIMEOUT 属性是任一非负整数，表示超时时间（以秒为单位）。 零 (0) 是默认值，表示无超时。  
  
可以使用 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md)、[PDO::setAttribute](../../connect/php/pdo-setattribute.md) 和 [PDO::prepare](../../connect/php/pdo-prepare.md) 指定 PDO::SQLSRV_ATTR_QUERY_TIMEOUT 属性。  
  
### <a name="direct-or-prepared-execution"></a>直接执行或已准备的执行  
可以使用 PDO::SQLSRV_ATTR_DIRECT_QUERY 属性来选择直接查询执行或已准备的语句执行。 可以使用 [PDO::prepare](../../connect/php/pdo-prepare.md) 或 [PDO::setAttribute](../../connect/php/pdo-setattribute.md) 来设置 PDO::SQLSRV_ATTR_DIRECT_QUERY。 有关 PDO::SQLSRV_ATTR_DIRECT_QUERY 的详细信息，请参阅 [PDO_SQLSRV 驱动程序中的直接语句执行和已准备的语句执行](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)。  

### <a name="handling-numeric-fetches"></a>处理数值提取
可以使用 PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE 属性处理数值 SQL 类型（bit、integer、smallint、tinyint、float 和 real）列中的数值提取。 当 PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE 设置为 true，整数列的结果将表示为 int，而 SQL 浮点数和实数则表示为 float。 可以使用 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) 设置此属性。 

可以通过 PDO::SQLSRV_ATTR_FORMAT_DECIMALS 和 PDO::SQLSRV_ATTR_DECIMAL_PLACES 属性修改默认的十进制格式设置行为。 这些属性的行为与 SQLSRV 端的相应选项相同（FormatDecimals**** 和 DecimalPlaces****），只是输出参数不支持格式设置。 可以在连接或语句级别使用 [PDO::setAttribute](../../connect/php/pdo-setattribute.md) 或 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) 设置这些属性，但任何语句属性将重写相应的连接属性。 如需了解更多详情，请参阅[设置十进制字符串和 Money 值格式（PDO_SQLSRV 驱动程序）](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)。

### <a name="handling-date-and-time-fetches"></a>处理日期和时间提取

PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE 指定是否以 [PHP DateTime](http://php.net/manual/en/class.datetime.php) 对象形式检索日期和时间类型。 如果保留 false，默认行为是将它们作为字符串返回。 可以在连接或语句级别使用 [PDO::setAttribute](../../connect/php/pdo-setattribute.md) 或 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) 设置此属性，但语句属性将重写相应的连接属性。 有关详细信息，请参阅[操作说明：使用 PDO_SQLSRV 驱动程序检索日期和时间类型作为 PHP Datetime 对象](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)。

## <a name="sqlsrv-driver-constants"></a>SQLSRV 驱动程序常量  
以下部分将列出由 SQLSRV 驱动程序使用的常量。  
  
### <a name="err-constants"></a>ERR 常量  
下表列出了用于指定 [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) 是返回错误、警告还是二者都返回的常量。  
  
|值|说明|  
|---------|---------------|  
|SQLSRV_ERR_ALL|将返回在上次调用 **sqlsrv** 函数时生成的错误和警告。 这是默认值。|  
|SQLSRV_ERR_ERRORS|将返回上次调用 **sqlsrv** 函数时生成的错误。|  
|SQLSRV_ERR_WARNINGS|将返回上次调用 **sqlsrv** 函数时生成的警告。|  
  
### <a name="fetch-constants"></a>FETCH 常量  
下表列出了用于指定 [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)返回的阵列类型的常量。  
  
|SQLSRV 常量|说明|  
|-------------------|---------------|  
|SQLSRV_FETCH_ASSOC|**sqlsrv_fetch_array** 以关联阵列的形式返回下一行数据。|  
|SQLSRV_FETCH_BOTH|**sqlsrv_fetch_array** 以带有数值键和关联键的阵列形式返回下一行数据。 这是默认值。|  
|SQLSRV_FETCH_NUMERIC|**sqlsrv_fetch_array** 以数字索引的阵列形式返回下一行数据。|  
  
### <a name="logging-constants"></a>日志记录常量  
本部分列出了用于通过 [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)更改日志记录设置的常量。 有关日志记录活动的详细信息，请参阅 [Logging Activity](../../connect/php/logging-activity.md)。  
  
下表列出了可用作 **LogSubsystems** 设置的值的常量：  
  
|SQLSRV 常量（括号中为等效整数）|说明|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|对所有子系统启用日志记录。|  
|SQLSRV_LOG_SYSTEM_CONN (2)|对连接活动启用日志记录。|  
|SQLSRV_LOG_SYSTEM_INIT (1)|对初始化活动启用日志记录。|  
|SQLSRV_LOG_SYSTEM_OFF (0)|禁用日志记录。|  
|SQLSRV_LOG_SYSTEM_STMT (4)|对语句活动启用日志记录。|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|对错误函数活动（例如 handle_error 和 handle_warning）启用日志记录 。|  
  
下表列出了可用作 **LogSeverity** 设置的值的常量：  
  
|SQLSRV 常量（括号中为等效整数）|说明|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|指定将记录错误、警告和通知。|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|指定将记录错误。|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|指定将记录通知。|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|指定将记录警告。|  
  
### <a name="nullable-constants"></a>可为 Null 值的常量  
下表列出了可用于确定某列是否可为 Null 值或是否不提供此信息的常量。 你可以比较 **sqlsrv_field_metadata** 返回的 [Nullable](../../connect/php/sqlsrv-field-metadata.md) 键的值，以确定该列的状态是否可为 Null 值。  
  
|SQLSRV 常量（括号中为等效整数）|说明|  
|----------------------------------------------------------|---------------|  
|SQLSRV_NULLABLE_YES (0)|该列可为 Null 值。|  
|SQLSRV_NULLABLE_NO (1)|该列不可为 Null 值。|  
|SQLSRV_NULLABLE_UNKNOWN (2)|不确定该列是否可为 Null 值。|  
  
### <a name="param-constants"></a>PARAM 常量  
下表包含用于在调用 [sqlsrv_query](../../connect/php/sqlsrv-query.md) 或 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)时指定参数方向的常量。  
  
|SQLSRV 常量|说明|  
|-------------------|---------------|  
|SQLSRV_PARAM_IN|表示输入参数。|  
|SQLSRV_PARAM_INOUT|表示双向参数。|  
|SQLSRV_PARAM_OUT|表示输出参数。|  
  
### <a name="phptype-constants"></a>PHPTYPE 常量  
下表列出了用于描述 PHP 数据类型的常量。 有关 PHP 数据类型的信息，请参阅 [PHP 类型](https://php.net/manual/en/language.types.php)。  
  
|SQLSRV 常量|PHP 数据类型|  
|-------------------|-----------------|  
|SQLSRV_PHPTYPE_INT|Integer|  
|SQLSRV_PHPTYPE_DATETIME|datetime|  
|SQLSRV_PHPTYPE_FLOAT|Float|  
|SQLSRV_PHPTYPE_STREAM($encoding<sup>1</sup>)|Stream|  
|SQLSRV_PHPTYPE_STRING($encoding<sup>1</sup>)|String|  
  
1. SQLSRV_PHPTYPE_STREAM 和 SQLSRV_PHPTYPE_STRING 接受用于指定流编码的参数********。 下表包含作为可接受参数的 SQLSRV 常量以及对相应编码的说明。  
  
|SQLSRV 常量|说明|  
|-------------------|---------------|  
|SQLSRV_ENC_BINARY|数据以原始字节流的形式从服务器返回，无需执行编码或转换。|  
|SQLSRV_ENC_CHAR|数据以 8 位字符的形式返回，如在系统上设置的 Windows 区域设置的代码页中所指定。 任何多字节字符或未映射到此代码页中的字符都会替换为单字节问号 (?) 字符。<br /><br />这是默认编码。|  
|“UTF-8”|数据以 UTF-8 编码的形式返回。 已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 1.1 中添加了此常量。 有关 UTF-8 支持的详细信息，请参阅[如何：使用内置 UTF-8 支持发送和检索 UTF-8 数据](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)。|  
  
> [!NOTE]  
> 使用 SQLSRV_PHPTYPE_STREAM 或 SQLSRV_PHPTYPE_STRING 时，必须指定编码********。 如果未提供参数，将返回错误。  
  
有关这些常量的详细信息，请参阅 [如何：指定 PHP 数据类型](../../connect/php/how-to-specify-php-data-types.md)， [如何：使用 SQLSRV 驱动程序以流的形式检索字符数据](../../connect/php/how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md)。  
  
### <a name="sqltype-constants"></a>SQLTYPE 常量  
下表列出了用于描述 SQL Server 数据类型的常量。 某些常量类似于函数，可能使用对应于精度、小数位数和/或长度的参数。  绑定参数时，应使用函数式常量。 对于类型比较，需要标准（非函数式）常量。 有关 SQL Server 数据类型的信息，请参阅[数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)。 有关精度、小数位数和长度的信息，请参阅[精度、小数位数和长度 (Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)。  
  
|SQLSRV 常量|SQL Server 数据类型|  
|-------------------|------------------------|  
|SQLSRV_SQLTYPE_BIGINT|bigint|  
|SQLSRV_SQLTYPE_BINARY|binary|  
|SQLSRV_SQLTYPE_BIT|bit|  
|SQLSRV_SQLTYPE_CHAR|char<sup>5</sup>|  
|SQLSRV_SQLTYPE_CHAR($charCount)|char|  
|SQLSRV_SQLTYPE_DATE|date<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIME|datetime|  
|SQLSRV_SQLTYPE_DATETIME2|datetime2<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIMEOFFSET|datetimeoffset<sup>4</sup>|  
|SQLSRV_SQLTYPE_DECIMAL|decimal<sup>5</sup>|
|SQLSRV_SQLTYPE_DECIMAL($precision, $scale)|Decimal|  
|SQLSRV_SQLTYPE_FLOAT|FLOAT|  
|SQLSRV_SQLTYPE_IMAGE|image<sup>1</sup>|  
|SQLSRV_SQLTYPE_INT|int|  
|SQLSRV_SQLTYPE_MONEY|money| 
|SQLSRV_SQLTYPE_NCHAR|nchar<sup>5</sup>|   
|SQLSRV_SQLTYPE_NCHAR($charCount)|nchar|  
|SQLSRV_SQLTYPE_NUMERIC|numeric<sup>5</sup>|
|SQLSRV_SQLTYPE_NUMERIC($precision, $scale)|numeric|  
|SQLSRV_SQLTYPE_NVARCHAR|nvarchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_NVARCHAR($charCount)|nvarchar|  
|SQLSRV_SQLTYPE_NVARCHAR('max')|nvarchar(MAX)|  
|SQLSRV_SQLTYPE_NTEXT|ntext<sup>2</sup>|  
|SQLSRV_SQLTYPE_REAL|real|  
|SQLSRV_SQLTYPE_SMALLDATETIME|smalldatetime|  
|SQLSRV_SQLTYPE_SMALLINT|smallint|  
|SQLSRV_SQLTYPE_SMALLMONEY|smallmoney|  
|SQLSRV_SQLTYPE_TEXT|text<sup>3</sup>|  
|SQLSRV_SQLTYPE_TIME|time<sup>4</sup>|  
|SQLSRV_SQLTYPE_TIMESTAMP|timestamp|  
|SQLSRV_SQLTYPE_TINYINT|tinyint|  
|SQLSRV_SQLTYPE_UNIQUEIDENTIFIER|uniqueidentifier|  
|SQLSRV_SQLTYPE_UDT|UDT|  
|SQLSRV_SQLTYPE_VARBINARY|varbinary<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARBINARY($byteCount)|varbinary|  
|SQLSRV_SQLTYPE_VARBINARY('max')|varbinary(MAX)|  
|SQLSRV_SQLTYPE_VARCHAR|varchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARCHAR($charCount)|varchar|  
|SQLSRV_SQLTYPE_VARCHAR('max')|varchar(MAX)|  
|SQLSRV_SQLTYPE_XML|xml|  
  
1.  这是映射到 varbinary(max) 类型的旧类型。  
  
2.  这是映射到较新 nvarchar 类型的旧类型。  
  
3.  这是映射到较新 varchar 类型的旧类型。  
  
4.  已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 1.1 中添加了对此类型的支持。  

5.  应在类型比较操作中使用这些常量，不要用类似的语法替换函数式常量。 对于绑定参数，应使用函数式常量。

  
下表列出了接受参数的 SQLTYPE 常量以及参数允许的值范围。  
  
|SQLTYPE|参数|参数的允许范围|  
|-----------|-------------|---------------------------------|  
|SQLSRV_SQLTYPE_CHAR、<br /><br />SQLSRV_SQLTYPE_VARCHAR|charCount|1 - 8000|  
|SQLSRV_SQLTYPE_NCHAR、<br /><br />SQLSRV_SQLTYPE_NVARCHAR|charCount|1 - 4000|  
|SQLSRV_SQLTYPE_BINARY、<br /><br />SQLSRV_SQLTYPE_VARBINARY|byteCount|1 - 8000|  
|SQLSRV_SQLTYPE_DECIMAL、<br /><br />SQLSRV_SQLTYPE_NUMERIC|精准率|1 - 38|  
|SQLSRV_SQLTYPE_DECIMAL、<br /><br />SQLSRV_SQLTYPE_NUMERIC|scale|1 - precision|  
  
### <a name="transaction-isolation-level-constants"></a>事务隔离级别常量  
用于 **sqlsrv_connect** 的 [TransactionIsolation](../../connect/php/sqlsrv-connect.md)键接受以下常量之一：  
  
-   SQLSRV_TXN_READ_UNCOMMITTED  
  
-   SQLSRV_TXN_READ_COMMITTED  
  
-   SQLSRV_TXN_REPEATABLE_READ  
  
-   SQLSRV_TXN_SNAPSHOT  
  
-   SQLSRV_TXN_SERIALIZABLE  
  
### <a name="cursor-and-scrolling-constants"></a>游标和滚动常量  
以下常量指定可用于结果集中的游标类型：  
  
-   SQLSRV_CURSOR_FORWARD  
  
-   SQLSRV_CURSOR_STATIC  
  
-   SQLSRV_CURSOR_DYNAMIC  
  
-   SQLSRV_CURSOR_KEYSET  
  
-   SQLSRV_CURSOR_CLIENT_BUFFERED  
  
以下常量指定要在结果集中选择的行：  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
有关如何使用这些常量的信息，请参阅 [Specifying a Cursor Type and Selecting Rows](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)。  
  
## <a name="see-also"></a>另请参阅  
[SQLSRV 驱动程序 API 参考](../../connect/php/sqlsrv-driver-api-reference.md)  
  
