---
title: 域管理：域列表
ms.date: 11/08/2011
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dm.domainlist.f1
ms.assetid: 8df305f0-97ea-4226-811b-979ed862e1f0
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 74486901a641b42f5f3c2c324b97307ef17c0182
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813832"
---
# <a name="domain-management-domain-list"></a>域管理：域列表

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  本主题介绍 **(DQS) 中** “域管理” [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 页的域列表中的控件。 使用此窗格可以选择要对其执行管理操作的域。 将对 **“域管理”** 页中的所有选项卡式页使用此同一窗格。  
  
## <a name="options"></a>选项  
  
### <a name="domains-list"></a>域列表  
 **域**  
 此列表显示了知识库中的所有域。 将针对在该列表中选择的域执行您在右侧窗格的选项卡式页中执行的操作。 有关详细信息，请参阅  
  
 **创建复合域**  
 在知识库中创建一个新的复合域。 此命令将显示 **“创建复合域”** 对话框。 通过右键单击某个域或单击域列表上方的图标可以使用此命令。 有关详细信息，请参阅 [创建复合域](../data-quality-services/create-a-composite-domain.md)。  
  
 **创建域**  
 在知识库中创建一个新域。 此命令将显示 **“创建域”** 对话框。 通过右键单击某个域或单击域列表上方的图标可以使用此命令。 有关详细信息，请参阅 [创建域](../data-quality-services/create-a-domain.md)。  
  
 **创建所选域的副本**  
 创建所选域的精确副本，并将其添加到知识库。 其名称将为从中创建该副本的域的名称，并在此名称之后追加“ - Copy”。 通过右键单击某个域，然后单击 **“创建副本”**，或者单击域列表上方的图标，可以使用此命令。 此命令不适用于复合域。  
  
 **从数据文件导入域**  
 从 .dqs 文件导入域。 此命令将显示 **“从数据文件导入”** 对话框，该对话框用于浏览文件系统并为单一域或复合域选择 .dqs 文件。 通过单击域列表上方的图标可以使用此命令。 有关详细信息，请参阅 [从 .dqs 文件导入域](../data-quality-services/import-a-domain-from-a-dqs-file.md)。  
  
 **删除域**  
 从知识库中删除所选域。 此命令将显示 **SQL Server Data Quality Services** 对话框。 如果您单击 **“是”**，该域及其所有数据将被永久删除。 通过右键单击某个域或单击域列表上方的图标可以使用此命令。  
  
 **创建链接域**  
 创建一个链接到所选域的域。 此命令将显示 **“创建域”** 对话框。 通过右键单击某个域，然后单击 **“创建链接域”** （该域链接到所选域），可以使用此命令。 所链接到的域显示在“创建域”对话框中。 该命令不适用于复合域。 没有可用于取消两个域链接的命令；若要执行此操作，请删除链接域。 无法对链接域创建链接域。 有关详细信息，请参阅 [创建链接域](../data-quality-services/create-a-linked-domain.md)。  
  
 链接域与其所链接到的域具有相同的值。 只有域的名称和属性不同。 如果您更改链接到的域中的域规则、域值、引用数据链接或基于字词的关系，则链接域中的域规则、域值、引用数据链接或基于字词的关系也将改变。 此外，如果您更改链接域中的值，所链接到的域中也会发生变化。  
  
 **导出知识库**  
 将整个知识库导出为 .dqs 文件。 此命令将显示 **“导出到数据文件”** 对话框。 通过单击页顶部的 **“导出知识库数据”** 图标，或在域列表窗格中域的上下文菜单的 **“导出”** 中，可以使用此命令。 有关详细信息，请参阅 [将知识库导出到 .dqs 文件](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)。  
  
 **导出域**  
 将域导出为 .dqs 文件。 此命令将显示 **“导出到数据文件”** 对话框。 页面顶部菜单栏的 **“导出”** 菜单中提供了此命令，也可通过右键单击域列表窗格来使用此命令。 有关详细信息，请参阅 [将域导出到 .dqs 文件](../data-quality-services/export-a-domain-to-a-dqs-file.md)。  
  
  
