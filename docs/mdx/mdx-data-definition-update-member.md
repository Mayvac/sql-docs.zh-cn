---
description: MDX 数据定义 - UPDATE MEMBER
title: " (MDX) 更新成员语句 |Microsoft Docs"
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3b1333a8784ea5427dec3ed7223a3c7c1a09120d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387061"
---
# <a name="mdx-data-definition---update-member"></a>MDX 数据定义 - UPDATE MEMBER


  更新现有的计算成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>参数  
 *Cube_Name*  
 一个有效的字符串，用于指定包含该成员的多维数据集的名称。  
  
 *Member_Name*  
 指定现有成员名称的有效字符串。  
  
 *MDX_Expression*  
 代表该成员更新目标的有效的多维表达式 (MDX) 表达式。  
  
 *Property_Name*  
 指定计算成员属性名称的有效字符串。  
  
 *Property_Value*  
 指定计算成员属性值的有效标量表达式。  
  
## <a name="remarks"></a>备注  
 UPDATE MEMBER 语句在保留此成员相对于其他计算的优先的同时，更新现有计算成员。 因此，您不能使用 UPDATE MEMBER 语句来更改 SOLVEORDER。  
  
 UPDATE MEMBER 语句不能在多维数据集的 MDX 脚本中指定。  
  
 指定当前连接的多维数据集以外的多维数据集将导致错误。 因此，应使用 CURRENTCUBE 来代替多维数据集名称，以表示当前的多维数据集。  
  
 有关 OLE DB 定义的成员属性的详细信息，请参阅 OLE DB 文档。  
  
## <a name="standard-properties"></a>标准属性  
 每个成员都有一组默认属性。 下表列出了这些默认属性。  
  
|属性标识符|含义|  
|-------------------------|-------------|  
|FORMAT_STRING|一个 Office 样式格式字符串，客户端应用程序可使用该字符串显示单元值。|  
|VISIBLE|指示计算成员在架构行集中是否可见的值。 可以使用 [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) 函数将可见计算成员添加到集。 非零值表示计算成员可见。 此属性的默认值为 *Visible*。<br /><br /> 不可见的计算成员通常用作更复杂的计算成员过程的中间步骤。 这些计算成员也可以由其他类型的成员（如度量值）引用。|  
|NON_EMPTY_BEHAVIOR|解析空单元时，MDX 用来确定计算成员的行为的度量值或集。|  
|CAPTION|指定客户端应用程序用来显示成员的标题的字符串值。|  
|DISPLAY_FOLDER|指定显示文件夹的路径的字符串值，客户端应用程序将在此处显示成员。 文件夹级别的分隔符由客户端应用程序定义。 对于提供的工具和客户端 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，反斜杠 (\\) 为级别分隔符。 若要为已定义的成员提供多个显示文件夹，请使用分号 (; ) 来分隔文件夹。|  
|ASSOCIATED_MEASURE_GROUP|与此成员关联的度量值组的名称。|  
  
## <a name="see-also"></a>另请参阅  
 [DROP MEMBER 语句 &#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [CREATE MEMBER 语句 &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [Mdx 数据定义语句 &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
