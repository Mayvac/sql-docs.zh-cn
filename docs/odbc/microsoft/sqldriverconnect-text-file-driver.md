---
description: SQLDriverConnect（文本文件驱动程序）
title: SQLDriverConnect (文本文件驱动程序) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2eb5c35e9f6ae56caa3c6e4ca7473defe3b8bc0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421801"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect（文本文件驱动程序）
> [!NOTE]  
>  本主题提供特定于文本文件驱动程序的信息。 有关此函数的常规信息，请参阅 [ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)中的相应主题。  
  
 **SQLDriverConnect** 使你可以连接到驱动程序，而无需 (DSN) 创建数据源。  
  
 所有驱动程序的连接字符串支持以下关键字： **DSN**、 **DBQ**和 **FIL**。  
  
 下表显示连接到每个驱动程序所需的最小关键字，并提供用于 **SQLDriverConnect**的关键字/值对的示例。 有关 DRIVERID 值的完整列表，请参阅 [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)。  
  
> [!NOTE]  
>  如果没有为文本驱动程序指定 DBQ 或 DefaultDir，则驱动程序将连接到当前目录。  
  
|驱动程序|需要关键字|示例|  
|------------|-----------------------|--------------|  
|文本|驱动程序|Driver = {Microsoft Text Driver ( * .txt; \* 。csv) };DefaultDir = c：\temp|
