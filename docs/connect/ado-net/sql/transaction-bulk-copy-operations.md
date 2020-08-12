---
title: 事务和大容量复制操作
description: 介绍了如何在事务中执行大容量复制操作，包括如何提交或回滚事务。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 685bb349366ad955248a05e23ec030788dcbc63d
ms.sourcegitcommit: 6b3569977b034554883a94d73d1c4df6e2f74fe2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85106909"
---
# <a name="transaction-and-bulk-copy-operations"></a>事务和大容量复制操作

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

大容量复制操作可以作为独立操作或作为多步事务的一部分执行。 后面这个选项使你能够在同一事务中执行多个大容量复制操作，以及执行其他数据库操作（例如插入、更新和删除），同时仍能够提交或回滚整个事务。  
  
默认情况下，大容量复制操作作为独立的操作完成。 大容量复制操作以非事务方式执行，不可以对其进行回滚。 如果需要在出错时回滚全部或部分大容量复制，可以执行以下操作：

 - 使用 <xref:Microsoft.Data.SqlClient.SqlBulkCopy> 托管的事务

 - 在现有事务中执行大容量复制操作

 - 登记到 System.Transactions <xref:System.Transactions.Transaction>。  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>执行非事务大容量复制操作  
下面的控制台应用程序演示了非事务大容量复制操作在操作中途遇到错误时将发生什么情况。  
  
在该示例中，源表和目标表分别包括一个名为 ProductID 的 `Identity` 列。 该代码首先通过删除所有行，然后插入知道其 ProductID 存在于源表中的一行，准备目标表  。 默认情况下，系统会在目标表中为添加的每个行生成一个 `Identity` 列的新值。 在此示例中，在打开连接时设置某个选项，该选项用于强制执行大容量加载过程以改为使用源表中的 `Identity` 值。  
  
执行大容量复制操作，并将 <xref:Microsoft.Data.SqlClient.SqlBulkCopy.BatchSize%2A> 属性设置为 10。 当操作遇到无效行时，将引发异常。 在此第一个示例中，大容量复制操作是非事务的。 提交发生错误之前复制的所有批。 回滚包含重复键的批，并暂停大容量复制操作，然后它才处理任何剩余的批。  
  
> [!NOTE]
>  除非已按[大容量复制示例设置](bulk-copy-example-setup.md)中所述创建了工作表，否则此示例将不会运行。 提供此代码是为了演示仅使用 SqlBulkCopy 时的语法。 如果源表和目标表位于同一 SQL Server 实例中，可以更便捷地使用 Transact-SQL `INSERT … SELECT` 语句复制数据。  
  
[!code-csharp[DataWorks SqlBulkCopyOptions_Default#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_Default.cs#1)]
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>在事务中执行专用的大容量复制操作  
默认情况下，大容量复制操作是其自己的事务。 要执行专用的大容量复制操作时，使用连接字符串创建 <xref:Microsoft.Data.SqlClient.SqlBulkCopy> 的实例，或者在没有活动事务的情况下使用现有 <xref:Microsoft.Data.SqlClient.SqlConnection> 对象。 在每个方案中，大容量复制操作创建一个事务，然后提交或回滚该事务。  
  
可在 <xref:Microsoft.Data.SqlClient.SqlBulkCopy> 类构造函数中显式指定 <xref:Microsoft.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> 选项以在其自己的事务中执行大容量复制操作。 每一批的操作将在单独的事务中执行。  
  
> [!NOTE]
>  因为不同批在不同的事务中执行，因此如果在大容量复制操作期间出现错误，将回滚当前批中的所有行，但之前批中的行将保留在数据库中。  
  
下面的控制台应用程序与之前的示例类似，但有一个例外：在此示例中，大容量复制操作管理其自己的事务。 提交发生错误之前复制的所有批。 回滚包含重复键的批，并暂停大容量复制操作，然后它才处理任何剩余的批。 
  
> [!IMPORTANT]
>  除非已按[大容量复制示例设置](bulk-copy-example-setup.md)中所述创建了工作表，否则此示例将不会运行。 提供此代码是为了演示仅使用 SqlBulkCopy 时的语法。 如果源表和目标表位于同一 SQL Server 实例中，可以更便捷地使用 Transact-SQL `INSERT … SELECT` 语句复制数据。  
  
[!code-csharp[DataWorks SqlBulkCopyOptions_UseInternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopyOptions_UseInternalTransaction.cs#1)]
  
## <a name="using-existing-transactions"></a>使用现有事务  
可以指定现有 <xref:Microsoft.Data.SqlClient.SqlTransaction> 对象作为 <xref:Microsoft.Data.SqlClient.SqlBulkCopy> 构造函数中的参数。 在这种情况下，大容量复制操作在现有事务中进行，并且不对事务状态进行任何更改，即既不提交也不中止该事务。 此方法允许应用程序将大容量复制操作包含在带有其他数据库操作的事务中。 不过，如果未指定 <xref:Microsoft.Data.SqlClient.SqlTransaction> 对象并传递空引用，且连接有活动事务，异常就会抛出。   
  
如果由于出现错误而需要回滚整个大容量复制操作，或如果大容量复制应在可以回滚的较大进程中执行，你可以向 <xref:Microsoft.Data.SqlClient.SqlBulkCopy> 构造函数提供 <xref:Microsoft.Data.SqlClient.SqlTransaction> 对象。  
  
下面的控制台应用程序与第一个（非事务）示例类似，但有一个例外：在此示例中，大容量复制操作包含在较大的外部事务中。 发生主键冲突错误时，将回滚整个事务，并且不会向目标表添加任何行。  
  
> [!IMPORTANT]
>  除非已按[大容量复制示例设置](bulk-copy-example-setup.md)中所述创建了工作表，否则此示例将不会运行。 提供此代码是为了演示仅使用 SqlBulkCopy 时的语法。 如果源表和目标表位于同一 SQL Server 实例中，可以更便捷地使用 Transact-SQL `INSERT … SELECT` 语句复制数据。  
  
[!code-csharp[DataWorks SqlBulkCopy_ExternalTransaction#1](~/../sqlclient/doc/samples/SqlBulkCopy_ExternalTransaction.cs#1)]
  
## <a name="next-steps"></a>后续步骤
- [SQL Server 中的大容量复制操作](bulk-copy-operations-sql-server.md)
