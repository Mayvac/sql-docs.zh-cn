---
description: Status 属性（ADO 记录集）
title: ADO 记录集)  (状态属性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
author: rothja
ms.author: jroth
ms.openlocfilehash: 7869ff91269d033b14a7f77e014da70962a1c1d5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441929"
---
# <a name="status-property-ado-recordset"></a>Status 属性（ADO 记录集）
指示与批更新或其他大容量操作有关的当前记录的状态。  
  
## <a name="return-value"></a>返回值  
 返回一个或多个 [RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md) 值的总和。  
  
## <a name="remarks"></a>备注  
 使用 **Status** 属性可查看在批更新过程中修改的记录挂起的更改。 你还可以使用**状态**属性来查看在大容量操作过程中失败的记录的状态，例如，在[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象上调用[Resync](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)或[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)方法时，或者将**记录集**对象的[Filter](../../../ado/reference/ado-api/filter-property.md)属性设置为书签的数组。 使用此属性，可以确定给定记录如何失败并相应地进行解决。  
  
## <a name="applies-to"></a>适用于  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [状态属性示例 (记录集)  (VB) ](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Status 属性示例 (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
