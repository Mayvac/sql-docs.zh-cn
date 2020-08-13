---
title: “数据集属性”对话框 ->“查询”（报表生成器）| Microsoft Docs
description: 了解如何使用报表生成器中“数据集属性”对话框上的“查询”，从报表服务器选择共享数据集或创建嵌入数据集。
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: reference
f1_keywords:
- "10024"
- sql13.rtp.rptdesigner.datasetproperties.query.f1
- "10160"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 14380ba698101c76a84d0b9eef27a4ea31953f2d
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458929"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>“数据集属性”对话框 -&gt;“查询”（报表生成器）
 
选择 **“数据集属性”** 对话框中的 **“查询”** 可以从报表服务器选择共享数据集或创建嵌入数据集。 对于嵌入数据集，必须选择一个数据源并生成查询。  
  
## <a name="options"></a>选项  
 **名称**  
 为数据集键入名称。 该名称不能与报表中的任何数据区域或组的名称相同。  
  
 **使用共享数据集**  
 选择此选项可以使用报表服务器中的预定义数据集。  
  
 **“浏览”**  
 找到报表服务器或 SharePoint 站点上的文件夹，然后选择一个共享数据集 (.rsd)。  
  
 **在我的报表中使用嵌入数据集**  
 选择此选项可以创建仅供此报表使用的数据集。  
  
 **数据源**  
 选择数据集要基于的数据源。 若要创建新的数据源，单击 **“新建”** 。  
  
 **查询类型**  
 选择要用于数据集的命令或查询的类型。 选择 **Text** 可运行从数据库中检索数据的查询。 选择 **Table** 可使用 **的** TableDirect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能选择表内的所有字段。 选择 **Stored Procedure** 可按名称运行存储过程。 默认情况下将选择**Text** ，该类型适用于大多数查询。 若要编辑选中的数据源查询，单击 **“查询设计器”** 。  
  
> [!NOTE]  
>  不是任何数据源都支持所有查询类型。 例如，仅数据源类型 **OLE DB** 和 **ODBC** 支持 **Table**。  
  
 **查询**  
 选中 **Text** 命令类型选项后将显示此选项。 需键入一个查询或通过单击“导入”来导入一个预先存在的查询。 单击“表达式” (*fx*) 按钮可编辑表达式。  
  
> [!NOTE]  
>  如果已使用查询设计器生成了一个查询，则此对话框中将显示该查询的文本。  
  
**表名称**  
选中 **“表”** 后会显示此选项。 需输入要用作数据集的表的名称。   
  
**选择或输入存储过程名称**  
选中“存储过程”命令类型选项后会显示此选项。 需键入或选择要使用的存储过程的名称。 单击“表达式” (*fx*) 按钮可编辑表达式。   
  
 **超时（以秒为单位）**  
 键入查询在多长时间后超时（秒）。默认为 30 秒。 **“超时值”** 的值必须为空或大于零。 如果该值为空，则查询将不会超时。  
  
 **刷新字段**  
 运行查询命令来更新“数据集属性”对话框 ->“字段”页中的字段列表。  
  
## <a name="see-also"></a>另请参阅  
[报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。  
[报表数据集 (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
[查询设计工具 (SSRS)](query-design-tools-ssrs.md)  
  
  
