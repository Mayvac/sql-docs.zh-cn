---
title: 不确定性内容模型 | Microsoft Docs
description: 举例说明了如何使用包含非确定性内容模型的 XML 架构。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cd6ab4f4bb7bc6b867ffc32937cc58f202b20af0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729173"
---
# <a name="non-deterministic-content-models"></a>不确定性内容模型
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拒绝包含不确定性内容模型的 XML 架构。  
  
 不过从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1 开始，如果匹配项约束为 0、1 或不受限制，则会接受不确定性内容模型。  
  
## <a name="example-non-deterministic-content-model-rejected"></a>示例：已拒绝的不确定性内容模型  
 下面的示例尝试创建具有不确定的内容模型的 XML 架构。 此代码失败，因为不清楚 `<root>` 元素应有一个包含两个 `<a>` 元素的序列，还是 `<root>` 元素应有两个序列，其中每个序列有一个 `<a>` 元素。  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 可以通过将匹配项约束移动到一个唯一的位置来修复此架构。 例如，可以将此约束移动到包含序列粒子：  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 也可以将此约束移动到被包含元素：  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a>示例：已接受的不确定性内容模型  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本中，会拒绝下面的架构。  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [在服务器上使用 XML 架构集合的要求和限制](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
