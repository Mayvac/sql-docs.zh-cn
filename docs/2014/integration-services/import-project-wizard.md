---
title: 导入项目向导 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b9f20115010f2ad51159f29a4b64da195938969
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436644"
---
# <a name="import-project-wizard"></a>导入项目向导
  使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 导入项目向导可以基于现有的项目创建一个新的 Integration Services 项目。 导入已部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目录的项目，或从项目部署文件（扩展名为 .ispac）导入项目。  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a>基于 .ispac 文件或目录中的项目创建项目  
  
1.  单击 "**文件**"，指向 "**新建**"，然后单击 "项目"。  
  
2.  展开 **“商业智能”**，然后单击 **Integration Services**。  
  
3.  在中间的窗格中选择 **“Integration Services 导入向导”** ，为解决方案键入 **“名称”** ，为项目指定 **“文件夹”** ，然后单击 **“确定”**。  
  
     此时应看到 **“Integration Services 导入项目向导”**。 该向导将基于现有的项目创建一个新的 Integration Services 项目。  
  
4.  在 **“简介”** 页上单击 **“下一步”** 以便看到 **“选择源”** 页。  
  
5.  指定要从 .ispac 文件还是从目录导入项目。  
  
    -   如果您选择 **“项目部署文件”** 选项，则指定指向 .ispac 文件的路径。  
  
    -   如果您选择 **“Integration Services 目录”** 选项，则指定目录在其上存在的数据库服务器实例的名称，以及指向该目录中的项目的路径。  
  
6.  在 **“选择源”** 页上单击 **“下一步”** 以便看到 **“检查”** 页。 查看在该页上显示的与向导将要执行的导入操作有关的信息。  
  
7.  单击 **“导入”** 以便基于您选择的项目创建一个新的 Integration Services 项目。  
  
8.  **“结果”** 页应该显示向导执行的导入操作的结果。 单击 **“保存报表”** 可以将报表保存到某一 XML 文件。  
  
9. 单击“**关闭**”以关闭向导。  
  
  
