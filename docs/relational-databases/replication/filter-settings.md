---
description: 筛选器设置
title: 筛选器设置 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 74ddf2a67970c290d427e777184eba74af28a3d1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486660"
---
# <a name="filter-settings"></a>筛选器设置
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  可以使用“筛选设置”**** 对话框为复制监视器中的网格定义筛选器。 例如，若要只显示 **“所有订阅”** 选项卡上处于活动状态的订阅，请从 **“列名”** 列选择 **“状态”** ，从 **“运算符”** 列选择 **“等于”** 并从 **“值1”** 列选择 **“活动”** 。 在您基于一个或多个列定义筛选器之后，将应用筛选器以便网格中只显示与筛选器条件匹配的子集行。  
  
## <a name="options"></a>选项  
 **列名称**  
 选择要对其进行筛选的列的名称。 您可以使筛选器基于一个或多个列。  
  
 **“运算符”**  
 为筛选器选择一个运算符，例如 **“小于或等于”**。  
  
 **“值1”** 和 **“值2”**  
 为筛选器输入或选择一个值。 大多数运算符只要求在 **“值1”** 列中提供值，但 **“介于”** 和 **“不介于”** 运算符还要求在 **“值2”** 列中提供值。  
  
 **清除筛选器**  
 单击此按钮可以清除已定义的所有筛选器。 若要删除某个筛选器，请选中此筛选器行并按 Delete 键。  
  
## <a name="see-also"></a>另请参阅  
 [监视复制](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
