---
title: 获取数据连接的备选方法（报表生成器）| Microsoft Docs
description: 了解有关连接到外部数据源（如 SQL Server 数据库）的替代方法的详细信息。
ms.date: 06/15/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: aebc5f3d-97d5-4d54-b525-753fed073a9a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: dfa10030537ebd325dae78c61985e75d6d2a49ff
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246349"
---
# <a name="alternative-ways-to-get-a-data-connection-report-builder"></a>获取数据连接的备选方法（报表生成器）
数据连接包含要连接到外部数据源（如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库）的信息。 通常会从数据源所有者处获取连接信息以及要使用的凭据类型。  
  
若要指定数据连接，可以从报表服务器使用共享数据源或创建仅在某个特定报表中使用的嵌入数据源。  
  
在大多数教程中，您使用嵌入数据源，但如果您有权访问共享数据源，则可以改为使用共享数据源。  
  
## <a name="getting-a-data-connection-from-a-shared-data-source"></a>从共享数据源获取数据连接  
如果报表服务器具有你有权使用的可用共享数据源，则你可以使用这些数据源来代替嵌入数据源。 以下过程说明如何找到共享数据源并提供使用这些数据源所需的任何凭据。  
  
若要使用共享数据源，浏览到报表服务器并选择一个共享数据源。 通常会从报表服务器管理员处获取报表服务器 URL。  
  
### <a name="to-specify-a-data-connection-from-a-list-of-shared-data-sources"></a>从共享数据源列表指定数据连接  
  
1.  在“新建表或矩阵”或“新建图表向导”中，在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”************。 将打开“选择数据源的连接”页面。  
  
2.  从数据源列表中选择有权访问的数据源。  
  
3.  若要验证是否能连接到数据源，请单击“测试连接”。 将显示消息“已成功地创建连接”。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  单击“下一步”。  
  
    如果需要，请输入您的凭据。 要本地保存凭据，请选择“保存连接的密码”。 如果不选择此选项，则每当你运行该报表时系统都会提示你输入凭据  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-specify-a-data-connection-by-browsing-to-a-shared-data-source-on-a-report-server"></a>通过浏览到报表服务器上的共享数据源来指定数据连接  
  
1.  在“新建表或矩阵”或“新建图表向导”中，在“选择数据集”页上，选择“创建数据集”，然后单击“下一步”************。 将打开“选择数据源的连接”页面。  
  
2.  单击“浏览”。 “选择数据源”对话框随即打开。  
  
3.  从“查找范围”下拉列表中选择“最近使用的站点和服务器” 。 在数据源窗格中，单击服务器的 URL，然后单击“打开”。  
  
    将显示数据源或模型的列表。  
  
4.  或者，在“名称”中，键入报表服务器的 URL。 单击 **“打开”** 。  
  
    报表生成器将连接到报表服务器，并加载根文件夹中可用的数据源。  
  
5.  导航到包含一个数据源（你有足够的权限，可以连接到该数据源）的文件夹，选择该数据源，然后单击“打开”****。  
  
    返回至“选择数据源的连接”页。  
  
6.  若要验证是否能连接到数据源，请单击“测试连接”。  
  
    将显示消息“已成功地创建连接”。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  单击“下一步”。  
  
8.  如果系统提示您输入用户名和密码，请输入您的凭据。 要本地保存凭据，请选择“保存连接的密码”。  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a>另请参阅  
[报表数据集 (SSRS)](../reporting-services/report-data/report-datasets-ssrs.md)  
[报表生成器教程](../reporting-services/report-builder-tutorials.md) 
  

