---
title: dbo.sysproxylogin （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 67e119b52b2dcb741ce1c63b343970e3152ccee5
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890412"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  记录与各个 SQL Server 代理的代理帐户关联的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。 该表存储在**msdb**数据库中。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户的 ID。 此值对应于**sysproxies**表中的**proxy_id**列。|  
|**sid**|**varbinary （85）**|用于 SQL Server 登录名的 Microsoft Windows *security_identifier* 。|  
|principal_id|**int**|指定用户或组的 ID，此用户或组具有将代理帐户用于指定子系统步骤的权限。|  
|**flag**|**int**|登录类型：<br /><br /> **0** = Windows 用户或组，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定系统角色<br /><br /> **2**  = **msdb**数据库角色|  
  
## <a name="remarks"></a>备注  
 只有**sysadmin**固定服务器角色的成员才能访问此表。  
  
## <a name="see-also"></a>另请参阅  
 [&#40;Transact-sql 的dbo.sys代理&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
