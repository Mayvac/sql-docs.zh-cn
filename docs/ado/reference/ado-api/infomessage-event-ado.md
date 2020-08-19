---
description: InfoMessage 事件 (ADO)
title: InfoMessage 事件 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
author: rothja
ms.author: jroth
ms.openlocfilehash: d3957c6cf6843ba27c54fb5a979901bd4a656c2e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443449"
---
# <a name="infomessage-event-ado"></a>InfoMessage 事件 (ADO)
只要在**ConnectionEvent**操作过程中出现警告，就会调用**InfoMessage**事件。  
  
## <a name="syntax"></a>语法  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>参数  
 *pError*  
 一个 [错误](../../../ado/reference/ado-api/error-object.md) 对象。 此参数包含返回的任何错误。 如果返回多个错误，则枚举 **错误** 集合以找到它们。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状态值。 如果出现警告， *adStatus* 将设置为 **AdStatusOK** ，而 *pError* 将包含警告。  
  
 在此事件返回之前，将此参数设置为 **adStatusUnwantedEvent** 以防止后续通知。  
  
 *pConnection*  
 [连接](../../../ado/reference/ado-api/connection-object-ado.md)对象。 发生警告的连接。 例如，打开**连接**对象或对**连接**执行[命令](../../../ado/reference/ado-api/command-object-ado.md)时，可能会出现警告。  
  
## <a name="see-also"></a>另请参阅  
 [ (VC + + 的 ADO 事件模型示例) ](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 事件处理程序摘要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
