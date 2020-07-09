---
title: STCrosses（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCrosses (geometry Data Type)
- STCrosses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STCrosses (geometry Data Type)
ms.assetid: 3e3fc065-555a-4bee-8b71-e92f3dc62a4f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b78da062fb43d04afb53b8e4743ad222d873fe32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748716"
---
# <a name="stcrosses-geometry-data-type"></a>STCrosses（geometry 数据类型）
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

如果一个 **geometry** 实例与另一个 **geometry** 实例相交，则返回 1。 否则，返回 0。
  
## <a name="syntax"></a>语法  
  
```  
  
.STCrosses ( other_geometry )  
```  
  
## <a name="arguments"></a>参数  
 *other_geometry*  
 将与调用 `STCrosses()` 的实例进行比较的另一个 geometry 实例。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：bit   
  
 CLR 返回类型：SqlBoolean   
  
## <a name="remarks"></a>备注  
 如果同时满足以下两个条件，则表示两个 **geometry** 实例相交：  
  
-   两个 **geometry** 实例的交集生成一个维度小于源 **geometry** 实例最大维度的几何图形。  
  
-   交集发生在两个源 **geometry** 实例的内部。  
  
 如果 geometry 实例的空间引用 ID (SRID) 不匹配，则此方法始终返回 null  。  
  
## <a name="examples"></a>示例  
 下面的示例使用 `STCrosses()` 来测试两个 `geometry` 实例，以查看它们是否相交。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0)', 0);  
SET @h = geometry::STGeomFromText('LINESTRING(0 0, 2 2)', 0);  
SELECT @g.STCrosses(@h);  
```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

