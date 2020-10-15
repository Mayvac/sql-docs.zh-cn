---
title: 报表查看器控件入门
description: 报表查看器控件可用来将 Reporting Services RDL 报表集成到 WebForms 和 WinForms 应用。
ms.custom: seo-lt-2019
ms.date: 09/01/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: conceptual
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d4195123fbe1660c1c081c810d2b5b6b0feebd80
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891507"
---
# <a name="integrate-reporting-services-using-the-report-viewer-controls---get-started"></a>使用报表查看器控件集成 Reporting Services - 入门

报表查看器控件可用来将 Reporting Services RDL 报表集成到 WebForms 和 WinForms 应用。 有关最新更新的详细信息，请参阅[更改日志](./release-notes-ssrs-application-integration.md)。

## <a name="add-the-report-viewer-control-to-a-new-web-project"></a>向新的 Web 项目添加报表查看器控件

1. 创建新的 ASP.NET 空网站或打开现有的 ASP.NET 项目  。

    可以使用 .NET Framework 4.6 或任何更新版本。

    ![创建新的 ASP.NET 空网站的屏幕截图。](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project-4-6.png)

2. 通过 NuGet 包管理器控制台  安装报表查看器控件 NuGet 包。

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. 向项目添加新的 .aspx 页并注册报表查看器控件程序集供页面内使用。

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. 向页面添加 ScriptManagerControl  。

5. 向页面添加报表查看器控件。 可更新下面的代码段，以引用远程报表服务器上承载的报表。

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
最终页面应如下所示。

```html
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Sample" %>

<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <meta http-equiv="X-UA-Compatible" content="IE=edge" /> 
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
    <asp:ScriptManager runat="server"></asp:ScriptManager>        
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
            <ServerReport ReportServerUrl="https://AContosoDepartment/ReportServer" ReportPath="/LatestSales" />
        </rsweb:ReportViewer>
    </form>
</body>
</html>
```

## <a name="update-an-existing-project-to-use-the-report-viewer-control"></a>更新现有项目，以使用报表查看器控件

请务必将任何程序集引用更新到版本 15.0.0.0  ，包括项目的 web.config 和引用查看器控件的所有 .aspx 页。

### <a name="sample-webconfig-changes"></a>示例 web.config 更改

```xml
<?xml version="1.0"?>
<!--
  For more information on how to configure your ASP.NET application, please visit
  https://go.microsoft.com/fwlink/?LinkId=169433
  -->
<configuration>
  <system.web>
    <compilation debug="true" targetFramework="4.6">
      <assemblies>
        <!-- All assemblies updated to version 15.0.0.0. -->
        <add assembly="Microsoft.ReportViewer.Common, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.DataVisualization, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.Design, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.ProcessingObjectModel, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebDesign, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WinForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </assemblies>
      <buildProviders>
        <!-- Version updated to 15.0.0.0. -->
        <add extension=".rdlc"
          type="Microsoft.Reporting.RdlBuildProvider, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </buildProviders>
    </compilation>
    <httpRuntime targetFramework="4.6"/>
    <httpHandlers>
      <!-- Version updated to 15.0.0.0 -->
      <add path="Reserved.ReportViewerWebControl.axd" verb="*"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"
        validate="false"/>
    </httpHandlers>
  </system.web>
  <system.webServer>
    <validation validateIntegratedModeConfiguration="false"/>
    <modules runAllManagedModulesForAllRequests="true"/>
    <handlers>
      <!-- Version updated to 15.0.0.0 -->
      <add name="ReportViewerWebControlHandler" verb="*" path="Reserved.ReportViewerWebControl.axd" preCondition="integratedMode"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
    </handlers>
  </system.webServer>
</configuration>
```

### <a name="sample-aspx"></a>示例 .aspx

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 15.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="add-the-report-viewer-control-to-a-new-windows-forms-project"></a>向新的 Windows 窗体项目添加报表查看器控件

1. 创建新的 Windows 窗体应用程序或打开现有的项目  。

    可以使用 .NET Framework 4.6 或任何更新版本。
    
    ![创建新的 Windows 窗体应用程序的屏幕截图。](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project-4-6.png)

