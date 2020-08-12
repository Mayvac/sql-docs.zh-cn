---
title: 创建和修改嵌入的数据源 | Microsoft Docs
description: 了解如何创建和修改在报表定义中定义且仅供该报表使用的嵌入的数据源。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 1c38c2e8-7a29-4f79-a4a3-85ed2b13723b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0e5f9aed11beacf056916e44e6f2df391444eae0
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85808447"
---
# <a name="create-and-modify-embedded-data-sources"></a>创建和修改嵌入的数据源
  嵌入数据源在报表定义中定义并只由该报表使用。  
  
## <a name="to-create-an-embedded-data-source-in-report-designer"></a>在报表设计器中创建嵌入的数据源  
  
1.  在“报表数据”窗格的工具栏中，单击 **“新建”** ，然后单击 **“数据源”** 。 此时将打开 **“数据源属性”** 对话框。  
  
    > [!NOTE]  
    >  如果“报表数据”窗格不可见，请单击“视图”菜单上的“报表数据”。  
  
2.  在 **“名称”** 文本框中，键入数据源的名称，或接受默认值。 此数据源名称在报表内部使用。 为便于识别，建议数据源名称包含在连接字符串中指定的数据库的名称。  
  
3.  确认是否已选中“嵌入连接”  ，然后执行以下操作。  
  
    1.  从“类型”下拉列表中，选择一个数据源类型，例如“Microsoft SQL Server”或“OLE DB”  。  
  
    2.  采用以下备选方案之一指定连接字符串：  
  
        -   直接在 **“连接字符串”** 文本框中键入连接字符串。 有关连接字符串的示例列表，请参阅[创建数据连接字符串 - 报表生成器和 SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)。  
  
        -   单击表达式 (**fx** ) 按钮创建计算结果为连接字符串的表达式。 在 **“表达式”** 对话框的“表达式”窗格中，键入该表达式。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   单击 **“编辑”** 打开在步骤 2 中选择的数据源类型的 **“连接属性”** 对话框。  
  
             根据需要，在 **“连接属性”** 对话框中为该数据源类型填写字段。 连接属性包括数据源的类型、名称以及要使用的凭据。 在此对话框中指定值之后，单击 **“测试连接”** 以确保该数据源可用并且指定的凭据是正确的。 有关特定数据源类型的详细信息，请参阅[从外部数据源中添加数据 (SSRS)](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md) 中的主题。  
  
    3.  单击 **“凭据”** 。  
  
         指定用于此数据源的凭据。 数据源所有者将选择支持的凭据类型。  
  
4.  嵌入的数据源会显示在“报表数据”窗格中。  
  
## <a name="to-create-an-embedded-data-source-in-report-builder"></a>在报表生成器中创建嵌入的数据源  
  
1.  在“报表数据”窗格的工具栏上，单击 **“新建”** ，然后单击 **“数据源”** 。 此时将打开 **“数据源属性”** 对话框。  
  
2.  在 **“名称”** 文本框中，键入数据源的名称，或接受默认值。  
  
3.  确认选中 **“使用嵌在我的报表中的连接”** 。  
  
    1.  从“选择连接类型”下拉列表中，选择一个数据源类型，例如“Microsoft SQL Server”或“OLE DB”  。  
  
    2.  采用以下备选方案之一指定连接字符串：  
  
        -   直接在 **“连接字符串”** 文本框中键入连接字符串。 有关连接字符串的示例列表，请参阅[创建数据连接字符串 - 报表生成器和 SSRS](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)。  
  
        -   单击表达式 (**fx** ) 按钮创建计算结果为连接字符串的表达式。 在 **“表达式”** 对话框的“表达式”窗格中，键入该表达式。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
        -   单击 **“生成”** 打开在步骤 2 中选择的数据源类型的 **“连接属性”** 对话框。  
  
             根据需要，在 **“连接属性”** 对话框中为该数据源类型填写字段。 连接属性包括数据源的类型、名称以及要使用的凭据。 在此对话框中指定值之后，单击 **“测试连接”** 以确保该数据源可用并且指定的凭据是正确的。  
  
4.  单击 **“凭据”** 。  
  
     指定用于此数据源的凭据。 数据源所有者将选择支持的凭据类型。 有关详细信息，请参阅[为报表数据源指定凭据和连接信息](specify-credential-and-connection-information-for-report-data-sources.md)  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     数据源将显示在“报表数据”窗格中。  
  
## <a name="see-also"></a>另请参阅  
 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [为报表数据源指定凭据和连接信息](specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
