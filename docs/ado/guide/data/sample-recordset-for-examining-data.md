---
description: 用于检查数据的示例记录集
title: 用于检查数据的示例记录集 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
author: rothja
ms.author: jroth
ms.openlocfilehash: f4c989667d5b4a5ceb3fb0c4f4d929e49be92e00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452909"
---
# <a name="sample-recordset-for-examining-data"></a>用于检查数据的示例记录集
首先，让我们看一下使用以下 SQL 查询返回的 **Recordset** 对象，该查询针对 Microsoft SQL Server 中的 Northwind 示例数据库执行。  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 生成的 **记录集** 对象包含下表所示的数据库中的所有生成。  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|叔叔 Bob 的随机是 Pears|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle Sauerkraut|45.6000|  
|51|Manjimup 是苹果|53.0000|  
|74|Longlife Tofu|10.0000|  
  
 如果你希望自己获得这些结果，请尝试以下 JScript 示例：  
  
-   [返回记录集的 JScript 示例](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
