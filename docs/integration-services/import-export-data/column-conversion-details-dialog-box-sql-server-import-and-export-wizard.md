---
description: “列转换详细信息”对话框（SQL Server 导入和导出向导）
title: “列转换详细信息”对话框（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18e512c1834a74be5c45ce81fd859eaebb375be5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484132"
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>“列转换详细信息”对话框（SQL Server 导入和导出向导）

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  如果双击“查看数据类型映射” **** 页上的单个列的行， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] “导入和导出向导”会显示“列转换详细信息” **** 对话框。 在此页上你可以查看有关单个列的详细转换信息。 信息包括以下各项：
-   源和目标列的数据类型。
-   向导将执行的数据类型转换（如果需要）。
-   向导用于确定所需的数据类型转换的数据类型映射文件。 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>“列转换详细信息”页的屏幕截图 
 下面的屏幕截图显示用户双击“查看数据类型映射” **** 页上的行后，向导的“列转换详细信息” **** 对话框。 若要进一步了解“查看数据类型映射” **** 页，请参阅 [查看数据类型映射](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)。
 
在此示例中，可查看以下操作。
-   源 SQL Server 表中的 `PersonID` 列为 `int` 类型。 向导通过引用数据类型映射文件 MSSQLToSSIS10.xml 将此类型映射到 SQL Server Integration Services (SSIS) `DT_I4` 数据类型，后者是一个四字节带符号整数。
-   目标 SQL Server 表中的 `PersonID` 列也为 `int` 类型。 向导将此类型映射到相同的 SSIS 数据类型。
-   向导得出的结论是“此列不需要转换”**。
 
  
 ![“导入和导出向导”的“列转换”页面](../../integration-services/import-export-data/media/column-conversion.png "“导入和导出向导”的“列转换”页面") 
  
## <a name="whats-next"></a>下一步操作  
 查看列转换详细信息并单击“确认” **** 后，“列转换详细信息” **** 对话框将返回到“查看数据类型映射” **** 页。 有关详细信息，请参阅 [查看数据类型映射](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md)。  

## <a name="see-also"></a>另请参阅
[SQL Server 导入和导出向导中的数据类型映射](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
