---
description: Number 属性 (ADO)
title: ADO)  (数字属性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: rothja
ms.author: jroth
ms.openlocfilehash: 448842387c524326e51b104a0850f9ff503d35e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443069"
---
# <a name="number-property-ado"></a>Number 属性 (ADO)
指示唯一标识 [错误](../../../ado/reference/ado-api/error-object.md) 对象的数字。  
  
## <a name="return-value"></a>返回值  
 返回可能对应于其中一个[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)常量的**Long**值。  
  
## <a name="remarks"></a>备注  
 使用 **Number** 属性可确定发生的错误。 属性的值是与错误条件对应的唯一编号。  
  
 [Errors](../../../ado/reference/ado-api/errors-collection-ado.md)集合以十六进制格式返回 HRESULT (例如，0x80004005) 或 long 值 (例如 2147467259) 。 这些 Hresult 可以由基础组件（例如 OLE DB 甚至 OLE 本身）引发。 有关这些数字的详细信息，请参阅[OLE DB 程序员参考](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)中[OLE DB)  (错误](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd)*。*  
  
## <a name="applies-to"></a>适用于  
 [Error 对象](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>另请参阅  
 [Description、HelpContext、"帮助"、"NativeError"、"Number"、"Source" 和 "SQLState Properties" 示例 (VB) ](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、"帮助"、"NativeError"、"Number"、"Source" 和 "SQLState Properties" 示例 (VC + +) ](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description 属性](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext，帮助的属性](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source 属性（ADO 错误）](../../../ado/reference/ado-api/source-property-ado-error.md)
