---
title: Z（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Z (geography Data Type)
- Z_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z method
ms.assetid: 9abc79c5-43c9-4cc2-b37f-d2ecdec7c234
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 885a7adaa3d88dd8534abca1378d7b10c6dece25
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85701174"
---
# <a name="z-geography-data-type"></a>Z（geography 数据类型）
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  实例的 Z（标高）值。 标高值的语义是用户定义的。  
  
## <a name="syntax"></a>语法  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 类型：float   
  
 CLR 类型：SqlDouble   
  
## <a name="remarks"></a>备注  
 如果 geography 实例不是 point，则此属性的值为 Null；对于未设置此属性的任何 Point 实例，此属性的值也为 Null   。  
  
 此属性为只读。  
  
 Z 坐标未在库进行的任何计算中使用，因此不通过任何库计算传递。  
  
## <a name="examples"></a>示例  
 下面的示例创建一个带有 Z（标高）和 M（度量）值的 `Point` 实例，并使用 `Z` 获取该实例的 Z 值。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>另请参阅  
 [Geography 实例上的扩展方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M（geography 数据类型）](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [AsTextZM（geography 数据类型）](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
