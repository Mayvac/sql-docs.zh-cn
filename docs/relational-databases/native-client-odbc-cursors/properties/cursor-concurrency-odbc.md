---
title: 游标并发（ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 809fbb485e18093b3f9e3e68d6ab6cf084787692
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85760696"
---
# <a name="cursor-concurrency-odbc"></a>游标并发 (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  和游标类型一样，游标操作也受应用程序设置的并发选项的影响。 并发选项是使用[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_CONCURRENCY 选项设置的。 并发类型包括：  
  
-   只读 (SQL_CONCUR_READONLY)  
  
-   值 (SQL_CONCUR_VALUES)  
  
-   行版本 (SQL_CONCUR_ROWVER)  
  
-   锁 (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>另请参阅  
 [游标属性](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
