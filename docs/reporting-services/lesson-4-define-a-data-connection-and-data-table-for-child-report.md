---
title: 第 4 课：定义用于子报表的数据连接和数据表 | Microsoft Docs
description: 了解如何使用 Reporting Services 创建用于子报表的数据连接和数据表。
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 80df8e86ed3d23c5ab097cdab3f26d83838c4544
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245116"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a>第 4 课：定义用于子报表的数据连接和数据表
设计父报表后，接下来要创建用于子报表的数据连接和数据表。 在本教程中，数据连接指向 AdventureWorks2014 数据库。  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a>通过添加 DataSet 定义数据连接和 DataTable（用于子报表）  
  
1.  在“网站”菜单上，选择“添加新项” 。  
  
2.  在“添加新项”对话框中，选择“数据集”，然后选择“添加”  。 出现提示后，应选择“是”，将该项添加到 App_Code 文件夹 。  
  
    此操作将一个新的 XSD 文件 **DataSet2.xsd** 添加到项目，并打开数据集设计器。  
  
3.  从“工具箱”窗口中，将 **TableAdapter** 控件拖到设计图面上。 随后将启动 **TableAdapter** 配置向导。  
  
4.  在“选择数据连接”页上，可以选择在第 2 课中创建的连接。 如果执行了此操作，请选择“下一步”并转到步骤 8。 否则，请选择“新建连接”。  
  
5.  在“添加连接”对话框中，执行以下步骤：  
  
    1.  在“服务器名称”框中，输入 AdventureWorks2014 数据库所在的服务器 。  
  
        默认的 SQL Server Express 实例为 **(local)\sqlexpress**。  
  
    2.  在“登录到服务器”部分中，选择使你可访问数据的选项。 “使用 Windows 身份验证”为默认选项。  
  
    3.  在“选择或输入数据库名称”下拉列表中，选择“AdventureWorks2014” 。  
  
    4.  选择“确定”，然后选择“下一步”。  
  
6.  如果在步骤 5 (b) 中选择了“使用 SQL Server 身份验证”，则选择一个选项，决定是在字符串中加入敏感数据还是在应用程序代码中设置该信息****。  
  
7.  在“将连接字符串保存到应用程序配置文件中”页上，键入连接字符串的名称，或接受默认的“AdventureWorks2014ConnectionString”********。 选择“**下一页**”。  
  
8.  在“选择命令类型”页上，选择“使用 SQL 语句”，然后选择“下一步”  。  
  
9. 在“输入 SQL 语句”页上，输入以下 Transact-SQL 查询以从 AdventureWorks2014 数据库检索数据，然后选择“下一步”  。  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
    还可通过选择“查询生成器”创建查询，然后通过选择“执行查询”按钮验证查询 。 如果查询返回的数据不符合预期，则可能使用的 AdventureWorks 版本较低。 有关如何获取 AdventureWorks2014 示例数据库的详细信息，请参阅 [AdventureWorks sample databases](https://github.com/Microsoft/sql-server-samples/releases)（AdventureWorks 示例数据库）。  
  
10. 在“选择要生成的方法”页上，取消选中“创建方法以将更新直接发送到数据库(GenerateDBDirectMethods)”，然后选择“完成”  。  
  
    > [!WARNING]  
    > 务必取消选中“创建方法以将更新直接发送到数据库(GenerateDBDirectMethods)”  
  
    配置 ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable.aspx) 作为报表的数据源现已完毕。 在 Visual Studio 中的“数据集设计器”页上，应看到所添加的 **DataTable** ，其中列出在查询中指定的列。 DataSet2 由根据查询从 PurhcaseOrderDetail 表获得的数据组成。  
  
11. 保存文件。  
  
12. 要预览数据，请在“数据”菜单上选择“预览数据”，然后选择“预览”  。  
  
## <a name="next-task"></a>下一个任务  
您已成功创建了用于子报表的数据连接和数据表。 接下来，将使用报表向导设计子报表。 请参阅[第 5 课：使用报表向导设计子报表](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)。  
  

