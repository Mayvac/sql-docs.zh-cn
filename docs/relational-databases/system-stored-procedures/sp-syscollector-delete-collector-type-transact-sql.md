---
title: sp_syscollector_delete_collector_type （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_delete_collector_type
- sp_syscollector_delete_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_delete_collector_type
ms.assetid: 3f32905e-0005-42cb-aef1-7bd04c51fbac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2c24011a274b362a6b8267b7559d2641a4f1c6aa
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892918"
---
# <a name="sp_syscollector_delete_collector_type-transact-sql"></a>sp_syscollector_delete_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  删除收集器类型的定义。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_syscollector_delete_collector_type [[ @collector_type_uid = ] 'collector_type_uid' ]  
          , [[ @name = ] 'name' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @collector_type_uid = ] 'collector_type_uid'`收集器类型的 GUID。 *collector_type_uid*是**uniqueidentifier** ，且*name*为 NULL 时必须具有值。  
  
`[ @name = ] 'name'`收集器类型的名称。 *名称*为**sysname** ，并且*collector_type_uid*为 NULL 时必须具有值。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>备注  
 *Collector_type_uid*或*name*必须具有值，两者都不能为 NULL。  
  
 如果存在这种收集类型的收集项，此过程将引发错误。  
  
## <a name="permissions"></a>权限  
 需要**dc_admin** （具有 execute 权限）的成员身份才能执行此过程。  
  
## <a name="example"></a>示例  
 此示例删除一般 T-SQL 查询收集器类型。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_delete_collector_type @collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419';  
```  
  
## <a name="see-also"></a>另请参阅  
 [&#40;Transact-sql&#41;系统存储过程](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [数据收集](../../relational-databases/data-collection/data-collection.md)  
  
  
