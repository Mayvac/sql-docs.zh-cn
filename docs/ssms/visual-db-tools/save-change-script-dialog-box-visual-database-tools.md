---
title: “保存更改脚本”对话框
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 04e1ac34a1c16dd5b0936634938f9edb0d8328aa
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "86010669"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>“保存更改脚本”对话框 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
此对话框可显示您在上次保存表以后所做更改的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。 使用该对话框还可以将脚本保存到位于所选位置的文本文件中。  
  
当您在表设计器中对表进行的更改尚未保存时，则可访问此对话框。 在“表设计器”  菜单上，单击“生成更改脚本”  。  
  
> [!NOTE]  
> Visual Database Tools 提供的更改脚本没有包含错误处理功能。 这些脚本假设在工具打开后数据库对象没有发生更改，因此不会发生与更改相关的问题。 运行更改脚本之前，您应在脚本中包括适当的错误处理语句。  
  
## <a name="options"></a>选项  
**每次保存时自动生成更改脚本**  
如果选择此选项，则在每次保存对表的更改时都会显示“保存更改脚本”  对话框。  
  
**是**  
打开“保存”  对话框，在其中可选择保存文本文件的位置。  
  
**是**  
取消创建更改脚本。  
  
