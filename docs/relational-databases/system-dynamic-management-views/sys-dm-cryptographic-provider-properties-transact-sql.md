---
title: sys. dm_cryptographic_provider_properties （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be99b97a8dc873866a7437f2e11f7e5d3588fec8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717455"
---
# <a name="sysdm_cryptographic_provider_properties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  返回有关注册的加密提供程序的信息。  
  
 
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|加密提供程序的标识号。|  
|guid|**uniqueidentifier**|唯一的提供程序 GUID。|  
|provider_version|**nvarchar(256)**|格式为 "*aa.bb.cccc.dd*" 的提供程序版本。|  
|sqlcrypt_version|**nvarchar(256)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]格式为 "*aa.bb.cccc.dd*" 的加密 API 的主要版本。|  
|friendly_name|**nvarchar(2048)**|提供程序提供的名称。|  
|authentication_type|**nvarchar(256)**|WINDOWS、BASIC 或其他。|  
|symmetric_key_support|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_export|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_import|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_persistance|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|asymmetric_key_support|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|asymmetric_key_export|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_import|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_persistance|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
  
## <a name="remarks"></a>备注  
 sys.dm_cryptographic_provider_properties 视图是公开显示的。  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;安全目录视图](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [可扩展的密钥管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [&#40;Transact-sql&#41;创建加密提供程序](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [与安全性相关的动态管理视图和函数 (Transact-SQL)](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
