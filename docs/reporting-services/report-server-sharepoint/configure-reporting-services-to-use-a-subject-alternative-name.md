---
title: 配置 Reporting Services 以使用使用者可选名称 | Microsoft Docs
description: 了解如何通过修改 rsreportserver.config 文件并使用 Netsh.exe 工具来配置 SQL Server Reporting Services 以使用 SAN。
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ecb4b0be06731070c0852f23375fafea0eed4434
ms.sourcegitcommit: 66a0672e47415dbd5cfd8d19075102c8c3973e70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83767057"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>配置 Reporting Services 以使用使用者可选名称

本主题说明了如何通过修改 rsreportserver.config 文件和使用 Netsh.exe 工具配置 Reporting Services (SSRS) 以使用使用者可选名称 (SAN)。

该说明适用于 Reporting Service URL 以及 Web 服务 URL。

若要使用 SAN，TLS/SSL 证书必须注册在服务器上、进行签名并且有私钥。 你无法使用自签名证书。  
  
 可以将 Reporting Services 中的 URL 配置为使用 TLS/SSL 证书。 证书通常只包含使用者名称，它只允许对传输层安全性 (TLS)（旧称为“安全套接字层 (SSL)”）会话使用一个 URL。 SAN 是证书中的附加字段，可便于 TLS 服务侦听许多 URL，并与其他应用程序共享 TLS 端口。 SAN 的形式为 `www.s2.com`。  
  
 若要详细了解 Reporting Services 的 TLS 设置，请参阅[在本机模式报表服务器上配置 TLS 连接](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)。  
  
## <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>将 SSRS 配置为使用适用于 Web 服务 URL 的使用者可选名称
  
1.  启动 Reporting Services 配置管理器。  
  
     有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)。  
  
2.  在“Web 服务 URL”  页上，选择 TLS/SSL 端口和 TLS/SSL 证书。  
  
     ![Reporting Services 配置管理器](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Reporting Services 配置管理器")  
  
     配置管理器为端口注册 TLS/SSL 证书。  
  
3.  打开 rsreportserver.config 文件。  
  
     对于 SSRS 本机模式，默认情况下，该文件位于以下文件夹：  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  复制 Report Server Web 服务应用程序的 URL 部分。  
  
     例如，以下初始 URL 部分为：  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     以下修改后的 URL 部分为：
  
    ```  
    <URL>  
         <UrlString>https://www.s1.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.s2.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
5.  保存 rsreportserver.config 文件。  
  
6.  以管理员身份启动一个命令提示符并运行 Netsh.exe 工具。  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  键入以下内容切换至 http 上下文。  
  
    ```  
    Netsh>http  
    ```  
  
8.  键入以下内容显示现有 urlacl：
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     出现如下条目。  
  
    ```  
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     一个 urlacl 是一个保留的 URL 的 DACL（自由访问控制列表）。  
  
9. 通过键入以下内容，为使用者备用名称创建一个用户和 SDDL 与现有条目相同的新条目。  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. 在 Reporting Services 配置管理器的“报表服务器状态”  页面上单击“停止”  ，然后单击“启动”  以重启报表服务器。  
  
## <a name="see-also"></a>另请参阅

 [RsReportServer.config 配置文件](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services 配置管理器](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [修改 Reporting Services 配置文件](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [配置报表服务器 URL](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

更多疑问？ [请访问 Reporting Services 论坛](https://go.microsoft.com/fwlink/?LinkId=620231)
