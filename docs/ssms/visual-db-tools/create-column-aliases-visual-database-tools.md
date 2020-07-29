---
title: 创建列别名
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: c4feb18b5f01b1e999ecec5b5b8e022230912d8f
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "85977818"
---
# <a name="create-column-aliases-visual-database-tools"></a>创建列别名 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
您可为列名创建别名，以更方便地使用列名、计算和汇总值。 例如，您可以创建列别名以实现以下目的：  
  
-   为诸如 `(quantity * unit_price)` 之类的表达式或为聚合函数创建列名，如“Total Amount”。  
  
-   为列名创建简写形式，如用 `"d_id"` 代表 `"discounts.stor_id."`  
  
定义列别名后，可在“选择”查询中使用该别名以指定查询输出。  
  
### <a name="to-create-a-column-alias"></a>创建列别名  
  
1.  在“条件”  窗格中，找到包含要为其创建别名的数据列的行，如果需要，还可将其标记为输出。 如果该数据列不在网格中，则将其添加到网格中。  
  
2.  在该行的“别名”  列中，输入别名。 别名必须遵循 SQL 的所有命名约定。 如果输入的别名包含空格，则查询和视图设计器将自动在其两旁放置分隔符。  
  
## <a name="see-also"></a>另请参阅  
[向查询中添加列 (Visual Database Tools)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[对查询结果进行排序和分组 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[汇总查询结果 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[执行基本的查询操作 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
