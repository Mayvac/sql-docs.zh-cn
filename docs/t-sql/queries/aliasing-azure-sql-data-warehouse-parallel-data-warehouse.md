---
title: 别名
description: Azure SQL 数据仓库和并行数据仓库中的别名。
titleSuffix: Azure SQL Data Warehouse
ms.custom: seo-lt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
author: shkale-msft
ms.author: shkale
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 01afcc83b2a7094ea65607cac87437854e828e11
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197306"
---
# <a name="aliasing-azure-sql-data-warehouse-parallel-data-warehouse"></a>别名创建（Azure SQL 数据仓库、并行数据仓库）

[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

别名创建允许在 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)][!INCLUDE[DWsql](../../includes/dwsql-md.md)] 查询中临时替换简短且易于记忆的字符串来代替表或列名称。 在 JOIN 查询中经常使用表别名，因为 JOIN 语法在引用列时需要完全限定的对象名称。  

别名必须是符合对象命名规则的单个词。 有关详细信息，请参阅[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]中的“对象命名规则”。 别名不能包含空格，也不能用单引号或双引号括起来。  

## <a name="syntax"></a>语法

```tsql
object_source [ AS ] alias
```

## <a name="arguments"></a>参数

*object_source*  
源表或源列的名称。  

AS  
一个可选的别名介词。 使用范围变量别名创建时，禁止使用 AS 关键字。  

alias 表或列所需的临时引用名称。 可以使用任何有效的对象名称。 有关详细信息，请参阅[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]中的“对象命名规则”。  

## <a name="examples-sssdw-and-sspdw"></a>示例：[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

以下示例展示了一个包含多个联接的查询。 此示例演示了表别名创建和列别名创建。  

- 列别名创建：在此示例中，涉及选择列表中的列的列和表达式都创建了别名。 `SalesTerritoryRegion AS SalesTR` 演示了一个简单的列别名。 `Sum(SalesAmountQuota) AS TotalSales` 演示了  

- 表别名创建：`dbo.DimSalesTerritory AS st` 展示了如何为 `dbo.DimSalesTerritory` 表创建 `st` 别名。  

```tsql
-- Uses AdventureWorks

SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion AS SalesTR,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```

如下所示，可以排除 AS 关键字，但为了便于阅读，通常会包含 AS 关键字。  

```tsql
-- Uses AdventureWorks

SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```

## <a name="next-steps"></a>后续步骤

- [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)
- [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)
- [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)