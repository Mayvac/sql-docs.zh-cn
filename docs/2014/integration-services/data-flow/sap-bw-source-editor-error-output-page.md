---
title: SAP BW 源编辑器（“错误输出”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e0197a21f563cd96745b3ee2bed148b18e0cb0f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437674"
---
# <a name="sap-bw-source-editor-error-output-page"></a>SAP BW 源编辑器（“错误输出”页）
  可以使用 **“SAP BW 源编辑器”** 的 **“错误输出”** 页选择错误处理选项，以及设置错误输出列的属性。  
  
 若要了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 源组件的详细信息，请参阅 [SAP BW 源](sap-bw-source.md)。  
  
> [!IMPORTANT]  
>  针对 Microsoft Connector 1.1 for SAP BW 的文档假定您熟悉 SAP Netweaver BW 环境。 有关 SAP NetWeaver BW 的详细信息，或者有关如何配置 SAP Netweaver BW 对象和过程的信息，请参阅您的 SAP 文档。  
  
> [!IMPORTANT]  
>  从 SAP Netweaver BW 提取数据要求额外的 SAP 许可。 请向 SAP 核实以便确认这些要求。  
  
 **打开“错误输出”页**  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含 SAP BW 源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。  
  
2.  在“数据流”  选项卡上，双击“SAP BW 源”。  
  
3.  在 **“SAP BW 源编辑器”** 中单击 **“错误输出”** ，以打开编辑器的 **“错误输出”** 页。  
  
## <a name="options"></a>选项  
  
> [!NOTE]  
>  如果您不知道配置源所需的所有值，可能需要询问您的 SAP 管理员。  
  
 **输入或输出**  
 查看数据源的名称。  
  
 **列**  
 查看在“SAP BW 源编辑器”对话框的“列”页上选择的外部（源）列。 有关此对话框的详细信息，请参阅 [SAP BW 源编辑器（“列”页）](sap-bw-source-editor-columns-page.md)。  
  
 **错误**  
 指定发生错误时 SAP BW 源组件应执行的操作：忽略错误、重定向行或使组件失败。  
  
 **截断**  
 指定发生截断时 SAP BW 源组件应执行的操作：忽略错误、重定向行或使组件失败。  
  
 **说明**  
 查看对错误的说明。  
  
 **将此值设置到选定的单元格**  
 指定发生错误或截断时 SAP BW 源组件应对所有选定单元格执行的操作：忽略错误、重定向行或使组件失败。  
  
 **应用**  
 将错误处理选项应用到选定的单元格。  
  
## <a name="see-also"></a>另请参阅  
 [SAP BW 源编辑器（“连接管理器”页）](sap-bw-source-editor-connection-manager-page.md)   
 [SAP BW 源编辑器（“列”页）](sap-bw-source-editor-columns-page.md)   
 [SAP BW 源编辑器（“高级”页）](sap-bw-source-editor-advanced-page.md)   
 [Microsoft Connector 1.1 for SAP BW F1 帮助](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
