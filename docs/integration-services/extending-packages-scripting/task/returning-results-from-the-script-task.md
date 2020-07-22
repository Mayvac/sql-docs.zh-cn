---
title: 从脚本任务返回结果 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 29698d7c7df768f2eb9f83bb33544fdaac75a2b4
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86910433"
---
# <a name="returning-results-from-the-script-task"></a>从脚本任务返回结果

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  脚本任务可使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 和可选的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性将状态信息返回到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行库，这些属性可用于在脚本任务完成后确定工作流的路径。  
  
## <a name="taskresult"></a>TaskResult  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 属性可报告任务是成功还是失败。 例如：  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a>ExecutionValue  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性还可以选择返回一个用户定义的对象，该对象可量化或提供有关脚本任务成功或失败的详细信息。 例如，FTP 任务使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性返回所传输的文件数。 执行 SQL 任务返回受其影响的行数。 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 还可用于确定工作流的路径。 例如：  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
