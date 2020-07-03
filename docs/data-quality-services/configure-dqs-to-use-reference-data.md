---
title: 将 DQS 配置为使用引用数据
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.administration.rdsconfiguration.f1
- sql13.dqs.administration.configuration.createDirectRDS.f1
- sql13.dqs.admin.config.rds.f1
ms.assetid: fae745e7-57a7-4cbc-8979-56ea8e392e4e
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 0e7a33369516adf7a7fdae9f0047ff7f434e9c16
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894201"
---
# <a name="configure-dqs-to-use-reference-data"></a>将 DQS 配置为使用引用数据

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  本主题介绍如何将 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 配置为使用引用数据来清理您的数据。 你可以使用来自 Azure Marketplace 的引用数据，也可以使用来自直接联机第三方引用数据提供程序的引用数据。  

> [!IMPORTANT]
> 本文提及以前可从 Azure DataMarket 获取的第三方参考数据服务。 DataMarket 和数据服务（包括 Melissa 地址数据）在 2016 年 12 月 31 日之后已不再使用。 因此，无法继续使用 DataMarket 中的指定服务运行本文中的示例。 但仍可使用第三方参考数据提供商提供的在线参考数据服务。

## <a name="before-you-begin"></a>开始之前  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a>先决条件  
 若要使用来自市场的引用数据，您必须具有有效的市场帐户密钥。 有关创建 Marketplace 帐户密钥的详细信息，请参阅[创建帐户](https://go.microsoft.com/fwlink/?LinkId=212936)（ https://go.microsoft.com/fwlink/?LinkId=212936) 。 还可以通过单击 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中 **“管理”** 下的 **“配置”** ，然后单击 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] “引用数据” **选项卡下的** “创建 DataMarket 帐户 ID” **，在** 中创建市场帐户密钥。  
  
###  <a name="security"></a><a name="Security"></a> Security  
  
####  <a name="permissions"></a><a name="Permissions"></a> 权限  
 您必须具有 DQS_MAIN 数据库的 dqs_administrator 角色，才能在 DQS 中配置引用数据服务设置。  
  
##  <a name="configure-dqs-to-use-reference-data-from-marketplace"></a><a name="Marketplace"></a> 将 DQS 配置为使用来自市场的引用数据  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][运行 Data Quality Client 应用程序](../data-quality-services/run-the-data-quality-client-application.md)。  
  
2.  在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中的 **“管理”** 下，单击 **“配置”**。  
  
3.  如果您的组织使用代理服务器连接到 Internet，则在 **“引用数据”** 选项卡中的 **“网络设置”** 区域下，在 **“代理服务器”** 和 **“端口”** 框中键入适当的值。  
  
4.  在 **“DataMarket 帐户 ID”** 框中指定市场帐户密钥，然后单击 **“验证 DataMarket 帐户 ID”** 图标以验证该帐户密钥。 系统将显示一条消息，以显示指定的市场帐户密钥是否有效。  
  
 您现在可以在 DQS 中使用为指定的市场帐户密钥订阅的来自市场的引用数据服务。  
  
##  <a name="configure-dqs-to-use-reference-data-from-direct-online-third-party-reference-data-providers"></a><a name="ThirdParty"></a>将 DQS 配置为使用来自直接联机第三方引用数据提供程序的引用数据  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][运行 Data Quality Client 应用程序](../data-quality-services/run-the-data-quality-client-application.md)。  
  
2.  在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中的 **“管理”** 下，单击 **“配置”**。  
  
3.  如果您的组织使用代理服务器连接到 Internet，则在 **“引用数据”** 选项卡中的 **“网络设置”** 区域下，在 **“代理服务器”** 和 **“端口”** 框中键入适当的值。  
  
4.  在 **“直接联机第三方引用数据服务设置”** 区域中，单击 **“添加新的引用数据服务提供程序”** 图标。  
  
5.  在 **“创建新的直接联机第三方引用数据服务提供程序”** 对话框中，指定以下详细信息：  
  
    1.  在 **“名称”** 框中，键入新的直接引用数据服务提供程序的名称。  
  
    2.  （可选）在 **“说明”** 框中，键入新的直接引用数据服务提供程序的说明。  
  
    3.  在 **“类别”** 框中，键入新的直接引用数据服务提供程序提供的数据类别。  
  
    4.  在“架构”框中，指定一个架构，此架构定义要从直接引用数据服务提供程序中使用的字段（列名称）的字符串。 字段名称不能包含空格，且字段应该用逗号进行分隔。 例如： `FirstName, LastName, City, State`。  
  
    5.  在 **URI** 框中，键入直接引用数据服务提供程序的 URI。 DQS 中仅允许安全 URI（地址以 “https://” 开头）。  
  
    6.  在 **“最大批处理大小”** 框中，键入将发送到引用数据服务提供程序以执行清理的每批的最大记录数。 可为清理活动指定每批最多 100 条记录。  
  
    7.  在 **“帐户 ID”** 框中，键入订阅引用数据服务提供程序的用户的帐户 ID。  
  
6.  单击 **“确定”** 以保存该数据，然后关闭 **“创建新的直接联机第三方引用数据服务提供程序”** 对话框。 新添加的直接联机第三方引用数据提供程序将可用于 DQS 的 **“直接引用数据服务提供程序”** 网格中。  
  
 您现在可以在 DQS 中使用新配置的直接联机第三方引用数据服务提供程序提供的引用数据服务。  
  
##  <a name="follow-up-after-configuring-dqs-to-use-reference-data"></a><a name="FollowUp"></a>跟进：在将 DQS 配置为使用引用数据后  
 现在您必须将所需的知识库域映射到您刚配置的数据提供程序所提供的引用数据。 若要执行此操作，请参阅[将域或复合域附加到引用数据](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)。  
  
  
