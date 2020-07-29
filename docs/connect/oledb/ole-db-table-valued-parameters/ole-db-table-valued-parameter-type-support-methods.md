---
title: OLE DB 表值参数类型支持（方法）| Microsoft Docs
description: OLE DB 表值参数类型支持（方法）
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: d56e201a9c227358e54752bfcd08f718bcfbc371
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008748"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>OLE DB 表值参数类型支持（方法）
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  以下标准 OLE DB 方法支持表值参数：  
  
|方法|表值参数支持|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|在您了解表值参数的类型信息并且希望基于该类型信息实例化表值参数行集对象时使用。<br /><br /> 有关详细信息，请参阅[表值参数行集创建](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)中的“静态方案”。|  
|IOpenRowset::OpenRowset|在您不了解表值参数的类型信息并且希望基于从服务器检索的元数据信息实例化表值参数行集对象时使用。<br /><br /> 有关详细信息，请参阅[表值参数行集创建](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)中的“动态方案”。|  
|ISSCommandWithParameters::SetParameterInfo|若要指定表值参数命令参数，使用者应在 DBPARAMBINDINFO 结构的 pwszName 成员中将参数类型指定为“table”或“DBTYPE_TABLE”  。 ulParamSize  设置为 ~0。 有关详细信息，请参阅[执行包含表值参数的命令](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)中的“表值参数规范”。|  
|ISSCommandWithParameters::SetParameterProperties|设置特定于表值参数的属性，如架构名称、类型名称、列顺序和默认列。<br /><br /> 使用者在 SSPARAMPROPS 结构的 iOrdinal 中指定参数的序号  。 请求的属性集为 DBPROPSET_SQLSERVERPARAMETER。|  
|ISSCommandWithParameters::GetParameterInfo|获取某一指定命令的所有参数的类型。<br /><br /> 对于表值参数，DBPARAMINFO 结构中的 wType 字段的类型为 DBTYPE_TABLE  。 ulParamSize 字段将设置为 ~0 以指示未知长度  。|  
|ISSCommandWithParameters::GetParameterProperties|获取 DBTYPE_TABLE 类型的参数的附加类型信息。<br /><br /> 使用者在 SSPARAMPROPS 结构的 iOrdinal 成员中指定参数的序号  。 使用者可以请求 ISSCommandWithParameters::SetParameterProperties 下所列的 DBPROPSET_SQLSERVERPARAMETER 属性集中的任意属性。<br /><br /> 由于使用者不清楚表值参数类型，访问接口必须将 SSPROP_PARAM_TYPE_TYPENAME、SSPROP_PARAM_TYPE_SCHEMANAME 和 SSPROP_PARAM_TYPE_CATALOGNAME 设置为各自的正确值。 其余属性（SSPROP_PARAM_TABLE_DEFAULT_COLUMNS 和 SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER）将具有各自的默认值。 在使用者发现表值参数类型名称之后，它使用 IOpenRowset::OpenRowset 创建此表值参数的实例，同时指定表值参数类型的名称。 有关详细信息，请参阅[表值参数类型发现](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)。|  
|IRowsetInfo::GetProperties|获取表值参数行集属性。 使用者可以使用这些属性对绑定进行最佳设置。|  
|IColumnsRowset::GetColumnsRowset|检索有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表的元数据信息。 对于表值参数，同一接口提供有关各列的详细元数据信息，如下所示：<br /><br /> DBCOLUMN_FLAGS 通过 DBCOLUMNFLAGS_ISNULLABLE 位指示为空性。<br /><br /> DBCOLUMN_ISUNIQUE 指示列是否为标识列。<br /><br /> DBCOLUMN_COMPUTEMODE 指示是否可计算列。|  
|IAccessor::CreateAccessor|若要将表值参数行集对象绑定到命令参数，应创建一个取值函数，并将该函数的 wType 成员设置为 DBTYPE_TABLE  。 DBOBJECT 结构将包含 iid 成员中的 IID_IRowset 或其他任何有效行集对象接口  。 其余字段的处理方式类似于 DBTYPE_IUNKNOWN。|  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 表值参数类型支持](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [创建表值参数行集](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [使用表值参数 (OLE DB)](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
