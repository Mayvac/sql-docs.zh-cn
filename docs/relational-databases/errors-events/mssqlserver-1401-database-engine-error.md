---
description: MSSQLSERVER_1401
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cc47816715273a60fb49f1d209e4d531c205c5aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88335203"
---
# <a name="mssqlserver_1401"></a>MSSQLSERVER_1401
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>详细信息  
  
| Attribute | 值 |  
| :-------- | :---- |  
|产品名称|SQL Server|  
|事件 ID|1401|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBM_MASTERSTARTUP|  
|消息正文|数据库镜像主线程例程的启动因以下原因失败: %ls。 请纠正此错误的原因，然后重新启动 SQL Server 服务。|  
  
## <a name="explanation"></a>说明  
镜像控制线程启动失败。  
  
## <a name="user-action"></a>用户操作  
在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中，查看此消息之前的相关错误。 请纠正此错误的原因，然后重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务 (MSSQLSERVER)。  
  
## <a name="see-also"></a>另请参阅  
[启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务](~/database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
