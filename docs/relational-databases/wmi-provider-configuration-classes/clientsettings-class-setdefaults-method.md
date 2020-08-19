---
description: ClientSettings 类 - SetDefaults 方法
title: 'SetDefaults 方法 (ClientSettings) '
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (ClientSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 862e03c447e6c7e0c80318b89bcd9cbf5ecd92aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460140"
---
# <a name="clientsettings-class---setdefaults-method"></a>ClientSettings 类 - SetDefaults 方法
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  设置客户端实例的所有默认值， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并提供覆盖现有数据的选项。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>组成部分  
 对象  
 一个**ClientSettings**表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端实例的 ClientSettings 对象。  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|*OverwriteAll*|一个指定是否覆盖 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端实例的现有值的布尔值。 若要覆盖现有数据，**则为 true** ;如果不覆盖现有数据，则**为 false** 。|  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 一个 **uint32** 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。  
  
## <a name="remarks"></a>备注  
  
