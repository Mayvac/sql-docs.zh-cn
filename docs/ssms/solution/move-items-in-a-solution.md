---
title: 在解决方案中移动项
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 67456bfd826610aaf500735d4f055e00f0c58aa7
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000803"
---
# <a name="move-items-in-a-solution"></a>在解决方案中移动项
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 项目中的项目项为查询、连接和杂项文件。 在解决方案资源管理器中，可以在项目之间移动查询和杂项文件，但无法移动连接。  
  
### <a name="to-move-items-in-solution-explorer"></a>在解决方案资源管理器中移动项  
  
1.  在解决方案资源管理器中，选择要移动的项。  
  
2.  在“编辑”  菜单上，单击“剪切”  。  
  
3.  在解决方案资源管理器中，选择目标位置。  
  
4.  在“编辑”  菜单上，单击“粘贴”  。  
  
可以通过在解决方案资源管理器中拖动查询和杂项文件来移动项。 拖动可使您看到拖动操作的结果。 将查询从一个项目类型移动到另一个项目类型可能会导致查询在目标项目中被视为杂项文件。  
  
> [!NOTE]  
> 移动连接查询时不会移动与目标项目的连接。 查询移动到目标项目之后，将丢失其原有连接。  
  
## <a name="see-also"></a>另请参阅  
[解决方案资源管理器](../../ssms/solution/solution-explorer.md)  
[复制解决方案中的项](../../ssms/solution/copy-items-in-a-solution.md)  
  
