---
title: GetPermissions 方法（ADOX） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
author: rothja
ms.author: jroth
ms.openlocfilehash: 221b340cd8df2a9bfc2bfdb19e3e46b18d3a2c57
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942699"
---
# <a name="getpermissions-method-adox"></a>GetPermissions 方法 (ADOX)
返回[组](../../../ado/reference/adox-api/group-object-adox.md)或[用户](../../../ado/reference/adox-api/user-object-adox.md)对对象或对象容器的权限。  
  
## <a name="syntax"></a>语法  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>返回值  
 返回一个**长整型**值，该值指定包含组或用户对对象的权限的位掩码。 此值可以是一个或多个[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)常量。  
  
#### <a name="parameters"></a>参数  
 *名称*  
 一个**变量**值，指定要为其设置权限的对象的名称。 如果要获取对象容器的权限，请将 "*名称*" 设置为 null 值。  
  
 *ObjectType*  
 一个**长整型**值，可以是[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)常量之一，它指定要获取其权限的对象的类型。  
  
 *ObjectTypeId*  
 可选。 一个**变量**值，指定 OLE DB 规范未定义的提供程序对象类型的 GUID。 如果*ObjectType*设置为**adPermObjProviderSpecific**，则此参数是必需的;否则，不使用此方法。  
  
## <a name="applies-to"></a>应用到  

:::row:::
    :::column:::
        [组对象 (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)  
    :::column-end:::
    :::column:::
        [用户对象 (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>另请参阅  
 [GetPermissions 和 SetPermissions 方法示例（VB）](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Name 属性（ADOX）](../../../ado/reference/adox-api/name-property-adox.md)   
 [SetPermissions 方法 (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
