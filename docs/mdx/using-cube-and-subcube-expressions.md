---
description: 使用多维数据集表达式和子多维数据集表达式
title: 使用多维数据集表达式和子多维数据集表达式 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 37f23c75d8a947e52daf47ef9648ccbd1587b9a8
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192297"
---
# <a name="using-cube-and-subcube-expressions"></a>使用多维数据集表达式和子多维数据集表达式


  可以在多维表达式 (MDX) 语句中使用多维数据集表达式和子多维数据集表达式，定义、操作或检索多维数据集或子多维数据集中的数据。  
  
## <a name="cube-expressions"></a>多维数据集表达式  
 多维数据集表达式包含多维数据集标识符或 CURRENTCUBE 关键字，因此只能是简单表达式。 许多 MDX 语句使用 CURRENTCUBE 关键字标识当前多维数据集上下文，而不要求使用多维数据集标识符。  
  
 多维数据集标识符在 MDX 语句的 BNF 表示法说明中显示为 *Cube_Name* 。  
  
 多维数据集表达式可以出现在多个位置。 在 MDX SELECT 语句中，这些表达式指定要在其中检索数据的多维数据集。 在以下的示例查询中，表达式 [Adventure Works] 指的是该名称的多维数据集：  
  
 `SELECT [Measures].[Internet Sales Amount] ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 在 CREATE MEMBER 语句中，多维数据集表达式指定您正在创建的计算成员将要出现在哪个多维数据集上。 在以下示例中，该语句在 Adventure Works 多维数据集的 Measures 维度上创建计算度量值：  
  
 `CREATE MEMBER [Adventure Works].[Measures].[Test] AS 1`  
  
 由于要在其中创建计算成员的多维数据集必须与 MDX 脚本所属的多维数据集相同，因此，在 MDX 脚本内部使用 CREATE MEMBER 语句时，可以用 CURRENTCUBE 关键字替换多维数据集的名称，如以下示例所示：  
  
 `CREATE MEMBER CURRENTCUBE.[Measures].[Test] AS 1;`  
  
 由于多维数据集的名称不再进行硬编码，因此，通过执行此操作，将计算成员的定义从一个多维数据集复制并粘贴到另一个多维数据集更为容易。  
  
## <a name="subcube-expressions"></a>子多维数据集表达式  
 子多维数据集表达式可以包含子多维数据集标识符或返回子多维数据集的 MDX 语句。 如果子多维数据集表达式包含子多维数据集标识符，它将是一个简单表达式。 如果它包含返回子多维数据集的 MDX 语句，则它是一个复杂语句。 例如，MDX SELECT 语句将返回子多维数据集，并且可在允许使用子多维数据集表达式的地方使用，如以下示例所示：  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Date].[Calendar Year].MEMBERS ON ROWS`  
  
 `FROM`  
  
 `(SELECT [Measures].[Internet Sales Amount] ON COLUMNS,`  
  
 `[Date].[Calendar Year].&[2004] ON ROWS`  
  
 `FROM [Adventure Works])`  
  
 FROM 子句中 SELECT 语句的此用法又称为嵌套 select。  
  
 遇到子多维数据集表达式的另一种常见应用场景是在 MDX 脚本中进行作用域分配。 在以下示例中，SCOPE 语句用于限制对包含 [Measures].[Internet Sales Amount] 的子多维数据集的分配：  
  
 `SCOPE([Measures].[Internet Sales Amount]);`  
  
 `This=1;`  
  
 `END SCOPE;`  
  
 子多维数据集标识符显示为 *Subcube_Name*。 在 MDX 语句的 BNF 表示法说明中。  
  
## <a name="see-also"></a>另请参阅  
 [基本 MDX 查询 &#40;MDX&#41;](/analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query)   
 [在 MDX &#40;MDX 中生成子多维数据&#41;](/analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx)   
 [&#40;MDX 创建子多维数据集语句&#41;](../mdx/mdx-data-definition-create-subcube.md)   
 [MDX&#41;&#40;表达式 ](../mdx/expressions-mdx.md)   
 [SCOPE 语句 (MDX)](../mdx/mdx-scripting-scope.md)  
  
