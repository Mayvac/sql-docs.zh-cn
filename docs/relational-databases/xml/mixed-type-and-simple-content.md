---
title: 混合类型和简单内容 | Microsoft Docs
description: 查看一个示例，该示例显示 SQL Server 不支持创建将混合类型限制为简单内容的 XML 架构。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 990ead43919e80a910860ee15a3758a36e2a1f93
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715135"
---
# <a name="mixed-type-and-simple-content"></a>混合类型和简单内容
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支持将混合类型限制为简单内容。  
  
## <a name="example"></a>示例  
 在下面的 XML 架构集合中， `myComplexTypeA` 是可以清空的复杂类型。 即它的两个元素都将 `minOccurs` 设置为 0。 与在 `myComplexTypeB` 声明中一样，不支持将此限制为简单内容的尝试。 因此，下面的 XML 架构集合创建语句将失败：  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [在服务器上使用 XML 架构集合的要求和限制](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
