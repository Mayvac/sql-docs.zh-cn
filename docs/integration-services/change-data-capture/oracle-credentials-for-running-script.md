---
title: 用于运行脚本的 Oracle 凭据 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d6e7cd34cbbccded9d8b92a9013e988980d8622f
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86917160"
---
# <a name="oracle-credentials-for-running-script"></a>Oracle Credentials for Running Script

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  若要从 Oracle CDC 设计器控制台运行 Oracle 补充日志记录脚本，程序将提示您输入正运行该脚本的 Oracle 用户的凭据。 若要运行该脚本，Oracle 用户必须对要捕获的所有表具有 ALTER TABLE 权限，并且对 DBA_LOG_GROUPS 视图具有 SELECT 权限。  
  
## <a name="task-list"></a>任务列表  
 在此对话框中输入以下信息：  
  
 **身份验证**  
  
 选择以下方案之一：  
  
-   **Windows 身份验证**：选择此选项可使用当前的 Windows 域凭据。 只有当 Oracle 数据库配置为使用 Windows 身份验证时，才可以使用此选项。  
  
-   **Oracle 身份验证**：如果选择此选项，则必须在您连接到的源 Oracle 数据库中为用户键入 **“用户名”** 和 **“密码”** 。  
  
## <a name="see-also"></a>另请参阅  
 [How to Manage a CDC Instance](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [查看和生成补充日志记录脚本](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
