---
title: 使用 INSERT 加载数据
description: 使用 T-sql INSERT 语句将数据加载到并行数据仓库中， (PDW) 分布式或复制的表。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: c28d15febb08855b914e4cd6ed04a97850ffe02c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766856"
---
# <a name="load-data-with-insert-into-parallel-data-warehouse"></a>加载包含 INSERT into Parallel 数据仓库的数据

您可以使用 tsql INSERT 语句将数据加载到 SQL Server 并行数据仓库 (PDW) 分布式或复制的表中。 有关 INSERT 的详细信息，请参阅 [insert](../t-sql/statements/insert-transact-sql.md)。 对于分布式表中的复制表和所有非分布列，PDW 使用 SQL Server 将语句中指定的数据值隐式转换为目标列的数据类型。 有关 SQL Server 数据转换规则的详细信息，请参阅 [SQL 数据类型转换](../t-sql/data-types/data-type-conversion-database-engine.md)。 但对于分布列，PDW 仅支持 SQL Server 支持的隐式转换的子集。 因此，当您使用 INSERT 语句将数据加载到分布列时，必须使用下表中定义的格式之一来指定源数据。  
  
  
## <a name="insert-literals-into-binary-types"></a><a name="InsertingLiteralsBinary"></a>在二进制类型中插入文本  
下表定义了接受的文本类型、格式和转换规则，用于将文本值插入到类型为 **binary** (*n*) 或 **varbinary** (*n*) 的分布列。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|二进制文本|0x*hexidecimal_string*<br /><br />示例：0x12Ef|二进制文本必须以0x 开头。<br /><br />数据源长度不能超过为数据类型指定的字节数。<br /><br />如果数据源长度小于 **binary** 数据类型的大小，则会将数据填充到右侧，使其达到数据类型大小。|  
  
## <a name="insert-literals-into-date-and-time-types"></a><a name="InsertingLiteralsDateTime"></a>将文本插入日期和时间类型  
日期和时间文本是使用特定格式的字符值表示的，并用单引号引起来。 下表定义了允许的文字类型、格式和转换规则，以便将日期或时间文字插入到类型为 **datetime**、 **smalldatetime**、 **date**、 **time**、 **datetimeoffset**或 **datetime2**的 SQL Server PDW 分布列。  
  
### <a name="datetime-data-type"></a>datetime 数据类型  
下表定义了用于将文本值插入到类型为 **datetime**的分布列中的接受格式和规则。 任何空字符串 ( "" ) 均转换为默认值 "1900-01-01 12：00： 00.000"。 只包含空格 ( "" ) 生成错误的字符串。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|**Datetime**格式的字符串文本|"YYYY-MM-DD hh： MM： ss [. nnn]"<br /><br />示例： "2007-05-08 12：35： 29.123"|在插入值时，缺少小数位设置为0。 例如，文本 "2007-05-08 12:35" 插入为 "2007-05-08 12：35： 00.000"。|  
|**Smalldatetime**格式的字符串文字|' YYYY-MM-DD hh： MM '<br /><br />示例： "2007-05-08 12:35"|在插入值时，秒数和剩余小数位数设置为0。|  
|**日期**格式的字符串文字|"YYYY-MM-DD"<br /><br />示例： "2007-05-08"|在插入值时，时间值 (小时、分钟、秒和小数) 设置为12：00：00.000。|  
|**Datetime2**格式的字符串文本|' YYYY-MM-DD hh： MM： ss. nnnnnnn '<br /><br />示例： "2007-05-08 12：35： 29.1234567"|源数据不能超过三个小数位。 例如，将插入文本 "2007-05-08 12：35： 29.123"，但值 "2007-05-08 12：35： 29.1234567" 生成错误。|  
  
### <a name="smalldatetime-data-type"></a>smalldatetime 数据类型  
下表定义了用于将文本值插入到类型 **smalldatetime**的分布列中的接受格式和规则。 任何空字符串 ( "" ) 将转换为默认值 "1900-01-01 12:00"。 只包含空格 ( "" ) 生成错误的字符串。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|**Smalldatetime**格式的字符串文字|' YYYY-MM-DD hh： mm ' 或 ' YYYY-MM-DD hh： mm： 00 '<br /><br />示例： "2007-05-08 12:00" 或 "2007-05-08 12:00:00"|源数据必须具有年、月、日、小时和分钟的值。 秒是可选的，如果存在，则必须设置为值00。 任何其他值将生成错误。|  
|**日期**格式的字符串文字|"YYYY-MM-DD"<br /><br />示例： "2007-05-08"|在插入值时，时间值 (小时、分钟、秒和小数) 设置为0。|  
  
