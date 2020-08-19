---
description: FilterGroupEnum
title: FilterGroupEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: rothja
ms.author: jroth
ms.openlocfilehash: f8d3c510cfd9fa6c4a28f78005021465b9b0917b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443659"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
指定要从 [记录集中](../../../ado/reference/ado-api/recordset-object-ado.md)筛选的一组记录。  
  
|返回的常量|值|描述|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|用于仅查看受上次 [删除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)、重新 [同步](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)或 [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) 调用影响的记录的筛选器。|  
|**adFilterConflictingRecords**|5|用于查看上次批处理更新失败的记录的筛选器。|  
|**adFilterFetchedRecords**|3|用于查看当前缓存中的记录的筛选器，即，最后一次调用的结果是从数据库中检索记录。|  
|**adFilterNone**|0|删除当前筛选器并还原所有记录以供查看。|  
|**adFilterPendingRecords**|1|用于仅查看已更改但尚未发送到服务器的记录的筛选器。 仅适用于批处理更新模式。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 Package： **.com. 数据**  
  
|返回的常量|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums. FilterGroup|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>适用于  
 [Filter 属性](../../../ado/reference/ado-api/filter-property.md)
