---
title: 在关系查询设计器中生成查询（报表生成器和 SSRS）
description: 了解如何在关系查询设计器中生成查询，以便可以指定要为报表数据集从外部数据源中检索哪些数据。
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 04/25/2019
ms.openlocfilehash: 5ead07a1cf2afa13189b76c0c6eb75a472699543
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85808477"
---
# <a name="build-a-query-in-the-relational-query-designer-report-builder-and-ssrs"></a>在关系查询设计器中生成查询（报表生成器和 SSRS）

查询设计器可帮助您指定为报表数据集要从外部数据源中检索的数据。 当您在向导中生成查询或创建数据集查询时，可以使用查询设计器。  
  
> [!NOTE]  
> [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 数据集基于数据源。 数据源的类型和创作环境决定在定义数据集查询时打开的查询设计器。 查询设计器功能根据基础数据源类型的不同而不同。 有关数据层的详细信息，请参阅[创建数据连接字符串 - 报表生成器和 SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)。

 可为以下任务使用查询设计器：  
  
-   浏览外部数据源中的多个架构的元数据  
  
-   指定要检索的数据集的字段  
  
-   指定两个对象（如表）之间的关系  
  
-   指定在将数据作为报表数据进行检索之前用于限制它的筛选器  
  
-   指示是否创建参数  
  
-   指定用于对外部数据源执行计算的聚合  
  
 打开查询设计器后，以生成嵌入数据集或共享数据集的相同方式生成查询。 以下过程使用嵌入数据集查询。  
  
 有关详细信息，请参阅[关系查询设计器用户界面（报表生成器）](../../reporting-services/report-data/relational-query-designer-user-interface-report-builder.md)。  
  
### <a name="to-build-a-query-for-an-embedded-dataset-in-report-design-view"></a>在报表设计视图中为嵌入数据集生成查询  
  
1.  打开查询设计器。 在“报表数据”窗格中，右键单击该数据集，然后单击“查询”。  
  
     将打开与数据源关联的查询设计器。  
  
2.  在“数据库视图”窗格中，展开显示数据库架构对象（如表、视图和存储过程）的层次结构视图的文件夹。 单击选择框为某个对象选择所有字段，或展开节点以选择单个字段。  
  
     在从“数据库视图”窗格中选择字段时， **“选择字段”** 窗格将显示您的选择。  
  
     如果从多个相关数据库表中选择字段，则使用“关系”窗格查看从数据库架构中检测到的表关系。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     数据集字段的列表将显示在“报表数据”窗格中。  
  
### <a name="to-specify-limits-for-a-query"></a>为查询指定限制  
  
1.  在关系查询设计器中，确认您已选择字段且这些字段显示在 **“所选字段”** 窗格中。  
  
2.  在“应用的筛选器”窗格工具栏中，单击 **“添加筛选器”** 。 此时将显示一个新的筛选器行。  
  
3.  在“字段名称”中，单击以显示字段的下拉列表，然后单击要作为筛选依据的字段名称****。 例如，若要按数量进行筛选，则单击包含项数的字段。  
  
4.  在“运算符”中，单击以显示运算符的下拉列表，然后选择要在筛选器中使用的比较运算符。  
  
5.  在 **“值”** 中，键入要作为筛选依据的值。 例如，若要针对大于 100 的数量进行筛选，则键入 100。  
  
6.  在此行中选择参数选项，以创建一个数据集参数，从而使用户能够指定筛选器值。 系统会自动创建与数据集参数匹配的报表参数。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 数据集字段的列表将显示在“报表数据”窗格中。  
  
### <a name="to-view-a-query-result-set"></a>查看查询结果集  
  
1.  在查询设计器工具栏中，单击“运行查询(!)”。  
  
    > [!NOTE]  
    >  查询设计器使用设计时凭据运行查询并检索结果集。 有关详细信息，请参阅[为报表数据源指定凭据和连接信息](specify-credential-and-connection-information-for-report-data-sources.md)  
  
 查询在数据源上运行并在“查询结果”窗格中返回示例数据。  
  
## <a name="see-also"></a>另请参阅  
 [报表数据集 (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [从外部数据源中添加数据 (SSRS)](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md)   
 [查询设计工具 (SSRS)](query-design-tools-ssrs.md)   
 [创建共享数据集或嵌入数据集（报表生成器和 SSRS）](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [报表设计视图（报表生成器）](../../reporting-services/report-builder/report-design-view-report-builder.md)   
 [共享数据集设计视图（报表生成器）](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [Reporting Services 查询设计器](https://msdn.microsoft.com/library/07efd3f1-804f-45f7-b62a-3e727a3d9835)  
  
  
