---
title: catalog.effective_object_permissions（SSISDB 数据库）| Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- catalog.effective_object_permissions views [Integration Services]
- effective_object_permissions view [Integration Services]
ms.assetid: e70c4ce9-79f5-44df-ac75-6c29b6e38776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8f47b58cbac71800715a5f2ec091b6ce026484e0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85673442"
---
# <a name="catalogeffective_object_permissions-ssisdb-database"></a>catalog.effective_object_permissions（SSISDB 数据库）

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  显示 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录中所有对象的当前主体的有效权限。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|安全对象的类型。 安全对象类型包括文件夹 (`1`）、项目 (`2`)、环境 (`3`） 和操作 (`4`)。|  
|object_id|**bigint**|对象的唯一标识符 (ID) 或主键。|  
|permission_type|**smallint**|权限的类型。|  
  
## <a name="remarks"></a>备注  
 此视图显示下表中所列的权限类型：  
  
|permission_type 值|权限名称|权限说明|适用对象类型|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|允许主体读取被视为对象一部分的信息（如属性）。 它不允许主体枚举或读取该对象中包含的其他对象的内容。|文件夹、项目、环境、操作|  
|`2`|MODIFY|允许主体修改被视为对象一部分的信息（如属性）。 它不允许主体修改该对象中包含的其他对象。|文件夹、项目、环境、操作|  
|`3`|在运行 CREATE 语句前执行|允许主体执行项目中的所有包。|Project|  
|`4`|MANAGE_PERMISSIONS|允许主体向对象分配权限。|文件夹、项目、环境、操作|  
|`100`|CREATE_OBJECTS|允许主体在文件夹中创建对象。|Folder|  
|`101`|READ_OBJECTS|允许主体读取文件夹中的所有对象。|Folder|  
|`102`|MODIFY_OBJECTS|允许主体修改文件夹中的所有对象。|Folder|  
|`103`|EXECUTE_OBJECTS|允许主体执行文件夹中所有项目的所有包。|Folder|  
|`104`|MANAGE_OBJECT_PERMISSIONS|允许主体管理文件夹中所有对象的权限。|Folder|  
  
 只评估调用方对其具有权限的对象。 权限基于以下各项进行计算：  
  
-   显式权限  
  
-   继承的权限  
  
-   角色中主体的成员身份  
  
-   组中主体的成员身份  
  
## <a name="permissions"></a>权限  
 用户只可查看其自己的权限以及他们作为成员的角色的权限。  
  
  
