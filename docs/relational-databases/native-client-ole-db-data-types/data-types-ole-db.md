---
title: 数据类型 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- data types [OLE DB]
- OLE DB, data types
ms.assetid: 15953706-f0d1-45f5-a2eb-a8bd36e1a5fc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2813653f46573ad0e5b1db558fbc31de50e1071d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785477"
---
# <a name="data-types-ole-db"></a>数据类型 (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  若要 [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用 Native client OLE DB 提供程序来执行语句并处理结果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，您必须知道在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 行集内绑定参数或列时，Native Client OLE DB 提供程序如何将数据类型映射到 OLE DB 数据类型，以及何时使用**ITableDefinition**接口在中创建表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [行集和参数中的数据类型映射](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-rowsets-and-parameters.md)  
  
-   [ITableDefinition 中的数据类型映射](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md)  
  
-   [SSVARIANT 结构](../../relational-databases/native-client-ole-db-data-types/ssvariant-structure.md)  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
