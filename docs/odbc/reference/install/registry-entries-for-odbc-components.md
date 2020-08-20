---
description: ODBC 组件的注册表项
title: ODBC 组件的注册表项 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3364f2b38fdb0c41ae0493b545740b17ee712bf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491332"
---
# <a name="registry-entries-for-odbc-components"></a>ODBC 组件的注册表项
> [!NOTE]  
>  从 Windows XP 和 Windows Server 2003 开始，ODBC 包含在 Windows 操作系统中。 只应在早期版本的 Windows 上显式安装 ODBC。  
  
 安装程序 DLL 会在注册表中维护有关每个已安装 ODBC 组件的信息。 在运行 Microsoft Windows NT 和 Microsoft Windows 95/98 的计算机上，此信息存储在注册表中以下项下的子项中：  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbcinst.ini
 ```

 由于 Odbcinst.ini 是 HKEY_LOCAL_MACHINE 树的子项，因此该计算机的所有用户都可以使用有关 ODBC 组件的信息。  
  
 本部分包含以下主题。  
  
-   [ODBC 核心子项](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [ODBC 驱动程序子项](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [驱动程序规范子项](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [默认驱动程序子项](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [ODBC 转换器子项](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [转换器规范子项](../../../odbc/reference/install/translator-specification-subkeys.md)