### <a name="date-data-type"></a>日期数据类型  
下表定义了用于将文本值插入到 **date**类型的分布列中的接受格式和规则。 任何空字符串 ( "" ) 将转换为默认值 "1900-01-01"。 只包含空格 ( "" ) 生成错误的字符串。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|**日期**格式的字符串文字|"YYYY-MM-DD"<br /><br />示例： "2007-05-08"|这是唯一接受的格式。|  
  
### <a name="time-data-type"></a>时间数据类型  
下表定义了用于将文本值插入到类型为 **time**的分布列中的接受格式和规则。 任何空字符串 ( "" ) 将转换为默认值 "00：00： 00.0000"。 只包含空格 ( "" ) 生成错误的字符串。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|**时间**格式的字符串文字|"hh： mm： ss. nnnnnnn"<br /><br />示例： "12：35： 29.1234567"|如果数据源的精度较小或相等 (小数位数) 与 **time** 数据类型的精度相同，则将用零填充数据。 例如，文本值 "12：35： 29.123" 插入为 "12：35： 29.1230000"。<br /><br />具有的精度大于目标数据类型的值将被拒绝。|  
  
### <a name="datetimeoffset-data-type"></a>datetimeoffset 数据类型  
下表定义了用于将文字值插入到类型为 **datetimeoffset** (*n*) 的分布列中的接受格式和规则。 默认格式为 "YYYY-MM-DD hh： MM： ss. nnnnnnn {+ |-} hh： MM"。 空字符串 ( "" ) 转换为默认值 "1900-01-01 12：00： 00.0000000 + 00:00"。 只包含空格 ( "" ) 生成错误的字符串。 小数位数值取决于列定义。 例如，定义为 **datetimeoffset** (2) 的列将具有两个小数位。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|**Datetime**格式的字符串文本|"YYYY-MM-DD hh： MM： ss [. nnn]"<br /><br />示例： "2007-05-08 12：35： 29.123"|在插入值时，缺少小数位和偏移值设置为0。 例如，文字 "2007-05-08 12：35： 29.123" 被插入为 "2007-05-08 12：35： 29.1230000 + 00:00"。|  
|**Smalldatetime**格式的字符串文字|' YYYY-MM-DD hh： MM '<br /><br />示例： "2007-05-08 12:35"|秒，在插入值时，剩余的小数位数和偏移量值将设置为0。|  
|**日期**格式的字符串文字|"YYYY-MM-DD"<br /><br />示例： "2007-05-08"|在插入值时，时间值 (小时、分钟、秒和小数) 设置为0。 例如，文本 "2007-05-08" 插入为 "2007-05-08 00：00： 00.0000000 + 00:00"。|  
|**Datetime2**格式的字符串文本|' YYYY-MM-DD hh： MM： ss. nnnnnnn '<br /><br />示例： "2007-05-08 12：35： 29.1234567"|源数据不能超过 datetimeoffset 列中指定的秒小数部分。 如果数据源的小数部分的小数位数较小或相等，则使用零将数据填充到右侧。 例如，如果数据类型为 datetimeoffset (5) ，则文本值 "2007-05-08 12：35： 29.123 + 12:15" 将插入为 "12：35： 29.12300 + 12:15"。|  
|**Datetimeoffset**格式的字符串文字|' YYYY-MM-DD hh： MM： ss. nnnnnnn {+&#124;-} hh： MM '<br /><br />示例： "2007-05-08 12：35： 29.1234567 + 12:15"|源数据不能超过 datetimeoffset 列中指定的秒小数部分。 如果数据源的小数部分的小数位数较小或相等，则使用零将数据填充到右侧。 例如，如果数据类型为 datetimeoffset (5) ，则文本值 "2007-05-08 12：35： 29.123 + 12:15" 将插入为 "12：35： 29.12300 + 12:15"。|  
  
