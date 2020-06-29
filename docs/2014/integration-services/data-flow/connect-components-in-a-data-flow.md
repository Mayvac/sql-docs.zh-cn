---
title: 连接数据流中的组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb04140fc5a065b93f8a08533b24ca786fc9202c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432334"
---
# <a name="connect-components-in-a-data-flow"></a>连接数据流中的组件
  本过程介绍如何将数据流中的组件输出连接到同一数据流中的其他组件。  
  
### <a name="to-connect-components-in-a-data-flow"></a>连接数据流中的组件  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。  
  
2.  在解决方案资源管理器中，双击该包将其打开。  
  
3.  单击“控制流”**** 选项卡，然后双击包含要连接的组件所在数据流的数据流任务。  
  
4.  在 **“数据流”** 选项卡的设计图面上，选择要连接的转换或源。  
  
5.  将转换或源的绿色输出箭头拖动到转换或目标。 某些数据流组件有错误输出，这些输出可通过同样方式连接。  
  
    > [!NOTE]  
    >  某些数据流组件可能有多个输出，您可以将每一个输出连接到不同的转换或目标。  
  
6.  若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
## <a name="see-also"></a>另请参阅  
 [在数据流中添加或删除组件](data-flow.md)   
 [在数据流组件中配置错误输出](../configure-an-error-output-in-a-data-flow-component.md)   
 数据流  
  
  
