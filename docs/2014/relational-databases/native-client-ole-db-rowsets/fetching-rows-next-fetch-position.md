---
title: 下次提取位置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: rothja
ms.author: jroth
ms.openlocfilehash: fcc771eef4acf603148bc4b4318e810b1bd72302
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055941"
---
# <a name="next-fetch-position"></a>下次提取位置
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序跟踪下一个提取位置，以便对**GetNextRows**方法的调用序列（无需跳过、对方向的更改或对**FindNextRow**、 **Seek**或**RestartPosition**方法的干预调用）将读取整个行集，而不会跳过或重复任何行。 可以通过调用 IRowset::GetNextRows、IRowset::RestartPosition 或 IRowsetIndex::Seek，或通过调用 FindNextRow 且 pBookmark 值为空来更改下次提取位置******************。 调用 FindNextRow 且 pBookmark 值不为空时，不会影响下次提取位置******。  
  
## <a name="see-also"></a>另请参阅  
 [提取行](fetching-rows.md)  
  
  
