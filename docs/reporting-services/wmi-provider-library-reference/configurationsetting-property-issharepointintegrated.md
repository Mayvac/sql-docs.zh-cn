---
description: ConfigurationSetting 属性 - IsSharePointIntegrated
title: IsSharePointIntegrated 属性 (WMI) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 628212c9538b3a2efea08b0fdfb5def7fe017e10
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497900"
---
# <a name="configurationsetting-property---issharepointintegrated"></a>ConfigurationSetting 属性 - IsSharePointIntegrated
  指定报表服务器是否处于 SharePoint 集成模式。 从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]开始，此属性将始终返回 **False** ，因为在 SharePoint 模式下， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例为 SharePoint 共享服务，且不受 WMI 提供程序的控制。  
  
## <a name="syntax"></a>语法  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>属性值  
 一个 **Boolean** 对象，指示报表服务器是否处于 SharePoint 集成模式。  
  
## <a name="example-code"></a>示例代码  
 [MSReportServer_ConfigurationSetting 类](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>要求  
 **命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [MSReportServer_ConfigurationSetting 成员](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
