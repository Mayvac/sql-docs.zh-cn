---
description: 概述：从 Excel 导入数据（适用于 Excel 的 MDS 加载项）
title: 从 Excel 导入数据
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: df78497bc65d383a3dc44225971ab1df742f32b5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "92257781"
---
# <a name="overview-importing-data-from-excel-mds-add-in-for-excel"></a>概述：从 Excel 导入数据（适用于 Excel 的 MDS 加载项）

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，要想与其他用户共享数据，可将数据发布到 MDS 存储库。 数据一经发布，即可供该外接程序的其他用户下载。  
  
 发布数据时，已添加或更新的所有数据都会发布到 MDS 存储库。 已删除的数据不会发布，必须单独删除数据。 有关详细信息，请参阅 [删除行（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/delete-a-row-mds-add-in-for-excel.md)。  
  
> [!NOTE]  
>  发布不能用于创建新实体。 有关创建实体的详细信息，请参阅[创建实体（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/create-an-entity-mds-add-in-for-excel.md)。  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a>当多个用户同时发布时  
 多个用户可以对相同的数据发布更新。 更新会在每个用户发布时保存到数据库中。 这表示未使用最近更新的数据的用户仍可以在自己发布时更改数据值。  
  
 只有更新的数据才会发布到数据库中。 不发布工作表中的任何过时数据。  
  
## <a name="transactions-and-annotations"></a>事务和批注  
 每个已发布的更改都保存为一个事务。 如果您愿意，则可以向事务添加批注（注释），解释您做出更改的原因。  
  
-   您不能为删除操作添加批注，尽管删除操作可另存为管理员可以撤消的事务。  
  
-   如果更改成员的 **Code** 值，该成员以前所有的事务都将不可用。 通过将 **Code** 值返回为原始值，你可以访问以前的事务。  
  
-   您可以查看其他用户对成员执行的事务。 还可以查看对成员执行的所有事务，即便不再对特定属性拥有权限。 你不能查看与你的权限设置为拒绝的属性相关的事务。  
  
 您可以查看对成员执行的所有事务。 有关详细信息，请参阅 [查看成员的所有批注或事务（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)。  
  
> [!IMPORTANT]  
>  如果您输入的批注超过 500 个字符，该批注将被自动截断。  
  
## <a name="business-rule-and-other-validation"></a>业务规则和其他验证  
 发布数据时，将执行验证，在确保数据准确无误后才将其添加到 MDS 存储库中。 如果数据不符合指定的条件，则不会将其发布到存储库。 有关详细信息，请参阅[验证数据（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|任务说明|主题|  
|----------------------|-----------|  
|将数据从活动工作表发布回 MDS 存储库。|[将数据从 Excel 导入 Master Data Services（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|同时从 MDS 存储库和工作表中删除行。|[删除行（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/delete-a-row-mds-add-in-for-excel.md)|  
|如果要随时查看数据更新，可查看数据行（成员）的批注（注释）和事务。|[查看成员的所有批注或事务（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|当你在发布前想要比较数据时，合并来自两个工作表的数据。|[合并数据（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md)|  

  
## <a name="related-content"></a>相关内容  
  
-   [刷新数据（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/refreshing-data-mds-add-in-for-excel.md)  
  
-   [用于 Microsoft Excel 的 Master Data Services 外接程序](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  
