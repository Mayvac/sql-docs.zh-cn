---
title: 设置作业历史记录日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48b0c0b72b7b27ca944e78603d2c574a8f4d27dc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "85001766"
---
# <a name="set-up-the-job-history-log"></a>Set Up the Job History Log
  本主题介绍如何设置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业历史记录日志。  
  
-   **开始之前：**  [安全性](#Security)  
  
-   **若要设置作业历史记录日志，请使用：**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="security"></a><a name="Security"></a> Security  
 有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> 使用 SQL Server Management Studio  
 **设置作业历史记录日志**  
  
1.  在“对象资源管理器”**** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开此实例。  
  
2.  右键单击“SQL Server 代理”****，然后单击“属性”****。  
  
3.  在 **“SQL Server 代理属性”** 对话框中，选择 **“历史记录”** 页。  
  
4.  从以下选项中选择：  
  
    1.  选中 **“限制作业历史记录日志的大小”**，然后键入作业历史记录日志的最大行数和每个作业的最大行数。  
  
    2.  选中 **“自动删除代理历史记录”**，然后指定时间段。这样，早于此时间段的历史记录将从日志中清除。  
  
## <a name="see-also"></a>另请参阅  
 [实现作业](implement-jobs.md)   
 [监视作业活动](monitor-job-activity.md)   
 [创建作业](create-jobs.md)  
  
  
