---
description: Cancel 方法 (ADO)
title: ) ADO (取消方法 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
author: rothja
ms.author: jroth
ms.openlocfilehash: 24d4beba2c703d2c8e21f51dd5bac9d06444a651
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451059"
---
# <a name="cancel-method-ado"></a>Cancel 方法 (ADO)
取消执行挂起的异步方法调用。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>备注  
 使用 **Cancel** 方法可终止异步方法调用的执行：即，使用 **adAsyncConnect**、 **adAsyncExecute**或 **adAsyncFetch** 选项调用的方法。  
  
 下表显示了在特定类型的对象上使用 **Cancel** 方法时终止的任务。  
  
|如果 *对象* 为|对此方法的最后一次异步调用被终止|  
|----------------------|-------------------------------------------------------------|  
|[命令](../../../ado/reference/ado-api/command-object-ado.md)|[运行](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Connection](../../../ado/reference/ado-api/connection-object-ado.md)|[Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) 或 [Open](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[记录](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)、 [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)、 [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)或 [Open](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|[打开](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[流](../../../ado/reference/ado-api/stream-object-ado.md)|[打开](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>适用于  

:::row:::
    :::column:::
        [命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
        [连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
        [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>另请参阅  
 [取消方法示例 (VB) ](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [取消方法示例 (VBScript) ](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [取消方法示例 (VC + +) ](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [ (RDS) 的 Cancel 方法 ](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch 方法 (ADO) ](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate 方法 (ADO) ](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate 方法 (RDS) ](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [ADO 命令 (执行方法) ](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [ADO 连接 (执行方法) ](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [开放式方法 (ADO 连接) ](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open 方法（ADO 记录集）](../../../ado/reference/ado-api/open-method-ado-recordset.md)
