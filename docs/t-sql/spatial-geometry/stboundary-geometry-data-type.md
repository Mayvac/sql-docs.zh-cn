---
title: STBoundary（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 94862dc99312cb495aa8f9dceba4959c8f4fa706
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748767"
---
# <a name="stboundary-geometry-data-type"></a>STBoundary（geometry 数据类型）
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  返回 **geometry** 实例的边界。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STBoundary ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geometry   
  
 CLR 返回类型：SqlGeometry   
  
## <a name="remarks"></a>备注  
 当 LineString、CircularString 或 CompoundCurve 实例的端点相同时，`STBoundary()` 返回空的 GeometryCollection     。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>A. 对具有不同终结点的 LineString 实例使用 STBoundary()  
 下面的示例创建 `LineString``geometry` 实例。 `STBoundary()` 返回 `LineString` 的边界。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>B. 对具有相同终结点的 LineString 实例使用 STBoundary()  
 下面的示例创建一个具有相同终结点的有效 `LineString` 实例。 `STBoundary()` 将返回一个空的 `GeometryCollection`。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>C. 对 CurvePolygon 实例使用 STBoundary()  
 下面的示例对 `STBoundary()` 实例使用 `CurvePolygon`。 `STBoundary()` 将返回一个 `CircularString` 实例。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
