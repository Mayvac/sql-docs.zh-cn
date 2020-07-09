---
title: STRelate（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STRelate (geometry Data Type)
- STRelate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRelate (geometry Data Type)
ms.assetid: 9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 274b14dc7d4feaedfd4f32221312762eddedc005
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762177"
---
# <a name="strelate-geometry-data-type"></a>STRelate（geometry 数据类型）
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  如果一个 **geometry** 实例与另一个 **geometry** 实例相关（其关系由“维扩展 9 交集模型”(DE-9IM) 模式矩阵值定义），则返回 1；否则，返回 0。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STRelate ( other_geometry, intersection_pattern_matrix )  
```  
  
## <a name="arguments"></a>参数  
 *other_geometry*  
 将与调用 `STRelate()` 的实例进行比较的另一个 geometry 实例。  
  
 *intersection_pattern_matrix*  
 两个 **geometry** 实例间的 DE-9IM 模式矩阵设备的 **nchar(9)** 类型编码可接受值字符串。  
  
## <a name="remarks"></a>备注  
 如果 geometry 实例的空间引用 ID (SRID) 不匹配，则此方法始终返回 null  。 如果矩阵格式不正确，此方法将引发 **ArgumentException**。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：bit   
  
 CLR 返回类型：SqlBoolean   
  
## <a name="examples"></a>示例  
 以下示例在显式 DE-9IM 模式下使用 `STRelate()` 来测试两个 **geometry** 实例是否在空间上不相联。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(5 5)', 0);  
SELECT @g.STRelate(@h, 'FF*FF****');  
```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
