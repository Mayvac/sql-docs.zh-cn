---
title: syspolicy_policy_execution_history_details （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_details
- syspolicy_policy_execution_history_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history_details view
ms.assetid: 97ef6573-5e8b-4ba5-8ae0-7901e79a9683
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b761d0e056037c134a3be837be04cba9395d9273
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900037"
---
# <a name="syspolicy_policy_execution_history_details-transact-sql"></a>syspolicy_policy_execution_history_details (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  显示执行的条件表达式、表达式目标、每次执行的结果以及有关出现的任何错误的详细信息。 下表介绍了 syspolicy_execution_history_details 视图中的列。  
  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|detail_id|**bigint**|此记录的标识符。 每个记录表示尝试计算或强制执行策略中的一个条件表达式。 如果应用于多个目标，每个条件将具有每个目标的详细记录。|  
|history_id|**bigint**|历史记录事件的标识符。 每个历史记录事件表示尝试执行一次策略。 由于条件可能具有几个条件表达式和几个目标，因此，history_id 可能会创建几条详细记录。 使用 "history_id" 列将此视图联接到 " [syspolicy_policy_execution_history](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-transact-sql.md) " 视图。|  
|target_query_expression|**nvarchar(max)**|策略目标和 syspolicy_policy_execution_history 视图。|  
|execution_date|**datetime**|此详细记录的创建日期和时间。|  
|result|**bit**|此目标和条件表达式计算成功或失败：<br /><br /> 0（成功）或 1（失败）。|  
|result_detail|**nvarchar(max)**|结果消息。 仅当由方面提供时才可用。|  
|exception_message|**nvarchar(max)**|发生的异常所生成的消息。|  
|exception|**nvarchar(max)**|发生的异常的说明。|  
  
## <a name="remarks"></a>备注  
 在排除基于策略的管理的故障时，请查询 syspolicy_policy_execution_history_details 视图，以确定失败的目标和条件表达式组合、失败时间并查看相关错误。  
  
 下面的查询将 `syspolicy_policy_execution_history_details` 视图与 `syspolicy_policy_execution_history_details` 和 `syspolicy_policies` 视图合并在一起，以显示策略名称、条件名称以及有关失败的详细信息。  
  
```  
SELECT Pol.name AS Policy,   
Cond.name AS Condition,   
PolHistDet.target_query_expression,   
PolHistDet.execution_date,   
PolHistDet.result,   
PolHistDet.result_detail,   
PolHistDet.exception_message,   
PolHistDet.exception   
FROM msdb.dbo.syspolicy_policies AS Pol  
JOIN msdb.dbo.syspolicy_conditions AS Cond  
    ON Pol.condition_id = Cond.condition_id  
JOIN msdb.dbo.syspolicy_policy_execution_history AS PolHist  
    ON Pol.policy_id = PolHist.policy_id  
JOIN msdb.dbo.syspolicy_policy_execution_history_details AS PolHistDet  
    ON PolHist.history_id = PolHistDet.history_id  
WHERE PolHistDet.result = 0 ;  
```  
  
## <a name="permissions"></a>权限  
 要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。  
  
## <a name="see-also"></a>另请参阅  
 [使用基于策略的管理来管理服务器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [基于策略的管理视图 (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
