---
title: 查看 Integration Services 服务器上的包列表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: f5498dfcd7ae18fc504784593212f54249b7f221
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84924178"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>查看 Integration Services 服务器上的包列表
  可以使用以下两种方式之一来查看存储在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器上的包列表。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] access  
 若要查看在服务器上存储的包的列表，请查询视图 [catalog.packages（SSISDB 数据库）](/sql/integration-services/system-views/catalog-packages-ssisdb-database)。  
  
 在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中  
 若要使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中的对象资源管理器查看服务器上存储的包，请遵循以下过程。  
  
### <a name="to-view-packages-using-ssmanstudiofull"></a>使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
1.  在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。 也就是说，连接到承载 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 数据库的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 实例。  
  
2.  在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。  
  
3.  展开 **“Integration Services 目录”** 节点以显示 **SSISDB** 节点。  
  
4.  展开 **SSISDB** 节点以显示一个或多个文件夹的列表。 每个文件夹包含 **“项目”** 文件夹中的一个或多个项目，而每个项目包含 **“包”** 文件夹中的一个或多个包。  
  
  
