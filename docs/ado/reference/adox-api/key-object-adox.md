---
description: 项对象 (ADOX)
title: " (ADOX) 的密钥对象 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: rothja
ms.author: jroth
ms.openlocfilehash: d622adac64a37d956fc71ee1399c2d147b2f993a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439859"
---
# <a name="key-object-adox"></a>项对象 (ADOX)
表示数据库表中的主键或唯一键字段。  
  
## <a name="remarks"></a>备注  
 下面的代码创建一个新 **密钥**：  
  
```  
Dim obj As New Key  
```  
  
 使用 **Key** 对象的属性和集合，可以执行以下操作：  
  
-   标识具有 [Name](../../../ado/reference/adox-api/name-property-adox.md) 属性的键。  
  
-   确定该键是 primary、foreign 还是 unique，并具有 [Type](../../../ado/reference/adox-api/type-property-key-adox.md) 属性。  
  
-   使用 [columns](../../../ado/reference/adox-api/columns-collection-adox.md) 集合访问键的数据库列。  
  
-   指定带有 [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) 属性的相关表的名称。  
  
-   确定删除或更新包含 [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) 和 [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) 属性的主键时执行的操作。  
  
 本部分包含以下主题。  
  
-   [项对象属性、方法和事件](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另请参阅  
 [键 Append 方法、Key Type、RelatedColumn、RelatedTable 和 UpdateRule Properties Example (VB) ](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [列集合 (ADOX) ](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [项集合 (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
