---
description: 视图和字段集合示例 (VB)
title: " (VB) 的视图和字段集合示例 |Microsoft Docs"
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
- Views collection [ADOX], Visual Basic example
- Fields collection [ADOX]
ms.assetid: d8304849-3f80-4cf3-9425-529d2a8ebedd
author: rothja
ms.author: jroth
ms.openlocfilehash: 5cbf00fc32364c1077be44ebb791708f361ec4da
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2020
ms.locfileid: "88768976"
---
# <a name="views-and-fields-collections-example-vb"></a>视图和字段集合示例 (VB)
下面的代码演示如何使用 [Command](./command-property-adox.md) 属性和 [Recordset](../ado-api/recordset-object-ado.md) 对象检索视图的字段信息。  
  
```  
' BeginViewFieldsVB  
Sub ViewFields()  
    On Error GoTo ViewFieldsError  
  
    Dim cnn As New ADODB.Connection  
    Dim rst As New ADODB.Recordset  
    Dim fld As ADODB.Field  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Connection  
    cnn.Open _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Open the catalog  
    Set cat.ActiveConnection = cnn  
  
    ' Set the Source for the Recordset  
    Set rst.Source = cat.Views("AllCustomers").Command  
  
    ' Retrieve Field information  
    rst.Fields.Refresh  
    For Each fld In rst.Fields  
        Debug.Print fld.Name & ":" & fld.Type  
    Next  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set rst = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
ViewFieldsError:  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
  
    Set cat = Nothing  
    Set rst = Nothing  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndViewFieldsVB  
```  
  
## <a name="see-also"></a>另请参阅  
 [ActiveConnection 属性 (ADOX) ](./activeconnection-property-adox.md)   
 [目录对象 (ADOX) ](./catalog-object-adox.md)   
 [Command 属性 (ADOX) ](./command-property-adox.md)   
 [视图对象 (ADOX) ](./view-object-adox.md)   
 [视图集合 (ADOX)](./views-collection-adox.md)