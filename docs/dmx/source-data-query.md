---
title: '&lt;源数据查询 &gt; |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 15767abbbffd7ede7d7ae252c7e84589abad1a98
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670017"
---
# <a name="ltsource-data-querygt"></a>&lt;源数据查询&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  若要为数据挖掘模型定型并从挖掘模型创建预测，您必须访问数据库外部的数据 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。 使用 \< 数据挖掘扩展插件（DMX）中的源数据查询> 子句来定义此外部数据。 [INSERT INTO &#40;dmx&#41;](../dmx/insert-into-dmx.md)中，[从 &#60;模型中选择&#62; 预测联接 &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)，然后[选择 "从自然预测联接](../dmx/select-from-model-prediction-join-dmx.md)语句" "所有使用** \< 源数据查询>**"。  
  
## <a name="query-types"></a>查询类型  
 指定源数据最常用的三种方式包括：  
  
 [OPENQUERY &#40;DMX&#41;](../dmx/source-data-query-openquery.md)  
 通过使用现有数据源，此语句可查询 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例以外的数据。  
  
 虽然**openquery**在功能上类似于**OPENROWSET**，但**openquery**具有以下优势：  
  
-   使用**OPENQUERY**编写 DMX 查询要容易得多。 您可以利用数据源中现有的连接字符串，而无需在每次编写查询时都创建一个新的连接字符串。 数据源对象还可以控制各个用户对数据的访问。  
  
-   管理员可以更好地控制对服务器上数据的访问方式。 例如，管理员可以管理哪些提供程序可以载入服务器以及可以访问哪些外部数据。  
  
 [OPENROWSET &#40;DMX&#41;](../dmx/source-data-query-openrowset.md)  
 通过使用现有数据源，此语句可查询 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例以外的数据。  
  
 [形状 &#40;DMX&#41;](../dmx/source-data-query-shape.md)  
 此语句可以查询多个数据源以创建嵌套表。 通过使用**形状**，您可以将来自多个源的数据合并成单个层次结构表。 这样便可利用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的功能，通过在表中嵌入表的方式来嵌套表。  
  
 若要指定源数据，还可以使用下列选项：  
  
-   任何有效的 DMX 语句  
  
-   任何有效的多维表达式 (MDX) 语句  
  
-   返回存储过程的表  
  
-   XML for Analysis (XMLA) 行集  
  
-   行集参数  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘扩展插件 &#40;DMX&#41; 数据操作语句](../dmx/dmx-statements-data-manipulation.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 语句参考](../dmx/data-mining-extensions-dmx-statements.md)   
 [嵌套表 &#40;Analysis Services 数据挖掘&#41;](https://docs.microsoft.com/analysis-services/data-mining/nested-tables-analysis-services-data-mining)  
  
  
