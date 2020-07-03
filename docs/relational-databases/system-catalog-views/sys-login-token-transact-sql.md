---
title: sys. login_token （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- login_token_TSQL
- sys.login_token_TSQL
- sys.login_token
- login_token
dev_langs:
- TSQL
helpviewer_keywords:
- sys.login_token catalog view
- logins [SQL Server], security tokens
- tokens [SQL Server]
ms.assetid: 86e06938-9d0a-44e5-99e2-55c8ef5f2f84
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d8b230ba7e9c243db61648f0257f606faa4e7f50
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899030"
---
# <a name="syslogin_token-transact-sql"></a>sys.login_token (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  为登录名标记中包含的每个服务器主体返回一行。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|principal_id|**int**|主体的 ID。 此值在服务器中是唯一的。|  
|**sid**|**varbinary （85）**|服务器主体的安全标识符。 如果这是 Windows 主体，则**sid** = windows sid。 如果登录名已映射到证书，则**sid** = 来自证书的 GUID。|  
|**name**|**nvarchar(128)**|主体的名称。 此值在服务器中是唯一的。|  
|**type**|**nvarchar(128)**|主体类型的说明。 所有类型都映射到**sid**。 值可以是下列任一值：<br /><br /> SQL LOGIN<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> SERVER ROLE<br /><br /> LOGIN MAPPED TO CERTIFICATE<br /><br /> LOGIN MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**使用情况**|**nvarchar(128)**|指示服务器主体参与 GRANT 或 DENY 权限的鉴定，或用作验证器。<br /><br /> 此值可以为下列值之一：<br /><br /> GRANT 或 DENY<br /><br /> 仅 DENY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>另请参阅  
 [sys. user_token &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md)   
 [sys. server_principals &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys. database_principals &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [主体（数据库引擎）](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
