---
title: “文件夹属性”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.isfolderprop.permissions.f1
- sql13.ssis.ssms.iscreatefolder.f1
- sql13.ssis.ssms.isfolderprop.general.f1
ms.assetid: d9a2bfae-fcc8-46be-b588-4a9db03f7e45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 334105bde7936543fd1dba3167fd61e1b440fd5e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922643"
---
# <a name="folder-properties-dialog-box"></a>“文件夹属性”对话框

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  文件夹包含 **SSISDB** 目录中的项目和环境。 每个文件夹都定义应用于该文件夹的内容的权限。 有关 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 权限的详细信息 ，请参阅 [catalog.grant_permission（SSISDB 数据库）](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)。  
  
## <a name="to-set-folder-description-and-permissions"></a>设置文件夹说明和权限  
  
1.  右键单击该文件夹并选择“属性”。   
  
2.  在 **“常规”** 页上，选择 **“常规”** 下的 **“说明”** ，然后输入可选说明。  
  
3.  在 **“权限”** 页上，单击 **“浏览...”** ，选择一个或多个数据库主体，然后单击 **“确定”** 。  
  
4.  在 **“登录名或角色”** 下选择一个名称，然后在 **“权限”** 下指定相应的权限。  
  
5.  单击 **“确定”** 以接受更改并关闭 **“文件夹属性”** 对话框。  
  
## <a name="see-also"></a>另请参阅  
 [Integration Services (SSIS) 服务器](../integration-services-ssis-packages.md)   
 [catalog.grant_permission（SSISDB 数据库）](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)  
  
  
