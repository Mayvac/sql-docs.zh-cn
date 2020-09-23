---
description: SQLXML 接口
title: SQLXML 接口 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bac370362700a4a5f1b500ebd1b01eb8063d5f03
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88396263"
---
# <a name="sqlxml-interface"></a>SQLXML 接口

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

JDBC 驱动程序提供对 JDBC 4.0 API 的支持，后者引入了 java.sql.SQLXML 接口。 SQLXML 接口定义与 XML 数据交互以及操作 XML 数据的方法。 数据类型 SQLXML  映射到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]xml  数据类型。  
  
SQLXML 接口提供用于以 String****、Reader**** 或 Writer****，或者 Stream**** 形式访问 XML 值的方法。 XML 值还可以通过 Source 来访问，或者设置为 Result，两者与 XML 分析器 API（如文档对象模型 (DOM)、Simple API for XML (SAX) 和 Streaming API for XML (StAX)）以及 XSLT 转换和 XPath 一起使用********。  
  
## <a name="remarks"></a>注解  

下表介绍了 SQLXML 接口中定义的方法：  
  
|方法语法|方法说明|  
|-------------------|------------------------|  
|[void free()](https://go.microsoft.com/fwlink/?LinkId=131685)|此方法释放 SQLXML 对象以及它所持有的资源。|  
|[InputStream getBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131754)|返回一个用于从 SQLXML 中读取数据的输入流。|  
|[Reader getCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131755)|将 XML 数据作为 java.io.Reader 对象或字符流返回****。|  
|[T extends Source T getSource(Class\<T> sourceClass)](https://go.microsoft.com/fwlink/?LinkId=131756)|返回 Source****，用于读取此 SQLXML**** 对象指定的 XML**** 值。<br /><br /> **** 注意：getSource 方法支持下列源：javax.xml.transform.dom.DOMSource、javax.xml.transform.sax.SAXSource、javax.xml.transform.stax.StAXSource 和 java.io.InputStream。|  
|[String getString()](https://go.microsoft.com/fwlink/?LinkId=131757)|返回此 SQLXML 对象所指定的 XML 值的字符串表示形式****。|  
|[OutputStream setBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131758)|检索可用于写入此 SQLXML 对象所表示的 XML 值的流****。|  
|[Writer setCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131759)|返回可用于写入此 SQLXML 对象所表示的 XML 值的流****。|  
|[T extends Result T setResult(Class\<T> resultClass)](https://go.microsoft.com/fwlink/?LinkId=131760)|返回 Result****，用于设置此 SQLXML**** 对象指定的 XML**** 值。<br /><br /> **** 注意：setResult 方法支持下列源：javax.xml.transform.dom.DOMResult、javax.xml.transform.sax.SAXResult、javax.xml.transform.stax.StaxResult 和 java.io.OutputStream。|  
|[void setString(String value)](https://go.microsoft.com/fwlink/?LinkId=131762)|将此 SQLXML 对象所指定的 XML 值设置为指定的字符串表示形式****。|  
  
应用程序只能从/向 SQLXML 对象中读取/写入 XML 值一次。  
  
调用 free() 方法后，SQLXML 对象将变为无效，既不可读也不可写。 如果应用程序尝试对该 SQLXML 对象调用 free() 方法以外的方法，将引发异常。  
  
当应用程序调用下列任意 getter 方法时，SQLXML 对象将变为既不可读也不可写：getSource、getCharacterStream、getBinaryStream 和 getString。  
  
当应用程序调用下列任意 setter 方法时，SQLXML 对象将变为既不可写也不可读：setResult、setCharacterStream、setBinaryStream 和 setString。  
  
## <a name="see-also"></a>另请参阅  

[支持 XML 数据](../../connect/jdbc/supporting-xml-data.md)  
