---
description: 数据挖掘扩展插件 (DMX) 参考
title: 数据挖掘扩展插件 (DMX) 参考 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bd6830e46f10ba20642d1975f293b72b768f7e5b
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726248"
---
# <a name="data-mining-extensions-dmx-reference"></a>数据挖掘扩展插件 (DMX) 参考
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  数据挖掘扩展插件 (DMX) 是一种可用于在中创建和使用数据挖掘模型的语言 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。 可以使用 DMX 创建新数据挖掘模型的结构、为这些模型定型并对其进行浏览、管理和预测。 DMX 由数据定义语言 (DDL) 语句、数据操作语言 (DML) 语句以及函数和运算符组成。  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Microsoft OLE DB for Data Mining 规范  
 中的数据挖掘功能的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 构建符合 [!INCLUDE[msCoName](../includes/msconame-md.md)] 数据挖掘规范 OLE DB。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]数据挖掘规范 OLE DB 定义以下各项：  
  
-   一种用于保存有关定义数据挖掘模型信息的结构。  
  
-   一种用于创建和处理数据挖掘模型的语言。  
  
 该规范以数据挖掘模型虚拟对象的形式定义数据挖掘的基础。 数据挖掘模型对象将封装所有有关特定挖掘模型的已知内容。 数据挖掘模型对象的结构与 SQL 表类似，包含用于说明模型的列、数据类型和元信息。 该结构允许您使用 DMX 语言（一种 SQL 扩展语言）来创建和处理模型。  
  
 **有关详细信息，请执行以下操作：** [挖掘结构 &#40;Analysis Services 数据挖掘&#41;](/analysis-services/data-mining/mining-structures-analysis-services-data-mining)  
  
##  <a name="dmx-statements"></a><a name="BKMK_DMXStatements"></a> DMX 语句  
 可以使用 DMX 语句创建、处理、删除、复制、浏览和预测数据挖掘模型。 DMX 中有两种类型的语句：数据定义语句和数据操作语句。 可以使用每种类型的语句执行各种不同的任务。  
  
 有关使用 DMX 语句的详细信息，请参考以下部分的内容：  
  
-   [数据定义语句](#BKMK_DDL)  
  
-   [数据操作语句](#BKMK_DML)  
  
-   [查询基础知识](#BKMK_Queries)  
  
###  <a name="data-definition-statements"></a><a name="BKMK_DDL"></a> 数据定义语句  
 使用 DMX 中的数据定义语句可以创建和定义新的挖掘结构和模型，导入和导出挖掘模型和挖掘结构，以及从数据库中删除现有模型。 DMX 中的数据定义语句属于数据定义语言 (DDL)。  
  
 使用 DMX 中的数据定义语句可以执行下列任务：  
  
-   使用 [CREATE 挖掘 structure](../dmx/create-mining-structure-dmx.md) 语句创建挖掘结构，并使用 [ALTER 挖掘 structure](../dmx/alter-mining-structure-dmx.md) 语句将挖掘模型添加到挖掘结构中。  
  
-   使用 [CREATE 挖掘 model](../dmx/create-mining-model-dmx.md) 语句生成空的数据挖掘模型对象，同时创建挖掘模型和关联的挖掘结构。  
  
-   使用 [export](../dmx/export-dmx.md) 语句将挖掘模型和关联的挖掘结构导出到文件。 使用 [import](../dmx/import-dmx.md) 语句从 EXPORT 语句创建的文件中导入挖掘模型和关联的挖掘结构。  
  
-   使用 [SELECT into](../dmx/select-into-dmx.md) 语句将现有挖掘模型的结构复制到新模型中，并使用相同的数据对其进行定型。  
  
-   使用 [DROP 挖掘 model](../dmx/drop-mining-model-dmx.md) 语句从数据库中完全删除挖掘模型。 使用 [DROP 挖掘 structure](../dmx/drop-mining-structure-dmx.md) 语句，从数据库中完全删除挖掘结构及其关联的所有挖掘模型。  
  
 若要了解有关使用 DMX 语句可以执行的数据挖掘任务的详细信息，请参阅 [&#40;DMX&#41; 语句参考中的数据挖掘扩展插件](../dmx/data-mining-extensions-dmx-statements.md)。  
  
 [返回到 DMX 语句](#BKMK_DMXStatements)  
  
###  <a name="data-manipulation-statements"></a><a name="BKMK_DML"></a> 数据操作语句  
 使用 DMX 中的数据操作语句可以处理现有挖掘模型、浏览模型以及对模型创建预测。 DMX 中的数据操作语句属于数据操作语言 (DML)。  
  
 使用 DMX 中的数据操作语句可以执行下列任务：  
  
-   使用 [INSERT INTO](../dmx/insert-into-dmx.md) 语句为挖掘模型定型。 执行该语句不会将实际源数据插入数据挖掘模型对象，但会创建有关说明算法所创建的挖掘模型的摘要信息。 中介绍了 INSERT INTO 语句的源查询 [\<source data query>](../dmx/source-data-query.md) 。  
  
-   扩展 SELECT 语句以浏览模型定型过程中计算并存储在数据挖掘模型中的信息，如源数据的统计信息。 以下子句可用于扩展 SELECT 语句的强大功能：  
  
    -   [选择 "与 &#60;模型不同" &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [从 &#60;模型&#62; 中进行选择。内容 &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
    -   [从 &#60;模型&#62; 中进行选择。DMX&#41;&#40;情况 ](../dmx/select-from-model-cases-dmx.md)  
  
    -   [从 &#60;模型&#62; 中进行选择。SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [从 &#60;模型&#62; 中进行选择。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   使用 SELECT 语句的 [预测联接](../dmx/select-from-model-prediction-join-dmx.md) 子句创建基于现有挖掘模型的预测。 中介绍了预测联接语句的源查询 [\<source data query>](../dmx/source-data-query.md) 。  
  
-   使用 [DELETE &#40;DMX&#41;](../dmx/delete-dmx.md) 语句，从模型或结构中删除所有定型的数据。  
  
 若要了解有关使用 DMX 语句可以执行的数据挖掘任务的详细信息，请参阅 [&#40;DMX&#41; 语句参考中的数据挖掘扩展插件](../dmx/data-mining-extensions-dmx-statements.md)。  
  
 [返回到 DMX 语句](#BKMK_DMXStatements)  
  
###  <a name="dmx-query-fundamentals"></a><a name="BKMK_Queries"></a> DMX 查询基础知识  
 SELECT 语句是大多数 DMX 查询的基础。 通过将各种子句与此类语句组合使用，可以浏览、复制或预测挖掘模型。 预测查询使用 SELECT 窗体根据现有挖掘模型创建预测。 函数在数据挖掘模型的固有功能的基础上，扩展了您浏览和查询挖掘模型的能力。  
  
 使用 DMX 函数可以获取在模型定型过程中发现的信息，并且还可以计算新的信息。 这些函数可用于多种用途，包括返回说明基础数据或预测精确性的统计信息，或返回预测的详细说明。  
  
 **有关详细****信息，请参阅**[了解 Dmx Select 语句](../dmx/understanding-the-dmx-select-statement.md)、[常规预测函数 &#40;Dmx&#41;](../dmx/general-prediction-functions-dmx.md)、[结构和使用 DMX 预测查询](../dmx/structure-and-usage-of-dmx-prediction-queries.md)、[数据挖掘扩展插件 &#40;dmx&#41; 函数引用](../dmx/data-mining-extensions-dmx-function-reference.md)    
  
 [返回到 DMX 语句](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘扩展插件 &#40;DMX&#41; 函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 运算符引用](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 语句参考](../dmx/data-mining-extensions-dmx-statements.md)   
 [数据挖掘扩展插件 &#40;DMX&#41; 语法约定](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [&#40;DMX&#41; 语法元素的数据挖掘扩展插件](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [&#40;DMX&#41;的常规预测函数 ](../dmx/general-prediction-functions-dmx.md)   
 [DMX 预测查询的结构和用法](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 语句](../dmx/understanding-the-dmx-select-statement.md)  
  
