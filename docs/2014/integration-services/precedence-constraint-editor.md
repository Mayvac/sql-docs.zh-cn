---
title: 优先约束编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba2c9c0c870294069dd1feb4eaabb72211877cc4
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423194"
---
# <a name="precedence-constraint-editor"></a>优先约束编辑器
  可以使用 **“优先约束编辑器”** 对话框配置优先约束。  
  
## <a name="options"></a>选项  
 **求值运算**  
 指定优先约束使用的求值运算。 运算包括： **“约束”**、 **“表达式”**、 **“表达式和约束”** 和 **“表达式或约束”**。  
  
 **值**  
 指定约束值：“成功” ****、“失败” **** 或“完成” ****。  
  
> [!NOTE]  
>   优先约束线的含义：绿色表示 **“成功”**，突出显示表示 **“失败”**，蓝色表示 **“完成”**。  
  
 **表达式**  
 如果使用运算“表达式”****、“表达式和约束”**** 或“表达式或约束”****，则键入一个表达式或启动表达式生成器来创建表达式。 表达式的计算结果必须为布尔值。  
  
 **测试**  
 验证表达式。  
  
 **逻辑与**  
 选择此选项可以指定：同一个可执行文件的多个优先约束必须一起计算。 所有约束的计算结果都必须为 `True`。  
  
> [!NOTE]  
>  这种类型的优先约束显示为绿色、突出显示或蓝色实线。  
  
 **逻辑或**  
 选择此选项可以指定：同一个可执行文件的多个优先约束必须一起计算。 至少必须有一个约束的计算结果为 `True`。  
  
> [!NOTE]  
>  这种类型的优先约束显示为绿色、突出显示或蓝色点线。  
  
## <a name="see-also"></a>另请参阅  
 [优先约束](control-flow/precedence-constraints.md)   
 [Integration Services 任务](control-flow/integration-services-tasks.md)   
 [Integration Services 容器](control-flow/integration-services-containers.md)   
 [Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)  
  
  
