---
description: SQLSpecialColumns（桌面数据库驱动程序）
title: SQLSpecialColumns (桌面数据库驱动程序) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3f023c4f82c5a2f9af7af2e34cc697ffdb34206
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421611"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns（桌面数据库驱动程序）
如果 *fColType*中的 SQL_BEST_ROWID 标志存在) ，则将返回唯一索引 (。 SQL_ROWVER 标志将不返回结果集。  
  
 所有行 Id 都有一个 SQL_SCOPE_CURROW 范围。  
  
 *SzTableQualifier*或*szTableName*参数不支持模式匹配。
