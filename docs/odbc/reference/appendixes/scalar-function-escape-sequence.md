---
description: 标量函数转义序列
title: 标量函数转义序列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b00be53fa0b9e23c2ee2b4e9cbac2db8e9884bc7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424939"
---
# <a name="scalar-function-escape-sequence"></a>标量函数转义序列
ODBC 对标量函数使用转义序列。 此转义序列的语法如下所示：  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>备注  
 在 BNF 表示法中，语法如下：  
  
 *ODBC-function-escape* ：： =  
  
 *ODBC-esc-发起方* fn *标量函数 ODBC-esc-终止符*  
  
 *标量函数* ：： = *函数名称* (*参数列表*)   
  
  (非终止符 *函数名* 和 *函数名* (*参数列表* 的定义，) 派生自 [附录 E：标量函数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)中的标量函数的列表。 )   
  
 *ODBC-esc-发起方* ：： = {  
  
 *ODBC-esc-终止符* ：： =}  
  
 若要确定数据源是否支持过程并且驱动程序支持 ODBC 过程调用语法，应用程序可以调用 **SQLGetInfo**。 有关详细信息，请参阅 [附录 E：标量函数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)。
