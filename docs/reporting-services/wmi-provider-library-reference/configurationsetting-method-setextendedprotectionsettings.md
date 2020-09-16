---
description: SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting)
title: SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 80693f5720974bedc8c0d4dae13ed4bb24727980
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480639"
---
# <a name="configurationsetting-method---setextendedprotectionsettings"></a>ConfigurationSetting 方法 - SetExtendedProtectionSettings
  SetExtendedProtectionSettings 方法用于设置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置文件 RSReportServer.config 中的 RSWindowsExtendedProtectionLevel 和 RSWindowsExtendedProtectionScenario 属性。  
  
## <a name="syntax"></a>语法  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>参数  
 *ExtendedProtectionLevel*  
 设置 RSRreportserver.config 文件中的 RSWindowsExtendedProtectionLevel。 必需值不区分大小写。  
  
 下表显示有效值：  
  
 `"Off | Allow | Require"`  
  
 *ExtendedProtectionScenario*  
 设置 RSReportserver.config 文件中的 RSWindowsExtendedProtectionScenario。 必需值不区分大小写。  
  
 下表显示有效值：  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a>注解  
 当 RSReportServer.config 文件中的 AuthenticationTypes 包括 RSWindowNTLM、RSWindowsNegotiate 或 RSWindowsKerberos 时，应用 RSWindowsExtendedProtectionLevel 和 RSWindowsExtendedProtectionScenario 属性。 设置这些属性将影响用户和客户端软件如何在报表服务器上进行身份验证。 建议你在将 ExtendedProtectionLevel 设置为 **Allow** 或 **Require**前阅读有关扩展保护的文档。  
  
 要设置 ExtendedProtectionLevel，用户必须是报表服务器上 BUILTIN\Administrators 组的成员。  
  
## <a name="requirements"></a>要求  
 **命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [RSWindowsExtendedProtectionScenario 属性 (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [RSWindowsExtendedProtectionLevel 属性 (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Reporting Services 针对验证的扩展保护](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [RsReportServer.config 配置文件](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
