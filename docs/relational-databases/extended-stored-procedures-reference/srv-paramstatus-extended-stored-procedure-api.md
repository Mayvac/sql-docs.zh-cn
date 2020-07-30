---
title: srv_paramstatus（扩展存储过程 API）| Microsoft Docs
description: 了解 srv_paramstatus 如何返回特定的远程存储过程调用参数的状态。
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramstatus
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
author: rothja
ms.author: jroth
ms.openlocfilehash: e55986b0d781b311b050eb5695ca350f7331e25c
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248326"
---
# <a name="srv_paramstatus-extended-stored-procedure-api"></a>srv_paramstatus（扩展存储过程 API）
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]请改用 CLR 集成。  
  
 返回特定远程存储过程调用参数的状态。  
  
## <a name="syntax"></a>语法  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>参数  
 srvproc**  
 指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。 该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。  
  
 *n*  
 指示参数的编号。 第一个参数的编号为 1。  
  
## <a name="returns"></a>返回  
 包含参数的状态标志的 int****。 目前，只有一个标志：如果位 0 设置为 1，则参数为一个返回参数。 如果没有第 n 个参数或没有任何远程存储过程，则返回 -1**。  
  
## <a name="remarks"></a>备注  
 此例程返回远程存储过程调用参数的状态标志。  
  
 参数包含通过远程存储过程在客户端和应用程序之间传递的数据。 客户端可以指定某些参数作为返回参数。 这些返回参数可包含应用程序传递回客户端的值。  
  
 目前，只有一个状态标志，该标志指示参数是否为一个返回参数。  
  
 使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。 如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。 如果发生错误，仍然会调用 SRV_RPC 处理程序，但它似乎没有参数， **srv_rpcparams**返回0。  
  
> [!IMPORTANT]  
>  应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。 有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。  
  
## <a name="see-also"></a>另请参阅  
 [srv_rpcparams（扩展存储过程 API）](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
