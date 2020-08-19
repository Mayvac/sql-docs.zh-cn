---
description: 组和用户 Append、ChangePassword 方法示例 (VB)
title: 组和用户追加，ChangePassword 方法示例 (VB) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ChangePassword method [ADOX], Visual Basic example
- Append method [ADOX], Visual Basic example
ms.assetid: c9426757-9cdd-4a95-b506-d3d011569109
author: rothja
ms.author: jroth
ms.openlocfilehash: 7aa335dc2aabdf05ab34a0245bb0aafc14b17cf1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439979"
---
# <a name="groups-and-users-append-changepassword-methods-example-vb"></a>组和用户 Append、ChangePassword 方法示例 (VB)
此示例演示了[组](../../../ado/reference/adox-api/groups-collection-adox.md)的[追加](../../../ado/reference/adox-api/append-method-adox-groups.md)方法，以及[用户](../../../ado/reference/adox-api/users-collection-adox.md)通过向系统添加新[组](../../../ado/reference/adox-api/group-object-adox.md)和新[用户](../../../ado/reference/adox-api/user-object-adox.md)的[附加](../../../ado/reference/adox-api/append-method-adox-users.md)方法。 新**组**将追加到新**用户**的 "**组**" 集合中。 因此，新 **用户** 将添加到 **该组**中。 此外， [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) 方法用于指定 **用户** 密码。  
  
> [!NOTE]
>  如果要连接到支持 Windows 身份验证的数据源提供程序，应在连接字符串中指定 **Trusted_Connection = yes** 或 **集成安全性 = SSPI** 而不是用户 ID 和密码信息。  
  
```  
' BeginGroupVB  
Sub Main()  
    On Error GoTo GroupXError  
  
    Dim cat As ADOX.Catalog  
    Dim usrNew As ADOX.User  
    Dim usrLoop As ADOX.User  
    Dim grpLoop As ADOX.Group  
  
    Set cat = New ADOX.Catalog  
  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';" & _  
        "jet oledb:system database=" & _  
        "'system.mdw'"  
  
    With cat  
        'Create and append new group with a string.  
        .Groups.Append "Accounting"  
  
        ' Create and append new user with an object.  
        Set usrNew = New ADOX.User  
        usrNew.Name = "Pat Smith"  
        usrNew.ChangePassword "", "Password1"  
        .Users.Append usrNew  
  
        ' Make the user Pat Smith a member of the  
        ' Accounting group by creating and adding the  
        ' appropriate Group object to the user's Groups  
        ' collection. The same is accomplished if a User  
        ' object representing Pat Smith is created and  
        ' appended to the Accounting group Users collection  
        usrNew.Groups.Append "Accounting"  
  
        ' Enumerate all User objects in the  
        ' catalog's Users collection.  
        For Each usrLoop In .Users  
            Debug.Print "  " & usrLoop.Name  
            Debug.Print "    Belongs to these groups:"  
            ' Enumerate all Group objects in each User  
            ' object's Groups collection.  
            If usrLoop.Groups.Count <> 0 Then  
                For Each grpLoop In usrLoop.Groups  
                    Debug.Print "    " & grpLoop.Name  
                Next grpLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next usrLoop  
  
        ' Enumerate all Group objects in the default  
        ' workspace's Groups collection.  
        For Each grpLoop In .Groups  
            Debug.Print "  " & grpLoop.Name  
            Debug.Print "    Has as its members:"  
            ' Enumerate all User objects in each Group  
            ' object's Users collection.  
            If grpLoop.Users.Count <> 0 Then  
                For Each usrLoop In grpLoop.Users  
                    Debug.Print "    " & usrLoop.Name  
                Next usrLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next grpLoop  
  
        ' Delete new User and Group objects because this  
        ' is only a demonstration.  
        ' These two line are commented out because the sub "OwnersX" uses  
        ' the group "Accounting".  
'        .Users.Delete "Pat Smith"  
'        .Groups.Delete "Accounting"  
  
    End With  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set usrNew = Nothing  
    Exit Sub  
  
GroupXError:  
  
    Set cat = Nothing  
    Set usrNew = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndGroupVB  
```  
  
## <a name="see-also"></a>另请参阅  
 [将方法追加 (ADOX 组) ](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [ADOX 用户 (追加方法) ](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [目录对象 (ADOX) ](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [ChangePassword 方法 (ADOX) ](../../../ado/reference/adox-api/changepassword-method-adox.md)   
 [组对象 (ADOX) ](../../../ado/reference/adox-api/group-object-adox.md)   
 [组集合 (ADOX) ](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [用户对象 (ADOX) ](../../../ado/reference/adox-api/user-object-adox.md)   
 [用户集合 (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