### <a name="datetime2-data-type"></a>datetime2 数据类型  
下表定义了用于将文本值插入到类型为 **datetime2** (*n*) 的分布列中的接受格式和规则。 默认格式为 "YYYY-MM-DD hh： MM： ss. nnnnnnn"。 空字符串 ( "" ) 转换为默认值 "1900-01-01 12:00:00"。 只包含空格 ( "" ) 生成错误的字符串。 小数位数值取决于列定义。 例如，定义为 **datetime2** (2) 的列将具有两个小数位。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|**Datetime**格式的字符串文本|"YYYY-MM-DD hh： MM： ss [. nnn]"<br /><br />示例： "2007-05-08 12：35： 29.123"|秒的小数部分是可选的，并在插入值时设置为0。<br /><br />比目标数据类型的小数位数大于目标数据类型的值。|  
|**Smalldatetime**格式的字符串文字|' YYYY-MM-DD hh： MM '<br /><br />示例： "2007-05-08 12"|在插入值时，可选的秒数和剩余小数位数设置为0。|  
|**日期**格式的字符串文字|"YYYY-MM-DD"<br /><br />示例： "2007-05-08"|在插入值时，时间值 (小时、分钟、秒和小数) 设置为0。 例如，文本 "2007-05-08" 插入为 "2007-05-08 12：00： 00.0000000"。|  
|**Datetime2**格式的字符串文本|"YYYY-MM-DD hh： MM： ss： nnnnnnn"<br /><br />示例： "2007-05-08 12：35： 29.1234567"|如果数据源包含的数据和时间组成部分小于或等于 **datetime2** (*n*) 中指定的值，则插入数据;否则，会生成错误。|  
  
## <a name="insert-literals-into-numeric-types"></a><a name="InsertLiteralsNumeric"></a>将文本插入数值类型  
下表定义了可接受的格式和转换规则，用于将文本值插入到使用数值类型的 SQL Server PDW 分布列。  
  
### <a name="bit-data-type"></a>bit 数据类型  
下表定义了用于将文本值插入到类型为 **bit**的分布列中的接受格式和规则。 空字符串 ( "" ) 或只包含空白的字符串 ( "" ) 转换为0。  
  
|文本类型|format|转换规则|  
|----------------|----------|--------------------|  
|**整数**格式的字符串文字|'nnnnnnnnnn'<br /><br />示例： "1" 或 "321"|格式为字符串文字的整数值不能包含负值。 例如，值 "-123" 生成错误。<br /><br />大于1的值将转换为1。 例如，值 "123" 将转换为1。|  
|字符串文本|"TRUE" 或 "FALSE"<br /><br />示例： "true"|值 "TRUE" 转换为 1;值 "FALSE" 转换为0。|  
|整数文本|nnnnnnnn<br /><br />示例：1或321|大于1或小于0的值将转换为1。 例如，将值123和-123 转换为1。|  
|Decimal 文本|nnnnn<br /><br />示例：1234.5678|大于1或小于0的值将转换为1。 例如，将值123.45 和-123.45 转换为1。|  
  
### <a name="decimal-data-type"></a>decimal 数据类型  
下表定义了用于将文字值插入 **decimal** (*p，s*) 类型的分布列的接受格式和规则。 数据转换规则与 SQL Server 相同。 有关详细信息，请参阅 MSDN 上的 [数据类型转换](../t-sql/data-types/data-type-conversion-database-engine.md) 。  
  
|文本类型|格式|  
|----------------|----------|  
|**整数**格式的字符串文字|'nnnnnnnnnnnn'<br /><br />示例： "321312313123"|  
|**十进制**格式的字符串文本|"nnnnnn"<br /><br />示例： "123344.34455"|  
|整数文本|nnnnnnnnnnnn<br /><br />示例：321312313123|  
|Decimal 文本|nnnnnn<br /><br />示例： "123344.34455"|  
  
### <a name="float-and-real-data-types"></a>float 和 real 数据类型  
下表定义了用于将文本值插入到 **float** 或 **real**类型的分布列中的接受格式和规则。 数据转换规则与 SQL Server 相同。 有关详细信息，请参阅 MSDN 上的 [数据类型转换](../t-sql/data-types/data-type-conversion-database-engine.md) 。  
  
|文本类型|格式|  
|----------------|----------|  
|**整数**格式的字符串文字|'nnnnnnnnnnnn'<br /><br />示例： "321312313123"|  
|**十进制**格式的字符串文本|"nnnnnn"<br /><br />示例： "123344.34455"|  
|**浮点**格式的字符串文本|"nnnnnE + nn"<br /><br />例如： "3.12323 E + 14"|  
|整数文本|nnnnnnnnnnnn<br /><br />示例：321312313123|  
|Decimal 文本|nnnnnn<br /><br />示例：123344.34455|  
|浮点型文本|n. nnnnnE + nn<br /><br />示例： 3.12323 E + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int、bigint、tinyint、smallint 数据类型  
下表定义了接受的格式和规则，用于将文本值插入 **int**、 **bigint**、 **tinyint**或 **smallint**类型的分布列。 数据源不能超出给定数据类型允许的范围。 例如， **tinyint** 的范围为0到255， **int** 的范围为-2147483648 到2147483647。  
  
