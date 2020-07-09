---
title: STIsValid（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid method (geography)
ms.assetid: 1bfe787f-ddf0-4fc7-af6a-570a58faab23
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 9b2eeeab17ad2f130886ad2f47ebcbe4ddc75715
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736080"
---
# <a name="stisvalid-geography-data-type"></a>STIsValid（geography 数据类型）
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  根据 **geography** 实例的开放地理空间信息联盟 (OGC) 类型，如果可确定该实例的格式正确并将其识别为有效地理对象，则返回 true。 如果 **geography** 实例格式不正确，则返回 false。 此方法是精确方法。  
  
 这种 geography 数据类型方法支持大于半球的 FullGlobe 实例或空间实例  。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：bit   
  
 CLR 返回类型：**SqlBoolean**  
  
## <a name="remarks"></a>备注  
 geography 实例的 OGC 类型可通过调用 [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md) 来确定。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 只生成有效的 **geography** 实例，但允许存储和检索无效的实例。 可使用 `MakeValid()` 方法检索表示无效实例的相同点集的有效实例。  
  
## <a name="examples"></a>示例  
 下面的示例创建一个空的 `geography` 实例并使用 `STIsValid()` 来测试该实例是否有效。  
  
```  
DECLARE @g geography = geography::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 4326);  
SELECT @g.STIsValid();  
DECLARE @g geography  
```  
  
## <a name="see-also"></a>另请参阅  
 [STGeometryType（geography 数据类型）](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)   
 [MakeValid（geography 数据类型）](../../t-sql/spatial-geography/makevalid-geography-data-type.md)   
 [地理实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
