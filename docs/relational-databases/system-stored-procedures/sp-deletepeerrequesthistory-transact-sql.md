---
description: sp_deletepeerrequesthistory (Transact-SQL)
title: sp_deletepeerrequesthistory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletepeerrequesthistory
- sp_deletepeerrequesthistory_TSQL
helpviewer_keywords:
- sp_deletepeerrequesthistory
ms.assetid: 63a4ec6e-ce79-4bf1-9d37-5ac88f8d6beb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 11773aa1e2a03ccc9b729c902a99cda10088c718
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474340"
---
# <a name="sp_deletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  删除与发布状态请求相关的历史记录，其中包括请求历史记录 ([MSpeer_request &#40;transact-sql&#41;](../../relational-databases/system-tables/mspeer-request-transact-sql.md)) 以及响应历史记录 (MSpeer_response &#40;[transact-sql&#41;](../../relational-databases/system-tables/mspeer-response-transact-sql.md)) 。此存储过程在参与对等复制拓扑的发布服务器上对发布数据库执行。 有关详细信息，请参阅 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>参数  
`[ @publication = ] 'publication'` 发出状态请求的发布的名称。 *发布* 为 **sysname**，无默认值。  
  
`[ @request_id = ] request_id` 指定单个状态请求，以便删除对此请求的所有响应。 *request_id* 的值为 **int**，默认值为 NULL。  
  
`[ @cutoff_date = ] cutoff_date` 指定截止日期，在该日期之前删除所有以前的响应记录。 *cutoff_date* 为 **datetime**，默认值为 NULL。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** (成功) 或 **1** (失败)   
  
## <a name="remarks"></a>备注  
 **sp_deletepeerrequesthistory** 用于对等事务复制拓扑。 有关详细信息，请参阅 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)。  
  
 执行 **sp_deletepeerrequesthistory**时，必须指定 *request_id* 或 *cutoff_date* 。  
  
## <a name="permissions"></a>权限  
 只有 **sysadmin** 固定服务器角色的成员或 **db_owner** 固定数据库角色的成员才能执行 **sp_deletepeerrequesthistory**。  
  
## <a name="see-also"></a>另请参阅  
 [sp_helppeerrequests &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [sp_requestpeerresponse &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  
