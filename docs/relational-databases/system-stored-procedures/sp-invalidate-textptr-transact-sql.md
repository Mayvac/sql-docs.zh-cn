---
title: sp_invalidate_textptr （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_invalidate_textptr_TSQL
- sp_invalidate_textptr
dev_langs:
- TSQL
helpviewer_keywords:
- sp_invalidate_textptr
ms.assetid: dd9920e1-7064-4c05-93d8-9303103fa1d6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 269a49f76bd583c2233cf3720818590ca132c6a3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899407"
---
# <a name="sp_invalidate_textptr-transact-sql"></a>sp_invalidate_textptr (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  使事务中指定的行内文本指针或所有行内文本指针失效。 **sp_invalidate_textptr**只能用于行内文本指针。 这些指针来自启用了**text in row**选项的表。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_invalidate_textptr [ [ @TextPtrValue = ] textptr_value ]  
```  
  
## <a name="arguments"></a>参数  
`[ @TextPtrValue = ] textptr_value`要使其无效的行内文本指针。 *textptr_value*为**varbinary （** 16 **）**，默认值为 NULL。 如果为 NULL，则**sp_invalidate_textptr**使事务中的所有行内文本指针失效。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>备注  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许每个数据库中的每个事务最多拥有 1,024 个活动的有效行内文本指针；而跨多个数据库的事务可在每个数据库中拥有 1,024 个行内文本指针。 **sp_invalidate_textptr**可用于使行内文本指针无效，并因此可用于附加的行内文本指针。  
  
 有关 text in row 选项的详细信息，请参阅 sp_tableoption (Transact-SQL)  。  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。  
  
## <a name="see-also"></a>另请参阅  
 [数据库引擎存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [&#40;Transact-sql&#41;系统存储过程](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_tableoption &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)   
 [TEXTPTR &#40;Transact-sql&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [TEXTVALID (Transact-SQL)](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)  
  
  
