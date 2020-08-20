---
description: 默认驱动程序子项
title: 默认驱动程序子项 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d78cc54253d002c54510fdc47f46f10de9281b65
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494550"
---
# <a name="default-driver-subkey"></a>默认驱动程序子项
默认子项包含一个值，该值描述默认数据源使用的驱动程序。 下表显示了此值的格式。  
  
|名称|数据类型|数据|  
|----------|---------------|----------|  
|**驱动程序**|REG_SZ|*默认-驱动程序-说明*|  
  
 *默认驱动程序说明*名称与描述驱动程序的 ODBC 驱动程序子项下的值的名称相同。  
  
 例如，如果默认数据源使用 SQL Server 驱动程序，则默认子项下的值可能是：  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  默认子项中包含的默认驱动程序可以引用默认的用户 DSN 或默认的系统 DSN。 如果默认的用户 DSN 和默认系统 DSN 都已创建，则默认驱动程序由最后创建的 DSN 确定，因此它可能不是先创建的 DSN 的有效条目。
