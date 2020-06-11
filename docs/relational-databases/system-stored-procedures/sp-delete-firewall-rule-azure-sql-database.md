---
title: sp_delete_firewall_rule
titleSuffix: Azure SQL Database
ms.date: 07/27/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_firewall_rule_TSQL
- sp_delete_firewall_rule
- sys.sp_delete_firewall_rule
- sys.sp_delete_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_firewall_rule procedure
ms.assetid: cf93eed1-ba97-4850-9fcc-b9c5a9317908
author: VanMSFT
ms.author: vanto
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f25cd3da648785ad25309c2c3943dbec7390c3d9
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627420"
---
# <a name="sp_delete_firewall_rule-azure-sql-database"></a>sp_delete_firewall_rule（Azure SQL 数据库）
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  从 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 服务器中删除服务器级的防火墙设置。 此存储过程只在 master 数据库中适用于服务器级主体登录名。  

  
## <a name="syntax"></a>语法  
  
```  
sp_delete_firewall_rule [@name =] 'name' 
[ ; ] 
```  
  
## <a name="arguments"></a>参数  
 存储过程的参数为：  
  
 [ @name =] "*name*"  
 将删除的服务器级防火墙设置的名称。 *name*为**nvarchar （128）** ，无默认值。  
  
## <a name="remarks"></a>注解  
 在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中，对连接和服务器级别的防火墙规则进行身份验证时所需的登录数据会暂时缓存在每个数据库中。 此缓存定期刷新。 若要强制刷新身份验证缓存并确保数据库具有最新版本的登录名表，请执行 [DBCC FLUSHAUTHCACHE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md)。  
  
## <a name="permissions"></a>权限  
 只有由设置过程创建的服务器级主体登录名才可以删除服务器级防火墙规则。 用户必须连接到 master 数据库才能执行 sp_delete_firewall_rule。  
  
## <a name="example"></a>示例  
 以下示例将删除名为“Example setting 1”的服务器级防火墙设置。 在虚拟 master 数据库中执行语句。  
  
```   
EXEC sp_delete_firewall_rule N'Example setting 1';   
```  
  
## <a name="see-also"></a>另请参阅  
 [Azure SQL Database 防火墙](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [如何：配置防火墙设置（Azure SQL Database）](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [Azure SQL Database &#40;sp_set_firewall_rule&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [firewall_rules &#40;Azure SQL 数据库&#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)  
  
  


