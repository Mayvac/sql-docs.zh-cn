---
description: 字段集合 (ADO)
title: 字段集合 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 1374770ab86038d50c4dd8cafabff328a5275ace
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443729"
---
# <a name="fields-collection-ado"></a>字段集合 (ADO)
包含[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)或[Record](../../../ado/reference/ado-api/record-object-ado.md)对象的所有[字段](../../../ado/reference/ado-api/field-object.md)对象。  
  
## <a name="remarks"></a>备注  
 **记录集**对象包含由**字段**对象组成的**字段**集合。 每个 **字段** 对象都对应于 **记录集中**的一列。 您可以通过对集合调用[Refresh](../../../ado/reference/ado-api/refresh-method-ado.md)方法，在打开**记录集**之前填充**字段**集合。  
  
> [!NOTE]
>  有关如何使用**字段**对象的更详细说明，请参阅**字段**对象主题。  
  
 **字段**集合具有[Append](../../../ado/reference/ado-api/append-method-ado.md)方法，该方法暂时创建**字段**对象并将其添加到集合，并使用**Update**方法完成所有添加或删除操作。  
  
 **记录**对象有两个可以使用[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)常量进行索引的特殊字段。 一个常量访问包含 **记录**的默认流的字段，另一个字段访问包含该 **记录**的绝对 URL 字符串的字段。  
  
 某些提供程序 (例如，[用于 Internet 发布的 Microsoft OLE DB 提供程序](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) 可以使用**记录**或**记录集**的可用字段子集填充**字段**集合。 其他字段将不会添加到集合中，直到它们首先被名称引用或由您的代码进行索引。  
  
 如果尝试按名称引用不存在的字段，新的**字段**对象将追加到[状态](../../../ado/reference/ado-api/status-property-ado-field.md)为 " **adFieldPendingInsert**" 的**字段**集合。 调用 [Update](../../../ado/reference/ado-api/update-method.md)时，如果提供程序允许，ADO 将在数据源中创建一个新字段。  
  
 本部分包含以下主题。  
  
-   [字段集合属性、方法和事件](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另请参阅  
 [字段对象](../../../ado/reference/ado-api/field-object.md)
