---
title: STInteriorRingN （geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a98567d42b701178f0996a82e563e5655a062dac
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762448"
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN（geometry 数据类型）
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

返回 Polygongeometry 实例的指定内环  。
  
## <a name="syntax"></a>语法  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>参数  
 *expression*  
 一个 int 表达式，其值介于 1 和 geometry 实例中的内环数之间   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geometry   
  
 CLR 返回类型：SqlGeometry   
  
 开放地理空间信息联盟 (OGC) 类型：LineString   
  
## <a name="remarks"></a>备注  
 如果 geometry 实例不是多边形，则此方法返回 NULL   。 如果表达式大于环数，则此方法还将引发 ArgumentOutOfRangeException  。 可以使用 `STNumInteriorRing``()` 返回环数。  
  
## <a name="examples"></a>示例  
 以下示例创建 `Polygon` 实例，并使用 `STInteriorRingN()` 以LineString 的形式返回多边形的内环  。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

