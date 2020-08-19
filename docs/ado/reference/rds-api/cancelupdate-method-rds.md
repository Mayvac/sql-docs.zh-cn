---
description: CancelUpdate 方法 (RDS)
title: CancelUpdate 方法 (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CancelUpdate method [RDS]
ms.assetid: 76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e3f7180b812aab47f9388e25a64d9445e9b5c9e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439229"
---
# <a name="cancelupdate-method-rds"></a>CancelUpdate 方法 (RDS)
取消对 [记录集](../../../ado/reference/ado-api/recordset-object-ado.md) 对象的当前行或新行所做的任何更改。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件 (参阅 Windows 8 和 [Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416) ，以了解更多详细信息) 。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到 [WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>语法  
  
```  
  
DataControl.CancelUpdate  
```  
  
#### <a name="parameters"></a>参数  
 *DataControl*  
 表示 RDS 的对象变量 [。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) 对象。  
  
## <a name="remarks"></a>备注  
 OLE DB 的游标服务将保留原始值和更改缓存的副本。 调用 **CancelUpdate**时，更改的缓存将重置为空，并且所有绑定控件都将用原始数据进行刷新。  
  
## <a name="applies-to"></a>适用于  
 [DataControl 对象 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另请参阅  
 [CancelUpdate 方法示例 (VBScript) ](../../../ado/reference/rds-api/cancelupdate-method-example-vbscript.md)   
 [通讯簿命令按钮](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [ADO (取消方法) ](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [ (RDS) 的 Cancel 方法 ](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch 方法 (ADO) ](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate 方法 (ADO) ](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Refresh 方法 (RDS) ](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges 方法 (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


