---
title: 实现呈现扩展插件 | Microsoft Docs
description: 了解如何通过实现呈现扩展插件，将 Reporting Services 报表数据和布局信息转换为设备特定的格式。
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d61af9bd987256a2ad293f7f9566fd1a2bcd041e
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529083"
---
# <a name="implementing-a-rendering-extension"></a>实现呈现扩展插件
  呈现扩展插件是将报表数据和布局信息转换为设备特定格式的报表服务器的组件或模块。 SQL Server Reporting Services 包括六个呈现扩展插件：HTML、Excel、Word、CSV 或 Text、XML、Image 和 PDF。 您可以创建其他呈现扩展插件以便以其他格式生成报表。  
  
> [!NOTE]  
>  若要确定哪些呈现扩展插件可用，您可以在 RSReportServer.config 文件中查看已安装的扩展插件列表。  
  
## <a name="in-this-section"></a>本节内容  
 [呈现扩展插件概述](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
 介绍如何为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 编写自定义呈现扩展插件。  
  
 [实现 IRenderingExtension 接口](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)  
 说明呈现扩展插件的属性。  
  
 [部署呈现扩展插件](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
 说明如何将呈现扩展插件部署到报表服务器。  
  
 [删除呈现扩展插件](../../../reporting-services/extensions/rendering-extension/removing-a-rendering-extension.md)  
 说明如何从报表服务器上删除呈现扩展插件。  
  
## <a name="see-also"></a>另请参阅  
 [Reporting Services 扩展插件](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services 扩展插件库](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
