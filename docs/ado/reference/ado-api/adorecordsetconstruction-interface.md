---
description: ADORecordsetConstruction 接口
title: ADORecordsetConstruction 接口 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 3dd1000dce8308ada4044eb9f043097f8767a9c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451319"
---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction 接口
**ADORecordsetConstruction**接口用于从 c/c + + 应用程序中的 OLE DB**行**集对象构造 ADO**记录集**对象。  
  
 此接口支持以下属性：  
  
## <a name="properties"></a>属性  
  
|属性|描述|  
|-|-|  
|[章节](../../../ado/reference/ado-api/chapter-property-ado.md)|读/写。<br />获取/设置此 ADO**记录集**对象的 OLE DB**章节**对象。|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|读/写。<br />获取/设置此 ADO**记录集**对象的 OLE DB **RowPosition**对象。|  
|[行集](../../../ado/reference/ado-api/rowset-property-ado.md)|读/写。<br />获取/设置此 ADO**记录集**对象的 OLE DB**行集**对象。|  
  
## <a name="methods"></a>方法  
 无。  
  
## <a name="events"></a>事件  
 无。  
  
## <a name="remarks"></a>备注  
 给定 OLE DB **行集** 对象 (`pRowset`) 时，ADO **记录集** 对象的构造 (`adoRs`) 数量到以下三个基本操作：  
  
1.  创建 ADO **记录集** 对象：  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  查询**Recordset**对象上的**IADORecordsetConstruction**接口：  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  调用 `IADORecordsetConstruction::put_Rowset` 属性方法，设置 `Rowset` ADO 对象上的 OLE DB 对象 `Recordset` ：  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 生成的 `adoRs` 对象现在表示从 OLE DB**行集**对象构造的 ADO**记录集**对象。  
  
 还可以从 OLE DB**章节**或**ROWPOSITION**对象构造 ADO**记录集**对象。  
  
## <a name="requirements"></a>要求  
 **版本：** ADO 2.0 及更高版本  
  
 **库：** msado15.dll  
  
 **UUID：** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>另请参阅  
 [ADO)  (Recordset 对象 ](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Rowset 属性 (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
