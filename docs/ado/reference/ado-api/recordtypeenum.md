---
description: RecordTypeEnum
title: RecordTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
author: rothja
ms.author: jroth
ms.openlocfilehash: a1e5a43d2b53a76a21d79ce671004e139dab5e20
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771986"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
指定 [记录](./record-object-ado.md) 对象的类型。  
  
|返回的常量|Value|说明|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|指示 (不包含) 子节点的 *简单* 记录。|  
|**adCollectionRecord**|1|指示 (包含) 子节点的 *集合* 记录。|  
|**adRecordUnknown**|-1|指示此 **记录** 的类型是未知的。|  
|**adStructDoc**|2|指示表示 COM 结构化文档的一种特殊类型的 *集合* 记录。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 这些常量没有 ADO/WFC 等效项。  
  
## <a name="applies-to"></a>适用于  
 [RecordType 属性 (ADO)](./recordtype-property-ado.md)