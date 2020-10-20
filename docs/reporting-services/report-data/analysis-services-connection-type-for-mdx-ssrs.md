---
title: 针对 MDX 的 Analysis Services 连接类型 | Microsoft Docs
description: 了解针对 MDX 的 Analysis Services 连接类型 (SSRS) 的详细信息，以能够便检索用作报表数据的元数据。
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: bd2e7148-3124-4e07-9734-22333127c3be
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3f8b6fb8aa45357318c398773708ecd2c66dba30
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91935073"
---
# <a name="analysis-services-connection-type-for-mdx-ssrs"></a>针对 MDX 的 Analysis Services 连接类型 (SSRS)
  若要在报表中包括来自 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维数据集的数据，你必须具有一个基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 类型的报表数据源的数据集。 此内置数据源类型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据扩展插件。 可以从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维数据集中检索有关维度、层次结构、级别、关键绩效指标 (KPI)、度量值和属性的元数据，以用作报表数据。  
  
 此数据处理扩展插件支持多值参数、服务器聚合以及与连接字符串分开管理的凭据。  
  
 使用本主题中的信息来生成一个数据源。 有关分步说明，请参阅 [添加和验证数据连接（报表生成器和 SSRS）](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)。  
  
##  <a name="connection-string"></a><a name="Connection"></a> 连接字符串  
 当连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维数据集时，您将会连接到服务器上一个 Analysis Services 实例中的数据库对象。 该数据库可能具有多个多维数据集。 可在生成查询时在查询设计器中指定多维数据集。 下面的示例演示连接字符串：  
  
```  
data source=<server name>;initial catalog=<database name>  
```  
  
 有关更多连接字符串的示例，请参阅[创建数据连接字符串 - 报表生成器和 SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)。  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> 凭据  
 执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。  
  
 报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。  
  
 在报表创作客户端，可以使用下列选项指定凭据：  
  
-   当前 Windows 用户（也称为集成安全性）。  
  
-   使用存储的用户名和密码。  
  
-   提示用户输入凭据。 此选项仅支持 Windows 集成安全性。  
  
-   不需要提供任何凭据。 若要使用此选项，您必须具有为报表服务器配置的无人参与的执行帐户。 有关详细信息，请参阅[配置无人参与的执行帐户（报表服务器配置管理器）](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)
  
 有关详细信息，请参阅[创建数据连接字符串 - 报表生成器和 SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) 或[为报表数据源指定凭据和连接信息](specify-credential-and-connection-information-for-report-data-sources.md)。  
  
  
##  <a name="queries"></a><a name="Query"></a> 查询  
 与 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据源建立数据连接之后，您可以创建一个数据集，并定义一个指定要从多维数据集中检索哪些数据的多维表达式 (MDX) 查询。 使用 MDX 图形查询设计器在数据源的基础数据结构中进行浏览和选择。  
  
 可以通过下列方式指定查询：  
  
-   以交互方式生成查询。 Analysis Services MDX 查询设计器支持以下视图：  
  
    -   **设计视图** 将维度、成员、成员属性、度量值和 KPI 从元数据浏览器拖至 **“数据”** 窗格，以生成 MDX 查询。 将计算成员从“计算成员”窗格拖至“数据”窗格，以定义附加数据集字段。  
  
    -   **查询视图** 将维度、成员、成员属性、度量值和 KPI 从元数据浏览器拖至“查询”窗格，以生成 MDX 查询。 在“查询”窗格中可以直接编辑 MDX 文本。 将计算成员从“计算成员”窗格拖至“查询”窗格，以定义附加数据集字段。  
  
     有关详细信息，请参阅 [Analysis Services MDX 查询设计器用户界面（报表生成器）](../../reporting-services/report-data/analysis-services-mdx-query-designer-user-interface.md)。  
  
-   从报表导入现有 MDX 查询。 使用 **“导入”** 查询按钮浏览到 .rdl 文件并导入查询。 对于包含基于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据源的嵌入数据集的报表，可以从中导入查询。 不支持直接从 .mdx 文件导入 MDX 查询。  
  
 在设计时，运行查询以查看结果集。 会自动将查询结果作为平展行集进行检索。 查询的结果集中的列填充数据集的字段集合。 生成查询后，在“报表数据”窗格中查看从元数据生成的数据集字段集合。 报告运行时，将从外部数据源返回实际数据。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据处理扩展插件支持扩展数据集字段属性。 这些值可从外部数据源获得，但在“报表数据”窗格中不显示。 可以通过内置 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Fields **集合，在报表中使用** 数据处理扩展插件支持的扩展字段属性。 对于在数据源中具有值的属性，可以访问预定义的属性值，如 **FormattedValue**、 **Color**或 **UniqueName**。 有关详细信息，请参阅 msdn.microsoft.com 上 [Analysis Services 数据库的扩展字段属性 (SSRS)](../../reporting-services/report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md)。  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> Parameters  
 若要包括查询参数，请在查询设计器的筛选区域创建一个筛选器，并将该筛选器标记为参数。 系统将为每个筛选器自动创建一个数据集以提供可用值。 默认情况下，这些数据集不显示在“报表数据”窗格中。 有关详细信息，请参阅[在 Analysis Services 的 MDX 查询设计器中定义参数（报表生成器和 SSRS）](../../reporting-services/report-data/define-parameters-in-the-mdx-query-designer-for-analysis-services.md)和[为多维数据的参数值显示隐藏的数据集（报表生成器和 SSRS）](../../reporting-services/report-data/show-hidden-datasets-for-parameter-values-multidimensional-data.md)。  
  
 默认情况下，每个报表参数的数据类型均为 **Text**。 创建报表参数后，您可能需要更改默认值。 有关详细信息，请参阅 [报表参数（报表生成器和报表设计器）](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)的详细信息。  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> 注释  
 Analysis Services 数据扩展插件基于 XMLA (XML for Analysis) 协议。 通过 XMLA 协议将来自多维数据集的结果集作为平展行集进行检索。 不支持不规则层次结构。 有关详细信息，请参阅 [不规则层次结构](/analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies)。  
  
 还可以从 OLE DB 数据源类型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维数据集中检索数据。 有关详细信息，请参阅 [OLE DB 连接类型 (SSRS)](../../reporting-services/report-data/ole-db-connection-type-ssrs.md)。  
  
 有关版本支持的详细信息，请参阅 [Reporting Services 支持的数据源 &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)。  
  
  
##  <a name="related-sections"></a><a name="Related"></a> 相关章节  
 文档中的这些章节提供有关报表数据的深入概念性信息，以及有关如何定义、自定义和使用与数据相关的报表部件的步骤信息。  
  
 [报表数据集 (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 提供访问报表数据的概述。  
  
 [创建数据连接字符串 - 报表生成器和 SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
 提供有关数据连接和数据源的信息。  
  
 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 提供有关嵌入数据集和共享数据集的信息。  
  
 [数据集字段集合（报表生成器和 SSRS）](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 提供有关查询生成的数据集字段集合的信息。  
  
 [Analysis Services 数据库的扩展字段属性 (SSRS)](../../reporting-services/report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md)  
 提供有关可通过 XMLA 数据访问接口获得的额外字段的信息。  
  
 [Reporting Services 支持的数据源 &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)。  
 提供有关每个数据扩展插件的平台和版本支持的详细信息。  
  
  
## <a name="see-also"></a>另请参阅  
 [报表参数（报表生成器和报表设计器）](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [表达式（报表生成器和 SSRS）](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
