---
title: 维度处理目标编辑器（"连接管理器" 页） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: janinezhang
ms.author: janinez
ms.openlocfilehash: deb6c1a4fb5095e387bed9ca2b88b66e62c0bd9a
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966973"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a>维度处理目标编辑器（“连接管理器”页）
  可以使用“维度处理目标编辑器”对话框的“连接管理器”页面指定与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例之间的连接********。  
  
 若要了解有关维度处理目标的详细信息，请参阅 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)。  
  
## <a name="options"></a>选项  
 **连接管理器**  
 从列表中选择现有连接管理器，或单击“新建”**** 创建新的连接管理器。  
  
 **新建**  
 通过使用“添加 Analysis Services 连接管理器”**** 对话框创建一个新连接。  
  
 **可用维度列表**  
 选择要处理的维度。  
  
 **处理方法**  
 选择要应用于列表中选定维度的处理方法。 此选项的默认值为 **“完全”**。  
  
|值|说明|  
|-----------|-----------------|  
|**添加(增量式)**|对维度执行增量处理。|  
|**完整**|对维度执行完全处理。|  
|**Update**|对维度执行更新处理。|  
  
## <a name="see-also"></a>另请参阅  
 [Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [维度处理目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)   
 [维度处理目标编辑器（“高级”页）](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  
