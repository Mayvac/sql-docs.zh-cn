---
description: 目录对象 (ADO MD)
title: 目录对象 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADO MD]
ms.assetid: 11f6f896-d69c-44a4-94cd-d54c93140e4a
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e62b4eedd835cff2d5bd99e054648339ffd9bc0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987298"
---
# <a name="catalog-object-ado-md"></a>目录对象 (ADO MD)
包含多维架构信息 (多维数据提供程序) 特定于多维数据访问接口 (MDP) 的多维数据集和基础维度、层次结构、级别和成员。  
  
## <a name="remarks"></a>注解  
 使用 **目录** 对象的集合和属性，可以执行以下操作：  
  
-   通过将 [ActiveConnection](./activeconnection-property-ado-md.md) 属性设置为标准 ADO [连接](../ado-api/connection-object-ado.md) 对象或有效的连接字符串，打开目录。  
  
-   标识具有[Name](./name-property-ado-md.md)属性的**编录**。  
  
-   使用 [CubeDefs](./cubedefs-collection-ado-md.md) 集合循环访问目录中的多维数据集。  
  
 本部分包含以下主题。  
  
-   [属性、方法和事件](./catalog-object-properties-methods-and-events-ado-md.md)  
  
## <a name="see-also"></a>另请参阅  
 [ (VB 的目录示例) ](./catalog-example-vb.md)   
 [ADO) 的连接对象 (](../ado-api/connection-object-ado.md)   
 [CubeDefs 集合 (ADO MD)](./cubedefs-collection-ado-md.md)