2. 通过 NuGet 包管理器控制台  安装报表查看器控件 NuGet 包。

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. 通过代码添加新控件或[向工具箱添加控件](#add-the-control-to-visual-studio-toolbar)。

    ```csharp
    private Microsoft.Reporting.WinForms.ReportViewer reportViewer1;
    
    private void InitializeComponent()
    {
        this.reportViewer1 = new Microsoft.Reporting.WinForms.ReportViewer();
        this.SuspendLayout();
        // 
        // reportViewer1
        // 
        this.reportViewer1.Location = new System.Drawing.Point(168, 132);
        this.reportViewer1.Name = "reportViewer1";
        this.reportViewer1.ServerReport.BearerToken = null;
        this.reportViewer1.Size = new System.Drawing.Size(396, 246);
        this.reportViewer1.TabIndex = 0;
        // 
        // Form1
        // 
        this.Controls.Add(this.reportViewer1);
    }
    ```

## <a name="how-to-set-100-height-on-the-report-viewer-control"></a>如何在报表查看器控件上设置 100% 高度

如果将查看器控件的高度设置为 100%，则父元素需要有一个定义的高度，或所有上级元素都需要有一定比例的高度。

### <a name="set-the-height-of-all-the-ancestors-to-100"></a>将所有上级元素的高度设置为 100%

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <style>
        html,body,form,#div1 {
            height: 100%; 
        }
    </style>
   </head>
<body>
    <form id="form1" runat="server">
    <div id="div1" >
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="https://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>
```

### <a name="set-the-parents-height-attribute"></a>设置父元素的高度属性

有关视区百分比长度的详细信息，请参阅[视区百分比长度](http://www.w3.org/TR/css3-values/#viewport-relative-lengths)。

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
</head>
<body>
    <form id="form1" runat="server">
    <div style="height:100vh;">
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="https://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>
```

## <a name="add-the-control-to-visual-studio-toolbar"></a>向 Visual Studio 工具栏添加控件

报表查看器控件现在作为 NuGet 包提供，并且默认情况下将不再显示在 Visual Studio 工具箱中。 可以向工具箱手动添加控件。

1. 安装适用于上述 WinForms 或 WebForms 的 NuGet 包。

2. 删除工具箱中列出的报表查看器控件。

    ![删除 ReportViewer 控件的屏幕截图。](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. 在工具箱中的任意位置单击右键，再选择“选择项...”  。

    ![工具箱中的“选择项”选项的屏幕截图。](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. 在 .NET Framework 组件中，选择“浏览”   。

    ![“.NET Framework 组件”对话框中的“浏览”按钮的屏幕截图。](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. 从安装的 NuGet 包中选择“Microsoft.ReportViewer.WinForms.dll”或“Microsoft.ReportViewer.WebForms.dll”   。

    > [!NOTE] 
    > NuGet 包将安装在项目的解决方案目录中。 dll 的路径将如下所示：`{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` 或 `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`。

6. 新控件将在工具箱内显示。 然后，如果需要，可将其移到工具箱内的其他选项卡中。

    ![工具箱中新 ReportViewer 控件的屏幕截图。](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

## <a name="common-issues"></a>常见问题
    
查看器控件是为新型浏览器设计的。 如果浏览器使用 IE 兼容性模式呈现页面，该控件可能无法按预期正常工作。 Intranet 站点可能需要 meta 标记来重写默认浏览器行为。

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
```

## <a name="nugetorg-pages"></a>NuGet.org 页

下面是指向 NuGet.org 网站上有关 Report Viewer 控件的 WebForm 和 WinForm 版本的文章的链接：

- Microsoft.ReportingServices.ReportViewerControl.WebForms [https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WebForms/](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WebForms/)
- Microsoft.ReportingServices.ReportViewerControl.Winforms [https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WinForms/](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.WinForms/)


## <a name="forum-feedback"></a>论坛反馈

在 [Reporting Services 论坛](/answers/topics/sql-server-reporting-services.html)上让团队了解问题。

## <a name="see-also"></a>另请参阅

[报表查看器控件中的数据收集](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)