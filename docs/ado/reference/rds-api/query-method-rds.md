---
description: Query 方法 (RDS)
title: " (RDS) 的 Query 方法 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
author: rothja
ms.author: jroth
ms.openlocfilehash: b4d883d9498622c5118ecfcaa418bd734e4356c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438859"
---
# <a name="query-method-rds"></a>Query 方法 (RDS)
使用有效的 SQL 查询字符串返回 [记录集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，Windows 操作系统中不再包含 RDS 服务器组件 (参阅 Windows 8 和 [Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416) ，以了解更多详细信息) 。 在 Windows 的未来版本中将删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到 [WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>语法  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>参数  
 *Recordset*  
 表示 **Recordset** 对象的对象变量。  
  
 *DataFactory*  
 表示 [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) 对象的对象变量。  
  
 *Connection*  
 一个包含服务器连接信息的 **字符串** 值。 这类似于 [连接](../../../ado/reference/rds-api/connect-property-rds.md) 属性。  
  
 *查询*  
 一个包含 SQL 查询的 **字符串** 。  
  
## <a name="remarks"></a>备注  
 查询应使用数据库服务器的 SQL 语言。 如果执行的查询出现错误，则返回结果状态。 **查询**方法不对**查询**字符串执行任何语法检查。  
  
## <a name="applies-to"></a>适用于  
 [DataFactory 对象 (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>另请参阅  
 [DataFactory 对象、Query 方法和 CreateObject 方法示例 (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


