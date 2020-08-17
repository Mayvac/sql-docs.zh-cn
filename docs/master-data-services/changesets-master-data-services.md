---
description: 变更集 (Master Data Services)
title: 变更集
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f227c49a-ed46-4e0f-8992-83093456cf94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7171e28103ebf0c18657a62a954faa1ca64cdf5a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88345013"
---
# <a name="changesets-master-data-services"></a>变更集 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 现在支持将任何挂起的更改作为变更集保存到实体。 此功能有两种使用场景。  
  
-   **当实体管理员打开 "需要批准" 时进行更改**  
  
     如果实体管理员指定对指定实体的更改在提交前需要批准，那么对实体的任何更改必须先保存到新的或现有的变更集，才能提交以供批准。  有关详细信息，请参阅[需要审批 (Master Data Services)](../master-data-services/approval-required-master-data-services.md)  
  
     请遵循以下工作流。  
  
    1.  创建变更集。 变更集处于打开状态。 请参阅 [创建变更集 (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  应用变更集，并向变更集中添加一些更改。 请参阅 [应用并更新变更集&#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  将变更集提交给实体管理员进行批准。 变更集处于挂起状态。 请参阅 [确认或提交变更 (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
    4.  实体管理员收到变更集等待批准的电子邮件通知。 如果实体管理员批准变更集，则该变更集处于已批准状态。 请参阅 [批准或拒绝变更集 (Master Data Services)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
    5.  将自动提交已批准变更集。 如果已成功提交更改，则变更集处于已提交状态。  
  
-   **本地用户更改**  
  
     如果只想要保存本地更改，以便以后使用或检索它们，则可以使用变更集来实现此目的。  
  
     请遵循以下工作流。  
  
    1.  创建变更集。 变更集处于打开状态。 请参阅 [创建变更集 (Master Data Services)](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  应用变更集，并向变更集中添加一些更改。 请参阅 [应用并更新变更集&#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  完成后，提交变更集。 请参阅 [确认或提交变更 (Master Data Services)](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>另请参阅  
 [创建变更集 &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [应用并更新变更集 &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [提交或提交变更集 &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [批准或拒绝变更集 &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)   
 [管理变更集 &#40;Master Data Services&#41;](../master-data-services/manage-changesets-master-data-services.md)  
  
  
