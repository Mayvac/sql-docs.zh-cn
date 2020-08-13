---
title: ODBC 连接类型 | Microsoft Docs
description: 利用本文中有关 ODBC 连接类型的信息，了解如何生成数据源。
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b8e41696695ec8a95dd16d1f30724147cdd359a1
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458969"
---
# <a name="odbc-connection-type-ssrs"></a>ODBC 连接类型 (SSRS)
  若要包含来自 ODBC 数据访问接口的数据，必须拥有一个基于类型为 ODBC 的报表数据源的数据集。 此内置数据源类型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC 数据处理扩展插件。  
  
 使用本主题中的信息来生成一个数据源。 有关分步说明，请参阅 [添加和验证数据连接（报表生成器和 SSRS）](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)。  
  
##  <a name="connection-string"></a><a name="Connection"></a> 连接字符串  
 用于 ODBC 数据处理扩展插件的连接字符串取决于您想要的 ODBC 驱动程序。 典型的连接字符串包含驱动程序支持的名称/值对。 例如，下面的连接字符串为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 和 AdventureWorks 数据库指定 ODBC 驱动程序。  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> 凭据  
 执行以下操作时需要提供凭据：运行查询、本地预览报表以及从报表服务器预览报表。  
  
 报表发布后，您可能需要更改数据源的凭据，以使报表在报表服务器上运行时，用于检索数据的权限有效。  
  
 如果将 ODBC 数据源配置为提示输入密码或在连接字符串中包含密码，并且用户输入了带有如标点符号之类特殊字符的密码，则某些基础数据源驱动程序无法验证这些特殊字符。 处理报表时，可能会出现“密码无效”这一消息来指示此问题。 如果不能更改密码，则可以使用数据库管理员角色将相应的凭据作为系统 ODBC 数据源名称 (DSN) 的一部分存储在报表服务器中。 有关详细信息，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档中的“OdbcConnection.ConnectionString”。  
  
> [!NOTE]  
>  建议您不要在连接字符串中添加登录信息（如密码）。 报表生成器在 **“数据源”** 对话框中提供了一个用于输入凭据的单独选项卡。  
  
 有关详细信息，请参阅[创建数据连接字符串 - 报表生成器和 SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) 或[为报表数据源指定凭据和连接信息](specify-credential-and-connection-information-for-report-data-sources.md)。  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> 注释  
 ODBC 是在 OLEDB 之前采用的一种早期数据访问技术。 ODBC 只支持关系数据源。 ODBC 数据访问接口称为“驱动程序” 。 ODBC 驱动程序由 Microsoft 和第三方供应商提供。 例如，Microsoft Office 安装了连接到 Office 文件格式的 ODBC 驱动程序。  
  
 必须先安装 ODBC 驱动程序并生成计算机或系统 DSN，才能生成 ODBC 连接字符串。 若要成功检索到想要的数据，则必须提供驱动程序支持的查询语法。 参数支持因驱动程序而异。 有关详细信息，请参阅特定于所选驱动程序的主题，例如，[SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)。  
  
###### <a name="platform-and-version-information"></a>平台和版本信息  
 有关特定 ODBC 数据提供程序的详细信息，请参阅 [Reporting Services 支持的数据源 (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)。
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> 操作指南主题  
 本节包含使用数据连接、数据源和数据集的分步说明。  
  
 [添加和验证数据连接（报表生成器和 SSRS）](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [创建共享数据集或嵌入数据集（报表生成器和 SSRS）](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [向数据集添加筛选器（报表生成器和 SSRS）](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
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
  
 [Reporting Services 支持的数据源 &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)。 提供有关每个数据扩展插件的平台和版本支持的详细信息。  
  
  
## <a name="see-also"></a>另请参阅  
 [报表参数（报表生成器和报表设计器）](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [表达式（报表生成器和 SSRS）](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
