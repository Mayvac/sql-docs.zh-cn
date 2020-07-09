---
title: 事务 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a706c73c12ad35480380f8d558837f30f3ad3542
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007564"
---
# <a name="transactions-transact-sql"></a>事务 (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  事务是单个工作单元。 如果某一事务成功，则在该事务中进行的所有数据修改均会提交，成为数据库中的永久组成部分。 如果事务遇到错误且必须取消或回滚，则所有数据修改均被清除。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以下列事务模式运行：  
  
 自动提交事务  
 每条单独的语句都是一个事务。  
  
 显式事务  
 每个事务均以 BEGIN TRANSACTION 语句显式开始，以 COMMIT 或 ROLLBACK 语句显式结束。  
  
 隐式事务  
 在前一个事务完成时新事务隐式启动，但每个事务仍以 COMMIT 或 ROLLBACK 语句显式完成。  
  
 批处理级事务  
 只能应用于多个活动结果集 (MARS)，在 MARS 会话中启动的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 显式或隐式事务变为批处理级事务。 当批处理完成时没有提交或回滚的批处理级事务自动由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进行回滚。  

> [!NOTE] 
> 有关与数据仓库产品相关的特殊注意事项，请参阅[事务（SQL 数据仓库）](transactions-sql-data-warehouse.md)。   

## <a name="in-this-section"></a>本节内容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供以下事务语句：  
  
|||  
|-|-|  
|[BEGIN DISTRIBUTED TRANSACTION](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[BEGIN TRANSACTION](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[COMMIT TRANSACTION](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[SAVE TRANSACTION](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[COMMIT WORK](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>另请参阅  
 [SET IMPLICIT_TRANSACTIONS (Transact-SQL)](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT (Transact-SQL)](../../t-sql/functions/trancount-transact-sql.md)  
  
  
