---
title: sys. fulltext_semantic_languages （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: a345e41f42cc70e941e4a87e3510312313d4dc03
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764669"
---
# <a name="sysfulltext_semantic_languages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  为在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中注册统计模型的每种语言返回一行。 注册语言模型后，则支持对该语言进行语义索引。  
  
 此目录视图类似于[transact-sql&#41;&#40;的 fulltext_languages ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)。  
    
||||  
|-|-|-|  
|**列名**|类型|**说明**|  
|lcid|int|语言的 Microsoft Windows 区域设置标识符 (LCID)。|  
|name|sysname|[&#40;transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)对应于**lcid**值的sys.sys语言中的别名值，或者是数字 lcid 的字符串表示形式。|  
  
## <a name="general-remarks"></a>一般备注  
 有关详细信息，请参阅 [安装和配置语义搜索](../../relational-databases/search/install-and-configure-semantic-search.md)。  
  
## <a name="metadata"></a>元数据  
 有关为了支持语义索引而安装的语义语言统计数据库的详细信息，请查询目录视图[sys. fulltext_semantic_language_statistics_database &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)。  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>权限  
 目录视图中仅显示用户拥有的安全对象的元数据，或用户对其拥有某些权限的安全对象的元数据。  
  
## <a name="examples"></a>示例  
 下面的示例演示如何查询**fulltext_semantic_languages sys.databases**以获取有关在当前实例上为语义索引注册的所有语言模型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的信息。  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [安装和配置语义搜索](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
