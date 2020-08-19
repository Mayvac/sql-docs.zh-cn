---
description: ParentCatalog 属性 (ADOX)
title: ParentCatalog 属性 (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User::get_ParentCatalog
- _Column::ParentCatalog
- _Table::put_ParentCatalog
- _Group::put_ParentCatalog
- _Column::get_ParentCatalog
- _Table::PutParentCatalog
- _Group::putref_ParentCatalog
- _Group::ParentCatalog
- _Column::PutParentCatalog
- _Column::put_ParentCatalog
- _Group::get_ParentCatalog
- _User::put_ParentCatalog
- _User::putref_ParentCatalog
- _Table::get_ParentCatalog
- _Group::PutParentCatalog
- _Table::ParentCatalog
- _Column::GetParentCatalog
- _Table::PutRefParentCatalog
- _User::GetParentCatalog
- _Table::GetParentCatalog
- _Table::putref_ParentCatalog
- _User::PutParentCatalog
- _User::ParentCatalog
- _User::PutRefParentCatalog
- _Group::GetParentCatalog
- _Group::PutRefParentCatalog
helpviewer_keywords:
- ParentCatalog property [ADOX]
ms.assetid: a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273
author: rothja
ms.author: jroth
ms.openlocfilehash: 93d15cdac3d8f7a47c74a783d176d806271f68a3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439719"
---
# <a name="parentcatalog-property-adox"></a>ParentCatalog 属性 (ADOX)
指定表、用户或列对象的父目录，以提供对特定于访问接口的属性的访问。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置并返回 [目录](../../../ado/reference/adox-api/catalog-object-adox.md) 对象。 将 **ParentCatalog** 设置为打开的 **目录** 后，便可以在将表或列追加到 **目录** 集合之前访问特定于提供程序的属性。  
  
## <a name="remarks"></a>备注  
 某些数据访问接口允许仅在创建时写入特定于提供程序的属性值：也就是说，将表或列追加到其 **目录** 集合中。 若要在将这些对象附加到**目录**之前访问这些属性，请先在**ParentCatalog**属性中指定**目录**。  
  
 将表或列追加到与**ParentCatalog**不同的**目录**时出错。  
  
## <a name="applies-to"></a>适用于  

:::row:::
    :::column:::
        [列对象 (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
    :::column-end:::
    :::column:::
        [表对象 (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [用户对象 (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>另请参阅  
 [ParentCatalog 属性示例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
