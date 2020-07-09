---
title: GetRoot（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetRoot
- GetRoot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetRoot [Database Engine]
ms.assetid: 240b70f1-eeda-44ab-b4bb-9e4af80fa7c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbc5bd95c10c89da4fb6fc6cbd1400f2e310927b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738199"
---
# <a name="getroot-database-engine"></a>GetRoot（数据库引擎）
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

返回层次结构树的根。 GetRoot() 是静态方法。
  
## <a name="syntax"></a>语法  
  
```sql
-- Transact-SQL syntax  
hierarchyid::GetRoot ( )   
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId GetRoot ( )   
```  
  
## <a name="return-types"></a>返回类型  
SQL Server 返回类型：hierarchyid 
  
CLR 返回类型：SqlHierarchyId 
  
## <a name="remarks"></a>备注  
用于确定层次结构树中的根节点。
  
## <a name="examples"></a>示例  
  
### <a name="a-transact-sql-example"></a>A. Transact-SQL 示例  
下面的示例返回层次结构树的根节点：
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = hierarchyid::GetRoot()  
```  
  
### <a name="b-clr-example"></a>B. CLR 示例  
下面的代码段调用 GetRoot() 方法：
  
```sql
SqlHierarchyId.GetRoot()  
```  
  
## <a name="see-also"></a>另请参阅
[hierarchyid 数据类型方法引用](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[分层数据 (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
