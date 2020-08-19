---
description: Size 属性（ADO 流）
title: ADO Stream) 的大小属性 (|Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
author: rothja
ms.author: jroth
ms.openlocfilehash: 92b546b95c1033b6222a0acc99355c5e0906de21
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442129"
---
# <a name="size-property-ado-stream"></a>Size 属性（ADO 流）
指示流的大小（以字节数为单位）。  
  
## <a name="return-values"></a>返回值  
 返回一个 **长整型** 值，该值指定流的大小（以字节数为单位）。 默认值为流的大小; 如果流的大小未知，则为-1。  
  
## <a name="remarks"></a>备注  
 **大小** 只能与打开的 [流](../../../ado/reference/ado-api/stream-object-ado.md) 对象一起使用。  
  
> [!NOTE]
>  任意数量的位数可以存储在 **Stream** 对象中，仅受系统资源限制。 如果 **流** 包含的位数超过了可以用 **Long** 值表示的位数，则会截断 **大小** ，因此不能准确地表示 **流**的长度。  
  
## <a name="applies-to"></a>适用于  
 [流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [Size 属性（ADO 参数）](../../../ado/reference/ado-api/size-property-ado-parameter.md)
