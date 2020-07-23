---
title: 以编程方式枚举可用的包 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically enumerate packages [SSIS]
- existence testing [Integration Services]
- enumerating packages [Integration Services]
ms.assetid: 254ec7ee-d3ff-4361-8995-46e9b9c4dc95
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86e30dcb8043d18d82e742666c8c36043f86c5a2
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920123"
---
# <a name="enumerating-available-packages-programmatically"></a>以编程方式枚举可用的包

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  <a name="top"></a> 以编程方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时，可能希望确定单个包或文件夹是否存在，或枚举可用于加载和执行的已保存的包。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空间的 <xref:Microsoft.SqlServer.Dts.Runtime> 类提供了多种满足这些要求的方法。    
    
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a>确定包或文件夹是否存在    
 若要以编程方式确定已保存的包是否存在，请先调用以下方法之一，然后再尝试加载和运行：    
    
|存储位置|调用的方法|    
|----------------------|--------------------|    
|SSIS 包存储区|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 若要以编程方式确定文件夹是否存在，请先调用以下方法之一，然后再尝试列出在其中存储的包：    
    
|存储位置|调用的方法|    
|----------------------|--------------------|    
|SSIS 包存储区|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [返回页首](#top)    
    
##  <a name="enumerating-available-packages"></a><a name="listing"></a> 枚举可用的包    
 若要以编程方式获取已保存的包的列表，请调用以下方法之一：    
    
|存储位置|调用的方法|    
|----------------------|--------------------|    
|SSIS 包存储区|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A>|    
    
 下面的示例是控制台应用程序，演示了这些方法的用法。    
    
###  <a name="example-ssis-package-store"></a><a name="listing_store"></a> 示例（SSIS 包存储区）    
 使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> 方法列出存储在 SSIS 包存储区中的包。 SSIS 包存储区管理的默认存储位置为“文件系统”和 MSDB。 可以在这些位置创建其他逻辑文件夹。    
    
```vb    
Imports Microsoft.SqlServer.Dts.Runtime    
    
Module Module1    
    
  Sub Main()    
    
    Dim sqlFolder As String    
    Dim sqlServer As String    
    
    Dim ssisApplication As Application    
    Dim sqlPackages As PackageInfos    
    Dim sqlPackage As PackageInfo    
    
    sqlServer = "."    
    
    ssisApplication = New Application()    
    
    ' Get packages stored in MSDB.    
    sqlFolder = "MSDB"    
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)    
    If sqlPackages.Count > 0 Then    
      Console.WriteLine("Packages stored in MSDB:")    
      For Each sqlPackage In sqlPackages    
        Console.WriteLine(sqlPackage.Name)    
      Next    
      Console.WriteLine()    
    End If    
    
    ' Get packages stored in the File System.    
    sqlFolder = "File System"    
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)    
    If sqlPackages.Count > 0 Then    
      Console.WriteLine("Packages stored in the File System:")    
      For Each sqlPackage In sqlPackages    
        Console.WriteLine(sqlPackage.Name)    
      Next    
    End If    
    
    Console.Read()    
    
  End Sub    
    
End Module    
```    
    
```csharp    
using System;    
using Microsoft.SqlServer.Dts.Runtime;    
    
namespace EnumeratePackagesSSIS_CS    
{    
  class Program    
  {    
    static void Main(string[] args)    
    {    
    
      string sqlFolder;    
      string sqlServer;    
    
      Application ssisApplication;    
      PackageInfos sqlPackages;    
    
      sqlServer = ".";    
    
      ssisApplication = new Application();    
    
      // Get packages stored in MSDB.    
      sqlFolder = "MSDB";    
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);    
      if (sqlPackages.Count > 0)    
      {    
        Console.WriteLine("Packages stored in MSDB:");    
        foreach (PackageInfo sqlPackage in sqlPackages)    
        {    
          Console.WriteLine(sqlPackage.Name);    
        }    
        Console.WriteLine();    
      }    
    
      // Get packages stored in the File System.    
      sqlFolder = "File System";    
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);    
      if (sqlPackages.Count > 0)    
      {    
        Console.WriteLine("Packages stored in the File System:");    
        foreach (PackageInfo sqlPackage in sqlPackages)    
        {    
          Console.WriteLine(sqlPackage.Name);    
        }    
      }    
    
      Console.Read();    
    
    }    
    
  }    
    
}    
```    
    
 [返回页首](#top)    
    
###  <a name="example-sql-server"></a><a name="listing_sql"></a> 示例 (SQL Server)    
 使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> 方法列出在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 实例中存储的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包。    
    
```vb    
Imports Microsoft.SqlServer.Dts.Runtime    
    
Module Module1    
    
  Sub Main()    
    
    Dim sqlFolder As String    
    Dim sqlServer As String    
    Dim sqlUser As String    
    Dim sqlPassword As String    
    
    Dim ssisApplication As Application    
    Dim sqlPackages As PackageInfos    
    Dim sqlPackage As PackageInfo    
    
    sqlFolder = String.Empty    
    sqlServer = "(local)"    
    sqlUser = String.Empty    
    sqlPassword = String.Empty    
    
    ssisApplication = New Application()    
    
    sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword)    
    
    For Each sqlPackage In sqlPackages    
      Console.WriteLine(sqlPackage.Name)    
    Next    
    
    Console.Read()    
    
  End Sub    
    
End Module    
```    
    
```csharp    
using System;    
using Microsoft.SqlServer.Dts.Runtime;    
    
namespace EnumeratePackagesSql_CS    
{    
  class Program    
  {    
    static void Main(string[] args)    
    {    
    
      string sqlFolder;    
      string sqlServer;    
      string sqlUser;    
      string sqlPassword;    
    
      Application ssisApplication;    
      PackageInfos sqlPackages;    
    
      sqlFolder = String.Empty;    
      sqlServer = "(local)";    
      sqlUser = String.Empty;    
      sqlPassword = String.Empty;    
    
      ssisApplication = new Application();    
    
      sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword);    
    
      foreach (PackageInfo sqlPackage in sqlPackages)    
      {    
        Console.WriteLine(sqlPackage.Name);    
      }    
    
      Console.Read();    
    
    }    
  }    
}    
```    
    
 [返回页首](#top)    
   
## <a name="see-also"></a>另请参阅    
 [包管理（SSIS 服务）](../../integration-services/service/package-management-ssis-service.md)    
    
  
