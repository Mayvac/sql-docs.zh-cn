---
description: 手动提交模式
title: 手动提交模式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb576166242078707846e005b958143812fd5901
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499831"
---
# <a name="manual-commit-mode"></a>手动提交模式
*在手动提交模式下，* 应用程序必须通过调用 **SQLEndTran** 以提交或回滚事务来显式完成事务。 这是大多数关系数据库的正常事务模式。  
  
 ODBC 中的事务不必显式启动。 相反，只要应用程序开始在数据库上操作，就会隐式开始事务。 如果数据源需要显式事务启动，则每当应用程序执行需要事务的语句并且没有当前事务时，驱动程序都必须提供此方法。
