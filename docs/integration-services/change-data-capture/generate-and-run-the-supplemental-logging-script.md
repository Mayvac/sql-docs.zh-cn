---
description: 生成和运行补充日志记录脚本
title: 生成和运行补充日志记录脚本 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a54fc6cab8ea15556aec82f810e2b678f1c78c7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484669"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>生成和运行补充日志记录脚本

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  使用“为捕获变更设置表”页可对 Oracle 源数据库运行一个将设置补充日志记录的脚本。  
  
 **运行补充日志记录脚本**  
  
 单击 **“运行脚本”** 可对为 CDC 实例定义的表运行补充日志记录脚本。 此脚本指示 Oracle 数据库在将 UPDATE 操作记录到捕获表时将有关的所有列写入其事务日志。 此脚本通常由 Oracle 系统管理员检查和执行。  
  
 您还可以使用 SQL * Plus 手动运行脚本。  
  
 **手动运行脚本**  
  
 单击 **“复制”** 将脚本粘贴到剪贴板。 打开 SQL* Plus 并且转到具有您的 Oracle 源数据库的目录。 将脚本粘贴到 SQL\*Plus 中，以便运行该脚本。  
  
 若要在文本文件中保存补充日志记录脚本，请单击 **“另存为”** 并且浏览到要保存该文件的位置。 为该文件提供一个名称，然后单击 **“保存”** 以便保存该文件。  
  
 单击 **“下一步”** 以便 [Generate Mirror Tables and CDC Capture Instances](../../integration-services/change-data-capture/generate-mirror-tables-and-cdc-capture-instances.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何创建 SQL Server 更改数据库实例](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [查看和生成补充日志记录脚本](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
