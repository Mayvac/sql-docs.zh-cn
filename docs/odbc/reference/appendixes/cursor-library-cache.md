---
description: 游标库缓存
title: 游标库缓存 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a558ab120d2812e88a4dbbdd8392c997ce423c8a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456646"
---
# <a name="cursor-library-cache"></a>游标库缓存
> [!IMPORTANT]  
>  此功能将在 Windows 的将来版本中删除。 避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 对于结果集中的每个数据行，游标库将缓存每个绑定列的数据、每个绑定列中的数据长度以及行的状态。 游标库使用缓存中的值来通过 **SQLFetch** 和 **SQLFetchScroll** 返回，并为定位操作构造搜索语句。 有关详细信息，请参阅 [构造搜索语句](../../../odbc/reference/appendixes/constructing-searched-statements.md)。  
  
 本部分包含以下主题。  
  
-   [列数据](../../../odbc/reference/appendixes/column-data.md)  
  
-   [列数据的长度](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [行状态](../../../odbc/reference/appendixes/row-status.md)  
  
-   [缓存的位置](../../../odbc/reference/appendixes/location-of-cache.md)
