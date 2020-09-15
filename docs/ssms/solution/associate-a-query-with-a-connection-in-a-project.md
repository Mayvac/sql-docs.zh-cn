---
description: 将查询与项目中的连接关联
title: 将查询与项目中的连接关联
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], query associations
- projects [SQL Server Management Studio], connections
- projects [SQL Server Management Studio], query connections
- query associations [SQL Server Management Studio]
ms.assetid: c9625ae0-29c1-4179-a709-51b7e2f9e23d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 511ee704f1e9e0cc256b0265ba882be8205c7860
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88316273"
---
# <a name="associate-a-query-with-a-connection-in-a-project"></a>将查询与项目中的连接关联
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
如果查询在创建时没有连接，或者将查询从一个项目移动到另一个项目，则该查询将不与当前项目中的连接关联。  
  
### <a name="to-associate-a-query-with-a-connection-in-a-project"></a>将查询与项目中的连接关联  
  
1.  如果查询在查询编辑器中处于打开状态，请右键单击查询编辑器的空白区域，指向“连接”****，再单击“连接”****。 如果查询未打开，请在解决方案资源管理器中双击查询，以连接该查询。  
  
2.  在“连接到数据库引擎”**** 对话框中，提供连接信息。 如果连接信息与现有连接匹配，该查询将与此连接关联。  
  
## <a name="see-also"></a>另请参阅  
[解决方案资源管理器](../../ssms/solution/solution-explorer.md)  
[更改与查询关联的连接](../../ssms/solution/change-the-connection-associated-with-a-query.md)  
[查看或更改项目中的连接属性](../../ssms/solution/view-or-change-the-properties-of-a-connection-in-a-project.md)  
  
