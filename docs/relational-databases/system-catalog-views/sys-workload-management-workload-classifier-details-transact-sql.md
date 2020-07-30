---
title: sys. workload_management_workload_classifier_details （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 3fbbc52f13bebbb46a3afc7d2dd450765d28a21a
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87393966"
---
# <a name="sysworkload_management_workload_classifier_details-transact-sql"></a>sys. workload_management_workload_classifier_details （Transact-sql）

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  返回每个分类器的详细信息。  
  
|列名|数据类型|说明|范围|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|分类器的 ID。  不可为 null。|
|classifier_type|**sysname**|可加入[workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md)。|`membername`</br>`wlm_label`</br>`wlm_context`</br>`start_time`</br>`end_time`|
|classifier_value|**sysname**|分类器的值。 不可为 null。||

## <a name="permissions"></a>权限

需要 VIEW SERVER STATE 权限。

## <a name="next-steps"></a>后续步骤
  
有关 SQL 数据仓库和并行数据仓库的所有目录视图的列表，请参阅[Sql 数据仓库和并行数据仓库目录视图](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)。 若要创建工作负荷分类器，请参阅[创建工作负荷分类器](../../t-sql/statements/create-workload-classifier-transact-sql.md)。 有关工作负荷分类的详细信息，请参阅 SQL 数据仓库[工作负荷分类](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)和[工作负荷重要性](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
