---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24d5ea772aa3bc698a3bcc60dcc07e38eb23ed92
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781017"
---
# <a name="mssqlserver_1458"></a>MSSQLSERVER_1458
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>详细信息  
  
| Attribute | 值 |  
| :-------- | :---- |  
|产品名称|SQL Server|  
|事件 ID|1458|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBM_FAILREDO_ON_PRIMARY|  
|消息正文|'%.*ls' 数据库的主体副本遇到错误 %d，状态 %d，严重性 %d。 数据库镜像已挂起。 请尝试纠正错误条件，然后继续镜像。|  
  
## <a name="explanation"></a>说明  
该消息指出主体数据库遇到了导致数据库镜像被挂起的错误。  
  
## <a name="user-action"></a>用户操作  
导致此错误的大多数原因可以自我更正。 如果该问题仍然存在，重新启动数据库或服务器实例通常可以更正该问题。 有关详细信息，请查看每个伙伴中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志以获得出现在此消息之前的关联错误。  
  
## <a name="see-also"></a>另请参阅  
[监视数据库镜像 (SQL Server)](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
