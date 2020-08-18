---
description: MSSQLSERVER_1101
title: MSSQLSERVER_1101 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59a6908bbeb0ef2a6a96b84e9abbee952e4aab78
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88336963"
---
# <a name="mssqlserver_1101"></a>MSSQLSERVER_1101
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>详细信息  
  
| Attribute | 值 |  
| :-------- | :---- |  
|产品名称|SQL Server|  
|事件 ID|1101|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|NOALLOCPG|  
|消息正文|由于文件组“%.\*ls”中的磁盘空间不足，无法为数据库“%.*ls”分配新页。 请删除文件组中的对象、将其他文件添加到文件组或者为文件组中的现有文件启用自动增长，以便增加必要的空间。|  
  
## <a name="explanation"></a>说明  
文件组中没有可用的磁盘空间。  
  
## <a name="user-action"></a>用户操作  
以下操作可能会使空间在文件组中可用。  
  
-   打开 AUTOGROW。  
  
-   向文件组添加更多文件。  
  
-   通过删除文件组中不必要的索引或表来释放磁盘空间。  
  
