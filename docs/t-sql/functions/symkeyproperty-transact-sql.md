---
title: SYMKEYPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SYMKEYPROPERTY_TSQL
- SYMKEYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SYMKEYPROPERTY
ms.assetid: 3d1f7075-3a3c-4660-8cd0-ed938b86fecd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c67de4390b23055aaa5c62b735ae2a52bcb2188f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85714730"
---
# <a name="symkeyproperty-transact-sql"></a>SYMKEYPROPERTY (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  返回从 EKM 模块创建的对称密钥的算法。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
SYMKEYPROPERTY ( Key_ID , 'algorithm_desc' | 'string_sid' | 'sid' )  
```  
  
## <a name="arguments"></a>参数  
 Key_ID   
 是数据库中对称密钥的 Key_ID。 若要查找您仅知道密钥名称的 Key_ID，请使用 SYMKEY_ID。 Key_ID 为 int 数据类型   。  
  
 **'** algorithm_desc **'**  
 指定输出应返回对称密钥的算法说明。 仅适用于从 EKM 模块创建的对称密钥。  
  
## <a name="return-types"></a>返回类型  
 **sql_variant**  
  
## <a name="permissions"></a>权限  
 需要对对称密钥拥有某些权限，并且调用方对对称密钥的 VIEW 权限没有被拒绝。  
  
## <a name="examples"></a>示例  
 下面的示例返回 Key_ID 为 256 的对称密钥的算法。  
  
```  
SELECT SYMKEYPROPERTY(256, 'algorithm_desc') AS Algorithm ;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [ASYMKEY_ID (Transact-SQL)](../../t-sql/functions/asymkey-id-transact-sql.md)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.symmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [安全性目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [KEY_ID (Transact-SQL)](../../t-sql/functions/key-id-transact-sql.md)   
 [ASYMKEYPROPERTY (Transact-SQL)](../../t-sql/functions/asymkeyproperty-transact-sql.md)  
  
  
