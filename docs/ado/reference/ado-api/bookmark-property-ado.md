---
description: Bookmark 属性 (ADO)
title: " (ADO) 的书签属性 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
author: rothja
ms.author: jroth
ms.openlocfilehash: b3ab83bb44bca7598074eb81d832ca9ed9b954d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451109"
---
# <a name="bookmark-property-ado"></a>Bookmark 属性 (ADO)
指示一个书签，该书签唯一标识 [recordset](../../../ado/reference/ado-api/recordset-object-ado.md) 对象中的当前记录，或将 **记录集** 对象中的当前记录设置为有效书签标识的记录。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回一个 **变量** 表达式，该表达式的计算结果为有效书签。  
  
## <a name="remarks"></a>备注  
 使用 " **书签** " 属性可以保存当前记录的位置并随时返回到该记录。 书签仅适用于支持书签功能的 **记录集** 对象。  
  
 打开 **Recordset** 对象时，它的每个记录都具有唯一的书签。 若要保存当前记录的书签，请将 **bookmark** 属性的值分配给变量。 若要在移动到不同记录后随时快速返回到该记录，请将 **记录集** 对象的 **Bookmark** 属性设置为该变量的值。  
  
 用户可能无法查看书签的值。 此外，用户不应期望书签直接可比较，因为引用同一记录的两个书签可能具有不同的值。  
  
 如果使用[Clone](../../../ado/reference/ado-api/clone-method-ado.md)方法创建**Recordset**对象的副本，则原始副本和重复**记录集**对象的**书签**属性设置都是相同的，并且可以互换使用。 但是，不能使用不同 **记录集** 对象的书签，即使它们是从同一源或命令创建的也是如此。  
  
> [!NOTE]
>  **远程数据服务使用情况** 当在客户端 **记录集** 对象上使用时， **书签** 属性始终可用。  
  
## <a name="applies-to"></a>适用于  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [BOF、EOF 和 Bookmark 属性示例 (VB) ](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF、EOF 和 Bookmark 属性示例 (VC + +) ](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Supports 方法](../../../ado/reference/ado-api/supports-method.md)
