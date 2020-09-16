---
description: Template Explorer
title: Template Explorer
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.templates.explorer.f1
- sql13.wb.templates.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 5fcf7040cbf7b0dc3982164ca6574f2c048ed28c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468507"
---
# <a name="template-explorer"></a>模板资源管理器

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了多种模板。 模板即包含 SQL 脚本的样板文件，可用于在数据库中创建对象。 首次打开模板资源管理器时，会将模板的副本置于 C:\Users AppData\Roaming\Microsoft\SQL Server Management Studio\130\Templates 下的用户文件夹中。  
  
您可以在模板资源管理器中浏览可用模板，然后打开该模板以便将代码纳入代码编辑器窗口中。 也可以创建自定义模板。  
  
## <a name="benefits-of-templates"></a>模板的优点  
模板适用于解决方案、项目和各种类型的代码编辑器。 模板可用于创建对象，如数据库、表、视图、索引、存储过程、触发器、统计信息和函数。 此外，通过创建用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]的扩展属性、链接服务器、登录名、角色、用户和模板，有些模板还可以帮助您管理服务器。  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供的模板脚本包含了可以帮助您自定义代码的参数。 打开模板后，使用“替换模板参数”**** 对话框可以将值插入到脚本中。  
  
为频繁执行的任务创建自定义模板。 将自定义脚本组织到现有文件夹中，或创建一个新的文件夹结构。  
  
[!INCLUDE[ssDE](../../includes/ssde_md.md)] 查询编辑器还支持代码段，可通过在特定位置右键单击将代码段插入到脚本中的该位置。  
  
## <a name="related-tasks"></a>Related Tasks  
参考以下主题可以开始使用模板。  
  
|**说明**|**主题**|  
|-------------------|-------------|  
|介绍如何将模板中的代码合并到代码编辑器窗口。|[打开模板](../../ssms/template/open-a-template.md)|  
|介绍如何在代码编辑器中打开模板后替换模板参数值。|[替换模板参数](../../ssms/template/replace-template-parameters.md)|  
  
