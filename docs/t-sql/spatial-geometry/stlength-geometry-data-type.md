---
title: STLength（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STLength_TSQL
- STLength (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STLength (geometry Data Type)
ms.assetid: e34dc620-2a65-4248-b099-fff91830ab98
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 11c88132b55957a84dfc44a6cec2e6563bf23eb7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762368"
---
# <a name="stlength-geometry-data-type"></a>STLength（geometry 数据类型）
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

返回 **geometry** 实例中的元素的总长度。
  
## <a name="syntax"></a>语法  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：float   
  
 CLR 返回类型：SqlDouble   
  
## <a name="remarks"></a>备注  
 如果 **geometry** 实例是闭合的，则其长度按围绕该实例的总长度进行计算；任何多边形的长度均为其周长，点的长度为 0。 任何 **geometrycollection** 类型的长度均为它所包含的 **geometry** 实例的长度之和。  
  
 STLength() 对有效和无效的 LineString 均适用。 通常，LineString 会因可能由 GPS 跟踪不准确之类的异常引起的段重叠而无效。 STLength() 不会删除重叠或无效的段。 它将重叠和无效的段包括在其返回的长度值中。 MakeValid() 方法可以从 LineString 中删除重叠段。  
  
## <a name="examples"></a>示例  
 下面的示例创建 `LineString` 实例并使用 `STLength()` 确定该实例的长度。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

