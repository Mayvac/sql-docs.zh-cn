---
description: MSSQLSERVER_17065
title: MSSQLSERVER_17065 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17065 (Database Engine error)
ms.assetid: 63c2ba5a-be34-461e-bee1-03c25b396cd2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99135bdde28dfaa1cc6b786c7a5e11221abce96f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88333613"
---
# <a name="mssqlserver_17065"></a>MSSQLSERVER_17065
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>详细信息  
  
| Attribute | 值 |  
| :-------- | :---- |  
|产品名称|SQL Server|  
|事件 ID|17065|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|SQLASSERT_BOTH|  
|消息正文|SQL Server 断言:文件：\<%s>，行 = %d 失败的断言 = '%s' %s。 此错误可能与时间有关。 如果重新运行该语句后错误仍然存在，请使用 DBCC CHECKDB 来检查数据库的结构是否完整，或重新启动服务器以确保内存中的数据结构未破坏。|  
  
## <a name="explanation"></a>说明  
与时间有关的暂时性错误或内存中或磁盘上的数据损坏均可导致此错误。  
  
## <a name="user-action"></a>用户操作  
重新运行导致激发异常的语句。 如果错误是由与时间有关的事件导致的，则此错误可能不会重复发生。 如果问题仍然存在，请运行 DBCC CHECKDB 检查磁盘上的数据是否损坏。 重新启动服务器以确保内存中的数据结构未损坏。  
  
## <a name="see-also"></a>另请参阅  
[DBCC CHECKDB (Transact-SQL)](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
