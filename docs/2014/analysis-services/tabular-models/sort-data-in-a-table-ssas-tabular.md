---
title: 对表中的数据进行排序（SSAS 表格） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: cf1a9c8782e1771d5a53700b5f72c48dbb300c7a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938648"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a>对表中的数据进行排序（SSAS 表格）
  可以按文本（从 A 到 Z 或从 Z 到 A）和按数字（从小到大或从大到小）对一个或多个列中的数据进行排序。  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>基于文本列对表数据进行排序  
  
1.  在模型设计器中，选择某一字母数字数据列或者列中的某一范围的单元，或者确保活动单元处于包含字母数字数据的表列中，然后单击要作为筛选依据的列标题中的箭头。  
  
2.  在“自动筛选”菜单中，执行以下操作之一：  
  
    -   若要按字母数字的升序排序，请单击 **“从 A 到 Z 排序”**。  
  
    -   若要按字母数字的降序排序，请单击 **“从 Z 到 A 排序”**。  
  
    > [!NOTE]  
    >  在某些情况下，从其他应用程序导入的数据之前可能插入了前导空格。 您必须删除这些前导空格才能正确对数据进行排序。  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>基于数字列对表数据进行排序  
  
1.  在模型设计器中，选择某一字母数字数据列或者列中的某一范围的单元，或者确保活动单元处于包含字母数字数据的表列中，然后单击要作为筛选依据的列标题中的箭头。  
  
2.  在“自动筛选”菜单中，执行以下操作之一：  
  
    -   若要从小到大对数字进行排序，请单击 **“从小到大排序”**。  
  
    -   若要从大到小对数字进行排序，请单击 **“从大到小排序”**。  
  
    > [!NOTE]  
    >  如果得到的并不是期望的结果，列中可能包含存储为文本而不是数字的数字。 例如，从某些会计系统导入的负数或是以 '（撇号）开头的数字均存储为文本。  
  
## <a name="see-also"></a>另请参阅  
 [&#40;SSAS 表格中对数据进行筛选和排序&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [SSAS 表格&#41;&#40;透视](perspectives-ssas-tabular.md)   
 [角色（SSAS 表格）](roles-ssas-tabular.md)  
  
  