|文本类型|格式|转换规则|  
|------------|------|----------------|
|**整数**格式的字符串文字|'nnnnnnnnnnnnnn'<br /><br />示例： "321312313123"| 无 |  
|整数文本|nnnnnnnnnnnnnn<br /><br />示例：321312313123| 无|  
|Decimal 文本|nnnnnn<br /><br />示例：123344.34455|小数点右边的值将被截断。|  
  
### <a name="money-and-smallmoney-data-types"></a>money 和 smallmoney 数据类型  
Money 文本值表示为数字，其中包含可选的小数点和货币符号作为前缀。 数据源不能超出给定数据类型允许的范围。 例如， **smallmoney** 的范围为-214748.3648 到214748.3647，而 **货币** 的范围为-922337203685477.5808 到922337203685477.5807。 下表定义了接受的格式和规则，用于将文本值插入到类型为 **money** 或 **smallmoney**的分布列。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|**整数**格式的字符串文字|nnnnnnnn<br /><br />示例： "123433"|在插入值时，小数点后缺少的位数设置为0。 例如，文本 "12345" 插入为12345.0000。|  
|**十进制**格式的字符串文本|"nnnnnn"<br /><br />示例： "123344.34455"|如果小数点后的位数超过4，则该值向上舍入到最接近的值。 例如，值 "123344.34455" 插入为123344.3446。|  
|**Money**格式的字符串文本|"$nnnnnn nnnn"<br /><br />示例： "$123456.7890"|可选的货币符号不会插入值。<br /><br />如果小数点后的位数超过4，则该值向上舍入到最接近的值。|  
|整数文本|nnnnnnnn<br /><br />示例：123433|在插入值时，小数点后缺少的位数设置为0。 例如，文本12345插入为12345.0000。|  
|Decimal 文本|nnnnnn<br /><br />示例：123344.34455|如果小数点后的位数超过4，则该值向上舍入到最接近的值。 例如，将值123344.34455 插入为123344.3446。|  
|Money 文本|$nnnnnn nnnn<br /><br />示例： $123456.7890|可选的货币符号不会插入值。<br /><br />如果小数点后的位数超过4，则该值向上舍入到最接近的值。|  
  
## <a name="inserting-literals-into-string-types"></a><a name="InsertLiteralsString"></a>将文本插入字符串类型  
下表定义了用于将文本值插入到使用字符串类型的 SQL Server PDW 列中的接受格式和转换规则。  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>char、varchar、nchar 和 nvarchar 数据类型  
下表定义在 **char**、 **varchar**、 **nchar** 和 **nvarchar**类型的分布列中插入文本值时的接受格式和规则。 数据源长度不能超过为数据类型指定的大小。 如果数据源长度小于 **char** 或 **nchar** 数据类型的大小，则会将数据填充到右侧，并用空格来达到数据类型大小。  
  
|文本类型|格式|转换规则|  
|----------------|----------|--------------------|  
|字符串文本|格式： "string"<br /><br />示例： "abc"| 无|  
|Unicode 字符串文本|格式： N'character string '<br /><br />示例： N'abc '|  无 |  
|整数文本|格式： nnnnnnnnnnn<br /><br />示例：321312313123| 无 |  
|Decimal 文本|格式： nnnnnn. nnnnnnn<br /><br />示例：12344.34455| 无 |  
|Money 文本|格式： $nnnnnn nnnnn<br /><br />示例： $123456.99|货币符号不是以值插入的。 若要插入货币符号，请将值作为字符串文本插入。 这将匹配 **dwloader** 工具的格式，它将每个文字视为字符串文字。<br /><br />不允许使用逗号。<br /><br />如果小数点后的位数超过2，则该值将向上舍入到最接近的值。 例如，将值123.946789 插入为123.95。<br /><br />当使用 CONVERT 函数插入 money 文本时，仅允许默认样式 0 (小数点后两位数) 。|  

  
## <a name="see-also"></a>另请参阅  
 
[分布式数据](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture)  
[INSERT](../t-sql/statements/insert-transact-sql.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Metadata query examples](metadata-query-examples.md) 
-->