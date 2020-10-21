---
description: 维度处理目标自定义属性
title: 维度处理目标自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e6959edde524e2219573793b5becb34f5d63f1c
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192717"
---
# <a name="dimension-processing-destination-custom-properies"></a>维度处理目标自定义属性

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  维度处理目标具有自定义属性和所有数据流组件通用的属性。  
  
 下表介绍了纬度处理目标的自定义属性。 所有属性均可读/写。  
  
|属性|数据类型|说明|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的实例或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目的连接字符串。|  
|KeyDuplicate|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理重复键错误的值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **IgnoreError** (0)。|  
|KeyErrorAction|Integer（枚举）|当 UseDefaultConfiguration 为 **False**时，指示如何处理键错误的值。 可能的值有 **ConvertToUnknown** (0) 和 **DiscardRecord** (1)。 此属性的默认值为 **ConvertToUnknown** (0)。|  
|KeyErrorLimit|Integer|当 UseDefaultConfiguration 为 **False**时，启用键错误的上限。|  
|KeyErrorLimitAction|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示达到 **KeyErrorLimit** 时需采取何种操作的值。 可能的值有 **StopLogging** (1) 和 **StopProcessing** (0)。 此属性的默认值为 **StopProcessing** (0)。|  
|KeyErrorLogFile|String|UseDefaultConfiguration 为 **False**时，指示错误日志文件的路径和文件名。|  
|KeyNotFound|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理缺失键错误的值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **IgnoreError** (0)。|  
|NullKeyConvertedToUnknown|Integer（枚举）|当 UseDefaultConfiguration 为 **False**时，指示如何处理 null 键转换为未知值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **IgnoreError** (0)。|  
|NullKeyNotAllowed|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理不允许的 null 的值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **IgnoreError** (0)。|  
|ProcessType|Integer（枚举）|转换使用的维度处理类型。 值有 **ProcessAdd** (1)（增量）、 **ProcessFull** (0) 和 **ProcessUpdate** (2)。|  
|UseDefaultConfiguration|布尔|一个指定转换是否使用默认错误配置的值。 如果此属性为 **False**，则转换包含有关错误处理的信息。|  
  
 维度处理目标的输入和输入列没有自定义属性。  
  
 有关详细信息，请参阅 [Dimension Processing Destination](../../integration-services/data-flow/dimension-processing-destination.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Common Properties](./set-the-properties-of-a-data-flow-component.md)  
  
