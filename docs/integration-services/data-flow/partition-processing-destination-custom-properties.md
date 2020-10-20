---
description: 分区处理目标自定义属性
title: 分区处理目标自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a4575b22bc7321322fbb51acdabded7a7039473d
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195339"
---
# <a name="partition-processing-destination-custom-properties"></a>分区处理目标自定义属性

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  分区处理目标具有自定义属性和所有数据流组件通用的属性。  
  
 下表介绍分区处理目标的自定义属性。 所有属性均可读/写。  
  
|属性|数据类型|说明|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例的连接字符串。|  
|KeyDuplicate|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理重复键错误的值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **IgnoreError** (0)。|  
|KeyErrorAction|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理键错误的值。 可能的值有 **ConvertToUnknown** (0) 和 **DiscardRecord** (1)。 此属性的默认值为 **ConvertToUnknown** (0)。|  
|KeyErrorLimit|Integer|UseDefaultConfiguration 为 **False**时，允许键错误的上限。|  
|KeyErrorLimitAction|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示达到 **KeyErrorLimit** 时需采取何种操作的值。 可能的值有 **StopLogging** (1) 和 **StopProcessing** (0)。 此属性的默认值为 **StopProcessing** (0)。|  
|KeyErrorLogFile|String|UseDefaultConfiguration 为 **False**时，指示错误日志文件的路径和文件名。|  
|KeyNotFound|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理缺失键错误的值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **ReportAndContinue** (1)。|  
|NullKeyConvertedToUnknown|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理 null 键转换为 Unknown 值的值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **IgnoreError** (0)。|  
|NullKeyNotAllowed|Integer（枚举）|UseDefaultConfiguration 为 **False**时，指示如何处理不允许的 null 的值。 可能的值有 **IgnoreError** (0)、 **ReportAndContinue** (1) 和 **ReportAndStop** (2)。 此属性的默认值为 **ReportAndContinue** (1)。|  
|ProcessType|Integer（枚举）|转换使用的分区处理的类型。 可能的值有 **ProcessAdd** (1)（增量）、 **ProcessFull** (0) 和 **ProcessUpdate** (2)。|  
|UseDefaultConfiguration|布尔|一个指定转换是否使用默认错误配置的值。 如果此属性为 **False**，则转换使用此表中列出的错误处理自定义属性的值，包括 KeyDuplicate 和 KeyErrorAction 等。|  
  
 分区处理目标的输入和输入列没有自定义属性。  
  
 有关详细信息，请参阅 [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Common Properties](./set-the-properties-of-a-data-flow-component.md)  
  
