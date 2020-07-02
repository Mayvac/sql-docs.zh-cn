---
title: sp_helplanguage （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2878d206d4bc90d801e1e8f42f4f3f2c04d2c121
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733199"
---
# <a name="sp_helplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  报告有关 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的某个特定的替代语言或所有语言的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>自变量  
`[ @language = ] 'language'`要显示其信息的替代语言的名称。 *language*的值为**sysname**，默认值为 NULL。 如果指定*language* ，则返回有关指定语言的信息。 如果未指定语言，则将返回**sys.sys语言**兼容性视图中有关所有语言的信息。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|语言标识号。|  
|**dateformat**|**nchar(3)**|日期的格式。|  
|**datefirst**|**tinyint**|每周的第一天：1 代表星期一，2 代表星期二，依此类推，直到 7 代表星期日。|  
|**升级**|**int**|最后一次升级此语言的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。|  
|name|**sysname**|语言名称。|  
|**alias**|**sysname**|语言的替代名称。|  
|**months**|**nvarchar(372)**|月份名称。|  
|**shortmonths**|**nvarchar(132)**|月份简称。|  
|**天数**|**nvarchar(217)**|日期名称。|  
|**lcid**|**int**|语言的 Windows 区域设置 ID。|  
|**msglangid**|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]消息组 ID。|  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-information-about-a-single-language"></a>A. 返回有关单个语言的信息  
 以下示例显示有关替代语言 `French` 的信息。  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. 返回有关所有语言的信息  
 以下示例显示有关所有安装的替代语言的信息。  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据库引擎存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE (Transact-SQL)](../../t-sql/functions/language-transact-sql.md)   
 [将 LANGUAGE &#40;Transact-sql&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
