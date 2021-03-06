---
description: 组对象 (ADOX)
title: 组对象 (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
author: rothja
ms.author: jroth
ms.openlocfilehash: 21514bbcbe91e1320a4a2806e545d5f7b40df8d3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984428"
---
# <a name="group-object-adox"></a>组对象 (ADOX)
表示在受保护的数据库中具有访问权限的组帐户。  
  
## <a name="remarks"></a>注解  
 [目录](./catalog-object-adox.md)的[Groups](./groups-collection-adox.md)集合表示所有目录的组帐户。 [用户](./user-object-adox.md)的**Groups**集合仅表示该用户所属的组。  
  
 利用 **组** 对象的属性、集合和方法，您可以：  
  
-   标识具有 [Name](./name-property-adox.md) 属性的组。  
  
-   使用 [GetPermissions](./getpermissions-method-adox.md) 和 [SetPermissions](./setpermissions-method-adox.md) 方法确定组是否具有读取、写入或删除权限。  
  
-   访问具有 [用户](./users-collection-adox.md) 集合的组中的成员身份的用户帐户。  
  
-   使用 [properties](../ado-api/properties-collection-ado.md) 集合访问特定于提供程序的属性。  
  
 本部分包含以下主题。  
  
-   [组对象属性、方法和事件](./group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另请参阅  
 [组集合 (ADOX) ](./groups-collection-adox.md)   
 [用户集合 (ADOX)](./users-collection-adox.md)