---
title: 导航 SQL Server PowerShell 路径 | Microsoft Docs
description: 了解如何使用 PowerShell cmdlet 导航用于表示 PowerShell 提供程序支持的对象层次结构的路径结构。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: sql-server-powershell
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c823a1ff344fb453229330a0657d0604432397c0
ms.sourcegitcommit: a9f16d7819ed0e2b7ad8f4a7d4d2397437b2bbb2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714235"
---
# <a name="navigate-sql-server-powershell-paths"></a>导航 SQL ServerPowerShell 路径
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell 提供程序在与文件路径相似的结构中公开 SQL Server 实例中的对象集。 您可以使用 Windows PowerShell cmdlet 导航提供程序路径，并且创建自定义驱动器以便缩短需键入的路径。  

> [!NOTE]
> SQL Server PowerShell 模块有两种；SqlServer 和 SQLPS 。 虽然 SQL Server 安装附带了 SQLPS 模块（用于向后兼容），但该模块不再更新。 最新的 PowerShell 模块是 SqlServer 模块。 SqlServer 模块不仅包含 SQLPS 更新版本的 cmdlet，并且还包含新的 cmdlet 以支持最新的 SQL 功能 。  
> 虽然 SQL Server Management Studio (SSMS) 随附了以前版本的 SqlServer 模块，但仅限 16.x 版本的 SSMS。 要在 SSMS 17.0 和更高版本中使用 PowerShell，则必须从 PowerShell 库安装 SqlServer 模块。
> 要安装 SqlServer 模块，请参阅[安装 SQL Server PowerShell](download-sql-server-ps-module.md)。
  
Windows PowerShell 实现 cmdlet 以便导航表示 PowerShell 提供程序支持的对象层次结构的路径结构。 在您导航到该路径中的节点时，可以使用其他 cmdlet 以便针对当前对象执行基本操作。 由于 cmdlet 会经常用到，因此它们具有简短的规范别名。 还有一组将 cmdlet 映射到类似命令提示符命令的别名，以及另一组用于 UNIX shell 命令的别名。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序实现了提供程序 cmdlet 的一部分，如下表中所示：  
  
|cmdlet|规范别名|cmd 别名|UNIX shell 别名|说明|  
|------------|---------------------|---------------|----------------------|-----------------|  
|**Get-Location**|**gl**|**pwd**|**pwd**|获取当前节点。|  
|**Set-Location**|**sl**|**cd、chdir**|**cd、chdir**|更改当前节点。|  
|**Get-ChildItem**|**gci**|**dir**|**ls**|列出存储在当前节点中的对象。|  
|**Get-Item**|**gi**|||返回当前项的属性。|  
|**Rename-Item**|**rni**|**rn**|**ren**|重命名对象。|  
|**Remove-Item**|**ri**|**del、rd**|**rm、rmdir**|删除对象。|  
  
> [!IMPORTANT]  
>  某些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 标识符（对象名称）包含 Windows PowerShell 不支持在路径名称中使用的字符。 有关如何使用包含这些字符的名称的详细信息，请参阅 [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md)。  
  
### <a name="sql-server-information-returned-by-get-childitem"></a>Get-ChildItem 返回的 SQL Server 信息  
 由 **Get-ChildItem** （或其 **dir** 和 **ls** 别名）返回的信息取决于你在 SQLSERVER: 路径中的位置。  
  
|路径位置|Get-ChildItem 结果|  
|-------------------|----------------------------|  
|SQLSERVER:\SQL|返回本地计算机的名称。 如果在连接到其他计算机上的 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例时使用的是 SMO 或 WMI，则还将列出这些计算机。|  
|SQLSERVER:\SQL\\*ComputerName*|计算机上 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例的列表。|  
|SQLSERVER:\SQL\\*ComputerName*\\*InstanceName*|实例中顶层对象类型（如 Endpoints、Certificates 和 Databases）的列表。|  
|对象类节点，如 Databases|该类型的对象列表，如数据库列表：master、model、AdventureWorks20008R2。|  
|对象名称节点，如 AdventureWorks2012|包含在该对象中的对象类型的列表。 例如，数据库将列出表和视图之类的对象类型。|  
  
 默认情况下， **Get-ChildItem** 不会列出任何系统对象。 使用 *Force* 参数可查看系统对象，例如 **sys** 架构中的对象。  
  
### <a name="custom-drives"></a>自定义驱动器  
 Windows PowerShell 允许用户定义虚拟驱动器，这些驱动器称为 PowerShell 驱动器。 这些驱动器可映射路径语句的起始节点。 使用它们的目的通常是为了缩短经常键入的路径。 SQLSERVER：路径可能会很长，会在 Windows PowerShell 窗口中占据一定的空间，而且需要键入大量内容。 如果您打算针对特定的路径节点执行大量工作，则可以定义一个映射到该节点的自定义 Windows PowerShell 驱动器。  
  
## <a name="use-powershell-cmdlet-aliases"></a>使用 PowerShell Cmdlet 别名  
 **使用 cmdlet 别名**  
  
-   代替键入整个 cmdlet 名称，键入一个较短的别名，或者映射到熟悉的注释提示命令的别名。  
  
### <a name="alias-example-powershell"></a>别名示例 (PowerShell)  
 例如，可以使用下面的其中一组 cmdlet 或别名，导航到 SQLSERVER:\SQL 文件夹并请求该文件夹的子项列表，从而检索可供使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的列表：  
  
```  
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a>使用 Get-ChildItem  
 **通过使用 Get-Childitem 返回信息**  
  
1.  导航到要获取其子级的列表的节点  
  
2.  运行 Get-Childitem 以便获取该列表。  
  
### <a name="get-childitem-example-powershell"></a>Get-ChildItem 示例 (PowerShell)  
 这些示例阐释 Get-Childitem 为 SQL Server 提供程序路径中的不同节点返回的信息。  
  
```  
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a>创建自定义驱动器  
 **创建和使用自定义驱动器**  
  
1.  使用 **New-PSDrive** 可以定义自定义驱动器。 使用 **Root** 参数可以指定自定义驱动器名称表示的路径。  
  
2.  在 **Set-Location**之类的路径导航 cmdlet 中引用自定义驱动器名称。  
  
### <a name="custom-drive-example-powershell"></a>自定义驱动器示例 (PowerShell)  
 此示例创建一个名为 AWDB 的虚拟驱动器，该驱动器映射到 AdventureWorks2012 示例数据库的已部署副本的节点。 然后，使用该虚拟驱动器导航到数据库中的表。  
  
```  
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server PowerShell 提供程序](sql-server-powershell-provider.md)   
 [使用 SQL ServerPowerShell 路径](work-with-sql-server-powershell-paths.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
