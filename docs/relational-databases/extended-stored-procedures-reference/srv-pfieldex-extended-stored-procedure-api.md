---
title: srv_pfieldex（扩展存储过程 API）| Microsoft Docs
description: 了解扩展存储过程 API 中 srv_pfieldex 如何返回指向包含所请求 SRV_PROC 字段的数据的指针。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_pfieldex
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: ee0bf315964d5710d657abf2288a2b9a79b3c00b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248284"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a>srv_pfieldex（扩展存储过程 API）
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]请改用 CLR 集成。  
  
 返回一个指针，指向包含请求的 SRV_PROC 字段的数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
```  
  
## <a name="arguments"></a>自变量  
 srvproc**  
 指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。 该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。  
  
 *定义域*  
 指定要返回的 srvproc 字段**。  
  
|字段|描述|返回类型|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|当前会话消息 LCID。|ULONG*|  
|SRV_INSTANCENAME|实例名称（如果已命名）；否则返回 NULL。|WCHAR*|  
  
 *长度*  
 指向一个 int 变量的指针，该变量包含所返回的 field 值的长度（以字节为单位）******。 如果 len 为 NULL，则不返回长度**。 返回 NULL 时，*len 设置为 0**。  
  
## <a name="returns"></a>返回值  
 一个指针，指向其类型取决于 field 的数据**。 len 为 NULL 或 srvproc 为 NULL 时，则返回 NULL****。 如果 field 未知，则返回 NULL**。 返回 NULL 时，*len 设置为 0**。  
  
> [!IMPORTANT]  
>  从服务器返回的缓冲区应为只读的。 否则，可能损坏服务器状态。  
  
## <a name="remarks"></a>备注  
 **安全说明** 应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，应对这些 DLL 进行测试。 有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。  
  
  
