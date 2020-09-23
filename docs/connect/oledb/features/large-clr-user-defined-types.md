---
title: 大型 CLR 用户定义类型 | Microsoft Docs
description: 了解不同 SQL Server 版本的公共语言运行时中用户定义类型的大小限制和相关行为。
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fdc52df9307bbe4ce3e826ca682d787e1c11506
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861464"
---
# <a name="large-clr-user-defined-types"></a>大型 CLR 用户定义类型
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  在 SQL Server 2005 中，公共语言运行时 (CLR) 中的用户定义类型 (UDT) 已限制为最大 8,000 字节。 这一限制在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更高版本中已取消。 CLR UDT 现在以针对大型对象 (LOB) 类型的类似方式处置。 也就是说，小于或等于 8,000 字节的 UDT 在行为上与 SQL Server 2005 中相同，但支持更大的 UDT 并且将其大小报告为“无限制”。  
  
 有关详细信息，请参阅[大型 CLR 用户定义类型 (OLE DB)](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md)。  
  
## <a name="use-cases"></a>用例   
  
 对于 OLE DB，对大型 UDT 的支持包括能够通过使用 ISequentialStream 绑定在服务器之间传送 UDT 值。  
  
 小于或等于 8,000 字节的 UDT 在行为上与 SQL Server 2005 中相同。 对于 OLE DB，仍可以通过使用 ISequentialStream 绑定来流式传输小型 UDT。  
  
 有时候，本机代码将必须理解 CLR UDT 的内容，但将不必实例化托管对象。 在此情况下，您可以使用自定义序列化将服务器上的 UDT 值转换为客户端的已知格式。  
  
 对于具有现有数据访问代码的应用程序，您可以通过在本机 API 中检索 UDT 并通过在混合模式应用程序中使用 C++ CLI interop 实例化它们，在客户端上利用 CLR UDT 行为。  
  
## <a name="see-also"></a>另请参阅  
 [适用于 SQL Server 的 OLE DB 驱动程序功能](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
