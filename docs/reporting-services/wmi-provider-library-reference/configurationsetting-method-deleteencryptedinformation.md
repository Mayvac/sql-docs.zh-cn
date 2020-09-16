---
description: DeleteEncryptedInformation 方法 (WMI MSReportServer_ConfigurationSetting)
title: DeleteEncryptedInformation 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6dea15e9dfe817d13b7a1178406b45ab4d8321f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497950"
---
# <a name="configurationsetting-method---deleteencryptedinformation"></a>ConfigurationSetting 方法 - DeleteEncryptedInformation
  从报表服务器数据库删除加密信息。  
  
## <a name="syntax"></a>语法  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>参数  
 *HRESULT*  
 [out] 指示调用是成功还是失败的值。  
  
 *ExtendedErrors[]*  
 [out] 一个字符串数组，包含此调用返回的其他错误。  
  
## <a name="return-value"></a>返回值  
 返回 *HRESULT* ，指示方法调用是成功还是失败。 值 0 指示方法调用已成功。 非零值指示已发生错误。  
  
## <a name="remarks"></a>备注  
 调用此方法后，将删除以下数据：  
  
-   加密的数据源信息，包括用户名和密码。  
  
-   使用传递扩展插件接口加密的订阅数据。  
  
-   报表服务器数据库密钥表中的所有信息。  
  
 调用此方法后，用户必须初始化使用报表服务器数据库的每台计算机。  
  
 调用 DeleteEncryptedInformation 方法不会影响报表服务器配置文件。  
  
## <a name="requirements"></a>要求  
 **命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [MSReportServer_ConfigurationSetting 成员](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
