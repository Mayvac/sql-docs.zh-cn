---
title: 筛选跟踪中的事件（SQL Server Profiler） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 18dea10c22e3800f1a9f099dbc94a188356e2733
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "85000249"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>在跟踪中筛选事件 (SQL Server Profiler)
  筛选器将限制跟踪内收集的事件。 如果没有设置筛选器，则跟踪输出中将返回选定事件类的所有事件。 并不一定要为跟踪设置筛选器。 但筛选器可使跟踪过程中造成的开销最小化。  
  
 可以使用 **“跟踪属性”** 或 **“跟踪模板属性”** 对话框中的 **“事件选择”** 选项卡向跟踪定义中添加筛选器。  
  
### <a name="to-filter-events-in-a-trace"></a>在跟踪中筛选事件  
  
1.  在 **“跟踪属性”** 或 **“跟踪模板属性”** 对话框中，单击 **“事件选择”** 选项卡。  
  
     **“事件选择”** 选项卡包含一个网格控件。 网格控件是包含所有可跟踪事件类的表。 每个事件类在表中占一行。 事件类可能略有不同，这取决于所连接服务器的类型和版本。 事件类由网格的“事件” **“事件”** 列进行标识，并按事件类别进行分组。 其余列则列出每个事件类可以返回的数据列。  
  
2.  单击 **“列筛选器”.**  
  
     此时将显示“编辑筛选器”**** 对话框。 “编辑筛选器”对话框包含一个比较运算符列表，可以使用这些运算符在跟踪中筛选事件****。  
  
3.  若要应用筛选器，请单击比较运算符，再键入要用于该筛选器的值。  
  
4.  单击“确定”。   
  
 **注意事项：**  
  
-   如果要对“事件选择”选项卡上的 **StartTime** 和 **EndTime** 数据列设置筛选条件，那么请确保：  
  
    -   输入的日期符合此格式： `YYYY/MM/DD HH:mm:sec`。  
  
         \- 或 -  
  
    -   在 **“常规选项”** 对话框中选中了 **“使用区域设置来显示日期和时间值”** 。 要查看“常规选项”  对话框，请在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的“工具”  菜单上单击“选项”  。  
  
         -以及-  
  
    -   输入的日期介于 1753 年 1 月 1 日到 9999 年 12 月 31 日之间。  
  
-   如果从 **osql** 实用工具或 **sqlcmd** 实用工具跟踪事件，则始终将 **%** 追加到 **TextData** 数据列上的筛选器。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
