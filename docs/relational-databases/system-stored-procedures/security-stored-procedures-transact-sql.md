---
title: 安全存储过程（Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system stored procedures [SQL Server], security
- stored procedures [SQL Server], security
- security [SQL Server], stored procedures
ms.assetid: 62b72907-7e95-4c97-9891-0c45d5b678ce
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dc231f8b31dfecbeafe59c4ed719d169e5ac95c4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731774"
---
# <a name="security-stored-procedures-transact-sql"></a>安全存储过程 (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]支持用于管理安全性的下列系统存储过程。 其中一些存储过程已不推荐使用，但为了支持向后兼容性而仍然继续提供。  不推荐使用的存储过程的主题将列出用于替换它们的存储过程。  

|||  
|-|-|  
|[sys. sp_add_trusted_assembly]( sys-sp-add-trusted-assembly-transact-sql.md) |[sp_addapprole](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md) （已弃用）|
|[sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)|[sp_addlinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)
|[sp_addlogin](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md) （已弃用） |[sp_addremotelogin](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md) （已弃用）
|[sp_addrole](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md) （已弃用） |[sp_addrolemember](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) （已弃用）
|[sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) （已弃用） |[sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md) （已弃用）
|[sp_adduser](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md) （已弃用） |[sp_approlepassword](../../relational-databases/system-stored-procedures/sp-approlepassword-transact-sql.md) （已弃用）
|[sp_audit_write](../../relational-databases/system-stored-procedures/sp-audit-write-transact-sql.md) |[sp_change_users_login](../../relational-databases/system-stored-procedures/sp-change-users-login-transact-sql.md) （已弃用）
|[sp_changedbowner](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md) （已弃用） 
|[sp_changeobjectowner](../../relational-databases/system-stored-procedures/sp-changeobjectowner-transact-sql.md) （已弃用）
|[sp_control_dbmasterkey_password](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md) |[sp_dbfixedrolepermission](../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md) （已弃用）
|[sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) （已弃用） |[sp_defaultlanguage](../../relational-databases/system-stored-procedures/sp-defaultlanguage-transact-sql.md) （已弃用）
|[sp_denylogin](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md) （已弃用） |[sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)
|[sp_dropalias](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md) （已弃用） |[sys. sp_drop_trusted_assembly]( sys-sp-drop-trusted-assembly-transact-sql.md) |
|[sp_dropapprole](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md) （已弃用） |[sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) |
|[sp_droplogin](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md) （已弃用） |[sp_dropremotelogin](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md) （已弃用） |
|[sp_droprole](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md) （已弃用） |[sp_droprolemember](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) （已弃用） |
|[sp_dropserver](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md) |[sp_dropsrvrolemember](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md) （已弃用） |
|[sp_dropuser](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md) （已弃用） |[sp_grantdbaccess](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md) （已弃用） |
|[sp_grantlogin](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md) （已弃用） |[sp_helpdbfixedrole](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md) |
|[sp_helplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-helplinkedsrvlogin-transact-sql.md) |[sp_helplogins](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md) |
|[sp_helpntgroup](../../relational-databases/system-stored-procedures/sp-helpntgroup-transact-sql.md) |[sp_helpremotelogin](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md) （已弃用） |
|[sp_helprole](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md) |[sp_helprolemember](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) |
|[sp_helprotect](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md) （已弃用） |[sp_helpsrvrole](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md) |
|[sp_helpsrvrolemember](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md) |[sp_helpuser](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md) （已弃用） |
|[sp_migrate_user_to_contained](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md)|[sp_MShasdbaccess](../../relational-databases/system-stored-procedures/sp-mshasdbaccess-transact-sql.md) |
|[sp_password](../../relational-databases/system-stored-procedures/sp-password-transact-sql.md) （已弃用）|[sp_refresh_parameter_encryption](../../relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) |
|[sp_remoteoption](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md) （已弃用）|[sp_revokedbaccess](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md) （已弃用） |
|[sp_revokelogin](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md) （已弃用）|[sp_setapprole](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md) |
|[sp_srvrolepermission](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md) （已弃用）|[sp_testlinkedserver](../../relational-databases/system-stored-procedures/sp-testlinkedserver-transact-sql.md) |
|[sp_unsetapprole](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md) |[sp_validatelogins](../../relational-databases/system-stored-procedures/sp-validatelogins-transact-sql.md) |
|[sp_xp_cmdshell_proxy_account](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md) | |

 
  
## <a name="see-also"></a>另请参阅  
 [&#40;Transact-sql&#41;系统存储过程](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [安全函数 (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
