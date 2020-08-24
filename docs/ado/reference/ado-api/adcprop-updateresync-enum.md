---
description: ADCPROP_UPDATERESYNC_ENUM
title: ADCPROP_UPDATERESYNC_ENUM |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
author: rothja
ms.author: jroth
ms.openlocfilehash: b4097bcdeb5460776017ce7a120ff43aa7a4420f
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2020
ms.locfileid: "88760241"
---
# <a name="adcprop_updateresync_enum"></a>ADCPROP_UPDATERESYNC_ENUM
指定 [UpdateBatch](./updatebatch-method.md) 方法是否后跟隐式重新 [同步](./resync-method.md) 方法操作，如果是，则为该操作的范围。  
  
|返回的常量|值|说明|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|调用与所有其他 ADCPROP_UPDATERESYNC_ENUM 成员的组合值的重新 **同步** 。|  
|**adResyncAutoIncrement**|1|默认。 尝试检索数据源自动递增或生成的列的新标识值，如 Microsoft Jet AutoNumber 字段或 Microsoft SQL Server 的标识列。|  
|**adResyncConflicts**|2|针对因并发冲突而失败的更新或删除操作的所有行调用重新 **同步** 。|  
|**adResyncInserts**|8|为所有成功插入的行调用重新 **同步** 。 但是，自动增量列值不会重新同步。 相反，新插入行的内容会根据现有的主键值进行重新同步。 如果主键是自动增量值，则重新 **同步** 不会检索目标行的内容。 若要自动递增自动增量主键值， **UpdateBatch**请调用具有组合值**adResyncAutoIncrement**  +  **adResyncInserts**的 UpdateBatch。|  
|**adResyncNone**|0|不会调用 **Resync**。|  
|**adResyncUpdates**|4|为所有已成功更新的行调用重新 **同步** 。|  
  
## <a name="applies-to"></a>适用于  
 [Update Resync 属性 - 动态 (ADO)](./update-resync-property-dynamic-ado.md)