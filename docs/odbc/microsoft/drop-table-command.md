---
description: DROP TABLE 命令
title: DROP TABLE 命令 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f383740584ca524c732172ee363f7ffb393c30c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412563"
---
# <a name="drop-table-command"></a>DROP TABLE 命令
从使用数据源指定的数据库中删除表，并将其从磁盘中删除。  
  
 Visual FoxPro ODBC 驱动程序支持此命令的本机 Visual FoxPro 语言语法。 有关特定于驱动程序的信息，请参阅 "备注"。  
  
## <a name="syntax"></a>语法  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>设置  
 *TableName*  
 指定要从通过数据源指定的数据库中删除的表并从磁盘中删除。  
  
 *FileName*  
 指定要从磁盘中删除的可用表。  
  
 ?  
 显示 "删除" 对话框，您可以从该对话框中选择要从使用数据源指定的数据库中删除的表，还可以从磁盘中删除。  
  
## <a name="remarks"></a>备注  
 发出 DROP TABLE 时，还将删除与该表关联的所有主索引、默认值和验证规则。 如果表中有与要删除的表关联的规则或关系，DROP TABLE 还会影响使用数据源指定的数据库中的其他表。 当从数据库中删除表时，规则和关系不再有效。  
  
## <a name="driver-remarks"></a>驱动程序备注  
 当应用程序将 ODBC SQL 语句删除表发送到数据源时，Visual FoxPro ODBC 驱动程序将使用下表中所示的语法将命令转换为 Visual FoxProDROP TABLE 命令。  
  
|ODBC 语法|数据源|Visual FoxPro 语法|  
|-----------------|-----------------|--------------------------|  
|删除表 *基-表名*|数据库 ( dbc 文件) |删除表 *TableName* 删除|  
||可用表目录 ( .dbf 文件) |ERASE *dbfName*<br /><br /> ERASE *cdxName*<br /><br /> ERASE *fptName*|
