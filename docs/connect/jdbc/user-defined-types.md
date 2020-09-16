---
description: 用户定义类型
title: 用户定义的类型 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 04c7d143e24efbd21e977c1538820e1cb2289049
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487978"
---
# <a name="user-defined-types"></a>用户定义类型

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

用户定义类型 (UDT) 是在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中引入的，以允许开发人员通过在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中存储公共语言运行时 (CLR) 对象来扩展服务器的标量类型系统。 UDT 可以包含多个元素，也可以具有多种行为，不同于传统的由单个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据类型组成的别名数据类型。 以前 UDT 的最大大小限制为 8 KB。 在 [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] 中，已经新增了对大于 64 KB 的 UDT 的支持。 从 3.0 版开始，JDBC 驱动程序还支持在指定 UserDefined 格式时大于 64 KB 的 UDT。

对于小于或等于 8,000 字节的 UDT 在行为上没有变化，但支持更大的 UDT 并且将其大小报告为“无限制”。

## <a name="see-also"></a>另请参阅

[了解 JDBC 驱动程序数据类型](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
