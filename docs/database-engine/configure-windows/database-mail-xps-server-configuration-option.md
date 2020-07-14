---
title: Database Mail XPs 服务器配置选项 | Microsoft Docs
description: 了解“DatabaseMail XPs”选项。 查看启用此选项的不同方式，以便可在 SQL Server 中使用数据库邮件。
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0d495017b9bf2a5f58a5a880f1ce9696976ebd50
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772571"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs 服务器配置选项

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

使用 **DatabaseMail XPs** 选项可以在此服务器上启用数据库邮件。 可能的值包括：  
  
- `0`：数据库邮件不可用（默认）。  
  
- `1`：数据库邮件可用。  
  
 该设置立即生效，无需停止并重新启动服务器。  
  
 启用数据库邮件后，必须配置一个数据库邮件主机数据库，才能使用 Database Mail。  
  
 使用“数据库邮件配置向导”配置数据库邮件可以启用 `msdb` 数据库中的数据库邮件扩展存储过程。 如果使用的是“数据库邮件配置向导”，则无需使用下面的 `sp_configure` 示例。  
  
 将“Database Mail XPs”选项设置为 `0` 可以防止启动数据库邮件。 如果该选项设置为 `0` 时数据库邮件正在运行，则它将继续运行并发送邮件，直到数据库邮件空闲时间达到 `DatabaseMailExeMinimumLifeTime` 选项中配置的时间。  
  
## <a name="examples"></a>示例
 以下示例启用了 Database Mail 扩展存储过程。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  

如果数据库邮件扩展存储过程尚未启用，请使用以下示例。

```sql
IF EXISTS (
    SELECT 1 FROM sys.configurations 
    WHERE NAME = 'Database Mail XPs' AND VALUE = 0)
BEGIN
  PRINT 'Enabling Database Mail XPs'
  EXEC sp_configure 'show advanced options', 1;  
  RECONFIGURE
  EXEC sp_configure 'Database Mail XPs', 1;  
  RECONFIGURE  
END
```

## <a name="see-also"></a>另请参阅
[数据库邮件](../../relational-databases/database-mail/database-mail.md)  
