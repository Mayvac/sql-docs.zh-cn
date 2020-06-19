---
title: 删除业务规则 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 934a25748e76706634073babf3b4df56b328670b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971627"
---
# <a name="delete-a-business-rule-master-data-services"></a>删除业务规则 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当不再需要某个业务规则时，可以删除它。  
  
> [!NOTE]  
>  您可以通过排除业务规则而不是删除它来防止针对业务规则验证数据。 有关详细信息，请参阅 [排除业务规则 (Master Data Services)](exclude-a-business-rule-master-data-services.md)。  
  
## <a name="prerequisites"></a>必备条件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。  
  
### <a name="to-delete-a-business-rule"></a>删除业务规则  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。  
  
3.  在 **“业务规则维护”** 页上，从 **“模型”** 列表中，选择某一模型。  
  
4.  从 **“实体”** 列表中，选择某一实体。  
  
5.  从 **“成员类型”** 列表中，为要应用于的业务规则选择成员类型。  
  
6.  从 **“属性”** 列表中，选择某一属性或保持默认值 **“全部”**。  
  
7.  在网格中，单击要删除的业务规则所对应的行。  
  
8.  单击 "**删除所选业务规则**"。  
  
9. 在确认对话框中，单击 **“确定”**。 "**状态**" 列中的值为 "**待删除**"。  
  
10. 单击 **“发布业务规则”**。  
  
11. 在确认对话框中，单击 **“确定”**。  
  
## <a name="see-also"></a>另请参阅  
 [排除业务规则 &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md)   
 [创建和发布业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [业务规则 (Master Data Services)](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
