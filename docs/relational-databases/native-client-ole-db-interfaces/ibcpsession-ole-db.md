---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d1b34d48691e44bafb46a748ea2dbf974f5238d2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762879"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  IBCPSession 接口公开了对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基于文件的大容量复制操作的支持****。 **IBCPSession**接口在与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话相同的级别下，在 Native Client OLE DB 提供程序中公开。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序中，数据源对象是会话对象的工厂，而大容量复制操作是在连接属性 SSPROP_ENABLEBULKCOPY 中指定的。 此外，SSPROP_ENABLEFASTLOAD 属性应当设置为 True。  
  
 调用 IDBCreateSession::CreateSession 方法随后将创建 BulkCopySession 对象********。 然后，可针对此 IBCPSession 对象的 IBCPSession 接口，采用极为相似的签名来调用通过 IBCPSession 对象公开的所有基于文件的大容量复制方法************。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序通过[IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)接口支持基于内存的大容量复制操作。  
  
 有关使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序进行大容量复制操作的详细信息，请参阅[执行大容量复制操作](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)。  
  
 有关演示如何使用 IBCPSession**** 接口的示例，请参阅 [IBCPSession::BCPDone (OLE DB)](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)。  
  
## <a name="in-this-section"></a>本节内容  
  
|方法|描述|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|在程序变量与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列之间创建绑定。|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|设置绑定到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中列的字段数。|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|设置大容量复制操作的选项。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|提交要发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的剩余行。|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|执行大容量复制操作。|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|初始化大容量复制结构，执行某些错误检查，验证数据和格式化文件名是否正确，然后打开文件。|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|从格式化文件中读取每一列的格式信息。|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|将每一列的格式信息写入格式化文件。|  
  
## <a name="see-also"></a>另请参阅  
 [接口 &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
