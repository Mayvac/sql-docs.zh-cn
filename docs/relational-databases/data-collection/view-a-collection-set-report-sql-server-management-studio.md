---
title: 查看收集组报表 (SSMS)
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 161fbacb2edc8d73d69bbc501e255ce657f6208c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715519"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a>查看收集组报表 (SQL Server Management Studio)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  配置了管理数据仓库后，可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看收集组报表。 针对安装过程中安装的系统数据收集组提供了报表。 这些报表包括：  
  
-   磁盘使用情况摘要  
  
-   查询统计信息历史记录  
  
-   服务器活动历史记录  
  
 此过程会显示 **“磁盘使用情况”** 收集组的报表。 您可以使用同样的常规过程来查看其他系统数据收集组的报表。  
  
### <a name="to-view-a-collection-set-report"></a>查看收集组报表  
  
1.  首次上载收集的数据时会为报表创建表。 如果尝试在首次上载之前查看报表，则将出现错误并且不会显示报表。 若要上传磁盘使用情况收集组的数据，请在对象资源管理器中依次展开“管理”  文件夹、“数据收集”  和“系统数据收集组”  ，右键单击“磁盘使用情况”  收集组，然后单击“立即收集并上传”  。  
  
2.  若要查看报表，请在对象资源管理器中依次“管理”  文件夹，右键单击“数据收集”  ，依次指向“报表”  “管理数据仓库”  ，然后单击“磁盘使用情况摘要”  。  
  
    > [!NOTE]  
    >  有些报告可能会在数据收集时间线下显示日历按钮。 单击此按钮可访问 **“数据收集报告日历”** 。  
  
#### <a name="data-collection-report-calendar"></a>“数据收集报告日历”  
 使用该对话框可指定要报告的数据的开始日期、开始时间和持续时间。 例如，可能要报告上星期三某特定 12 小时内服务器的磁盘使用活动。  
  
 **开始日期**  
 输入报表数据的开始日期，或从日历选择一个日期。  
  
 **开始时间**  
 输入报表数据的开始时间或单击箭头以指定一个时间。  
  
 **Duration**  
 指定在报表中要包括的时间范围。 默认值为 240 分钟。 可从以下值中进行选择：15 分钟、60 分钟、240 分钟（4 小时）、720 分钟（12 小时）和 1440 分钟（24 小时）。  
  
## <a name="see-also"></a>另请参阅  
 [数据收集](../../relational-databases/data-collection/data-collection.md)   
 [Management Studio 中的自定义报表](../../ssms/object/custom-reports-in-management-studio.md)   
 [配置管理数据仓库 (SQL Server Management Studio)](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
