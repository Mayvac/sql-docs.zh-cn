---
description: SQLCloseCursor
title: SQLCloseCursor |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 58cb99fa0c7416335d71bf4d92f5129272131ea3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428329"
---
# <a name="sqlclosecursor"></a>SQLCloseCursor
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SQLCloseCursor**使用*选项*值 SQL_CLOSE 来替换[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) 。 收到 **SQLCloseCursor**后， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序将放弃挂起的结果集行。 请注意，如果 **SQLCloseCursor**不改变任何存在) ，语句的列和参数绑定 (。  
  
## <a name="see-also"></a>另请参阅  
 [SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331)   
 [ODBC API 实现细节](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
