---
title: STDimension（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDimension (geography Data Type)
- STDimension_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension method
ms.assetid: 4368b0f6-0678-4ade-87dc-b43d8b2e8d92
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 1a681baef72aaab151c3c65f2694778882bb56d6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85704200"
---
# <a name="stdimension-geography-data-type"></a>STDimension（geography 数据类型）
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  返回 **geography** 实例的最大维度。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：int   
  
 CLR 返回类型：SqlInt32   
  
## <a name="remarks"></a>备注  
 如果 **geography** 实例为空，则 STDimension() 返回 -1。  
  
## <a name="examples"></a>示例  
 以下示例使用 `STDimension()` 创建一个存放 `geography` 实例的表变量，并插入一个 `Point`、一个 `LineString` 和一个 `Polygon`。  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geography);  
  
INSERT INTO @temp values ('Point', geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326));  
INSERT INTO @temp values ('LineString', geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
INSERT INTO @temp values ('Polygon', geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 然后，该示例返回每个 `geography` 实例的维度。  
  
|name|dim|  
|----------|---------|  
|Point|0|  
|LineString|1|  
|Polygon|2|  
  
## <a name="see-also"></a>另请参阅  
 [地理实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
