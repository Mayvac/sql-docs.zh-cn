---
title: 筛选设置（对象资源管理器和实用工具资源管理器）
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.common.filtersettings.f1
- sql13.ag.job.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 66ae081ad6fcfb5b5d361201430ea9fb4d8dcd6c
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001964"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a>筛选设置（对象资源管理器和实用工具资源管理器）
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
使用此对话框可以指定筛选器。 使用筛选器，可以将对象资源管理器和实用工具资源管理器配置为仅显示符合特定条件的项。 例如，可以使用筛选器仅显示名称中包含词语“维护”的作业。 “筛选设置”  对话框的标题包含服务器的名称，还可能包含数据库的名称。  
  
## <a name="ui-element-list"></a>UI 元素列表  
**属性**  
显示要筛选的属性。  
  
**“运算符”**  
选择筛选器将值应用于属性的方式。 下面是可用的选项：  
  
-   **等于**  
  
    筛选器将显示属性和值都精确匹配的项。  
  
-   **包含**  
  
    筛选器将显示属性包含指定值的项。 属性可能会包含其他文本。  
  
-   **不包含**  
  
    筛选器将显示属性不包含指定值的项。  
  
-   **小于**  
  
    此筛选器适用于日期，将显示日期早于指定值的项。  
  
-   **小于或等于**  
  
    此筛选器适用于日期，将显示日期早于或等于指定值的项。  
  
-   **大于**  
  
    此筛选器适用于日期，将显示日期晚于指定值的项。  
  
-   **大于或等于**  
  
    此筛选器适用于日期，将显示日期晚于或等于指定值的项。  
  
-   **Between**  
  
    此筛选器适用于日期，将显示日期介于指定的两个日期之间的项。 选择“介于”  并按 Tab 即可添加另一行，用于指定第二个日期。  
  
-   **不介于**  
  
    此筛选器适用于日期，将显示日期不介于指定的两个日期之间的项。 选择“不介于”  并按 Tab 移出“运算符”  列，即可添加另一行，用于指定第二个日期。  
  
**值**  
键入要与属性进行比较的值。 对于日期，请单击下箭头显示日历，以选择日期。  
  
**清除筛选器**  
删除所有当前筛选设置。  
  
## <a name="see-also"></a>另请参阅  
[使用 SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
[SQL Server 实用工具概述](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
