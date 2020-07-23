---
title: Integration Services 转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transformations [Integration Services], listed
- transformations [Integration Services], types
- transformations [Integration Services]
- data flow [Integration Services], transformations
- business intelligence transformations [Integration Services]
- join transformations
- split transformations [Integration Services]
- custom transformations [Integration Services]
- row transformations [Integration Services]
- rowset transformations [Integration Services]
ms.assetid: c70c4f6e-82dd-4948-b923-fd5193f67f7e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff200828c1204d15f648ec783fe720d86ac22dd1
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919243"
---
# <a name="integration-services-transformations"></a>Integration Services 转换

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 转换是包的数据流中对数据进行聚合、合并、分发和修改的组件。 转换还可以执行查找操作并生成样本数据集。 本节介绍 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 所包括的转换并说明它们是如何工作的。  
  
## <a name="business-intelligence-transformations"></a>商业智能转换  
 下列转换执行商业智能操作，例如清除数据、挖掘文本以及运行数据挖掘预测查询。  
  
|转换|说明|  
|--------------------|-----------------|  
|[渐变维度转换](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)|配置渐变维度更新的转换。|  
|[模糊分组转换](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)|对列数据中的值进行标准化的转换。|  
|[模糊查找转换](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)|使用模糊匹配查找引用表中的值的转换。|  
|[字词提取转换](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)|从文本中提取字词的转换。|  
|[字词查找转换](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)|在引用表中查找字词并对从文本中提取的字词进行计数的转换。|  
|[数据挖掘查询转换](../../../integration-services/data-flow/transformations/data-mining-query-transformation.md)|运行数据挖掘预测查询的转换。|  
|[DQS 清理转换](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)|通过应用为数据源创建的规则更正来自连接的数据源的数据的转换。|  
  
## <a name="row-transformations"></a>行转换  
 下列转换更新列值并创建新列。 转换应用于转换输入中的每个行。  
  
|转换|说明|  
|--------------------|-----------------|  
|[字符映射转换](../../../integration-services/data-flow/transformations/character-map-transformation.md)|将字符串函数应用于字符数据的转换。|  
|[复制列转换](../../../integration-services/data-flow/transformations/copy-column-transformation.md)|将输入列的副本添加到转换输出的转换。|  
|[数据转换](../../../integration-services/data-flow/transformations/data-conversion-transformation.md)|将列的数据类型转换为另一种数据类型的转换。|  
|[派生列转换](../../../integration-services/data-flow/transformations/derived-column-transformation.md)|用表达式的结果填充列的转换。|  
|[导出列转换](../../../integration-services/data-flow/transformations/export-column-transformation.md)|将数据流中的数据插入到文件中的转换。|  
|[导入列转换](../../../integration-services/data-flow/transformations/import-column-transformation.md)|读取文件中的数据并将其添加到数据流中的转换。|  
|[脚本组件](../../../integration-services/data-flow/transformations/script-component.md)|使用脚本提取、转换或加载数据的转换。|  
|[OLE DB 命令转换](../../../integration-services/data-flow/transformations/ole-db-command-transformation.md)|为数据流中的每个行运行 SQL 命令的转换。|  
  
## <a name="rowset-transformations"></a>行集转换  
 下列转换将创建新行集。 行集可以包括聚合值和已排序值、样本行集或者透视行集和逆透视行集。  
  
|转换|说明|  
|--------------------|-----------------|  
|[聚合转换](../../../integration-services/data-flow/transformations/aggregate-transformation.md)|执行聚合（如 AVERAGE、SUM 和 COUNT）的转换。|  
|[排序转换](../../../integration-services/data-flow/transformations/sort-transformation.md)|对数据进行排序的转换。|  
|[百分比抽样转换](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)|使用百分比指定样本大小来创建样本数据集的转换。|  
|[行抽样转换](../../../integration-services/data-flow/transformations/row-sampling-transformation.md)|通过指定样本中的行数来创建样本数据集的转换。|  
|[透视转换](../../../integration-services/data-flow/transformations/pivot-transformation.md)|创建规范化表的不太规范化版本的转换。|  
|[逆透视转换](../../../integration-services/data-flow/transformations/unpivot-transformation.md)|创建非规范化表的较规范化版本的转换。|  
  
## <a name="split-and-join-transformations"></a>拆分和联接转换  
 以下转换将行分发到不同的输出，创建转换输入的副本，将多个输入联接成一个输出，并执行查找操作。  
  
|转换|说明|  
|--------------------|-----------------|  
|[有条件拆分转换](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)|将数据行路由到不同输出的转换。|  
|[多播转换](../../../integration-services/data-flow/transformations/multicast-transformation.md)|将数据集分发到多个输出的转换。|  
|[Union All 转换](../../../integration-services/data-flow/transformations/union-all-transformation.md)|合并多个数据集的转换。|  
|[合并转换](../../../integration-services/data-flow/transformations/merge-transformation.md)|合并两个已排序数据集的转换。|  
|[合并联接转换](../../../integration-services/data-flow/transformations/merge-join-transformation.md)|使用 FULL、LEFT 或 INNER 联接将两个数据集联接起来的转换。|  
|[查找转换](../../../integration-services/data-flow/transformations/lookup-transformation.md)|使用完全匹配查找引用表中的值的转换。|  
|[缓存转换](../../../integration-services/data-flow/transformations/cache-transform.md)|将数据流中已连接数据源的数据写入到缓存连接管理器（将数据保存到缓存文件中）的转换。 查找转换会对缓存文件中的数据执行查找。|  
|[平衡数据分发器转换](../../../integration-services/data-flow/transformations/balanced-data-distributor-transformation.md)|转换将传入行的缓冲区均匀分布到各个独立线程的输出上，以提升运行在多核和多处理器服务器上的 SSIS 包的性能。|  
  
## <a name="auditing-transformations"></a>审核转换  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包括以下转换，用于添加审核信息和对行进行计数。  
  
|转换|说明|  
|--------------------|-----------------|  
|[审核转换](../../../integration-services/data-flow/transformations/audit-transformation.md)|使环境信息可用于包中数据流的转换。|  
|[行计数转换](../../../integration-services/data-flow/transformations/row-count-transformation.md)|对通过转换的行进行计数并将最终计数存储到变量中的转换。|  
  
## <a name="custom-transformations"></a>自定义转换  
 还可以编写自定义转换。 有关详细信息，请参阅 [开发具有同步输出的自定义转换组件](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) 和 [开发具有异步输出的自定义转换组件](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)。  
  
  
