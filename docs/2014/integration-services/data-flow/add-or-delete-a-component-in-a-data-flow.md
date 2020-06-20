---
title: 在数据流中添加或删除组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 1d66397729b4263cfed4a2911417b932d049fd30
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84916849"
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a>在数据流中添加或删除组件
  数据流组件是数据流中的源、目标和转换。 包中的控制流必须包含数据流任务，然后才能向数据流添加组件。  
  
 下面的过程介绍如何在包的数据流中添加或删除组件。  
  
### <a name="to-add-a-component-to-a-data-flow"></a>向数据流添加组件  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。  
  
2.  在解决方案资源管理器中，双击该包将其打开。  
  
3.  单击“控制流”选项卡，然后双击包含要向其添加组件的数据流的数据流任务。   
  
4.  在工具箱中，展开 **“数据流源”** 、 **“数据流转换”** 或 **“数据流目标”** ，然后将数据流项拖动到 **“数据流”** 选项卡的设计图面。  
  
5.  若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
### <a name="to-delete-a-component-from-a-data-flow"></a>从数据流删除组件  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。  
  
2.  在解决方案资源管理器中，双击该包将其打开。  
  
3.  单击“控制流”选项卡，然后双击包含要从中删除组件的数据流的数据流任务。   
  
4.  右键单击数据流组件，然后单击“删除”  。  
  
5.  确认删除操作。  
  
6.  若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
## <a name="see-also"></a>另请参阅  
 [连接数据流中的组件](data-flow.md)   
 [在数据流组件中配置错误输出](../configure-an-error-output-in-a-data-flow-component.md)   
 [数据流](data-flow.md)  
  
  
