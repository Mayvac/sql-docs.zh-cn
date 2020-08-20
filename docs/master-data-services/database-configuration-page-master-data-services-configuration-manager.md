---
description: “数据库配置”页（Master Data Services 配置管理器）
title: “数据库配置”页
ms.custom: seo-lt-2019
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql13.mds.configmanager.dbpg.f1
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3e7bee6e69dbfe3089e5f75a9500c767dd675fca
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461751"
---
# <a name="database-configuration-page-master-data-services-configuration-manager"></a>“数据库配置”页（Master Data Services 配置管理器）

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  使用 **“数据库配置”** 页可以编辑 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库的系统设置。 系统设置将影响与所选 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库相关联的所有 Web 应用程序和 Web 服务。 您必须首先选择或创建一个 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库，然后系统设置才能启用并且可用于配置。  
  
## <a name="current-database"></a>当前数据库  
 选择一个现有 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库或创建要编辑其系统设置的新数据库。 在创建后，将选择这个新数据库。  
  
|控件名称|描述|  
|------------------|-----------------|  
|**SQL Server 实例**|显示所选 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的名称。 在您连接到某一实例并选择或创建某一 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库之前，此项为空。|  
|**Master Data Services 数据库**|显示所选 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库的名称。 在您连接到某一实例并选择或创建某一 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库之前，此项为空。|  
|**Master Data Services 数据库版本**|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库架构的版本。|  
|**创建数据库**|打开 **“创建数据库”** 向导，从中您可以连接到某一 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例并为该实例创建 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库。|  
|**选择数据库**|打开 **“连接到数据库”** 对话框，在其中连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例并选择 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库。|  
|**升级数据库**|打开向导，您可以在其中升级指定的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库。 仅当指定的数据库需要升级时，此按钮才会启用。|  
|**修复数据库**|单击此按钮以确保 MDS 数据库安装正确。 这在将 MDS 数据库备份并还原到从未托管过 MDS 数据库的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的情况下非常有用。|  
  
## <a name="system-settings"></a>系统设置  
 为与所选 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库相关联的所有 Web 应用程序和 Web 服务编辑系统设置。  
  
 这些设置在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中提供，并存储在数据库的系统设置表 (mdm.tblSystemSetting) 中。 有关所有设置的列表，请参阅[系统设置 (Master Data Services)](../master-data-services/system-settings-master-data-services.md)。  
  
## <a name="see-also"></a>另请参阅  
[Master Data Services 的安装和配置](../master-data-services/master-data-services-installation-and-configuration.md) [数据库要求 &#40;Master Data Services&#41;](../master-data-services/install-windows/database-requirements-master-data-services.md)  
  
  
