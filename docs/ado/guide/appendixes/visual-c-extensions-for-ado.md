---
description: ADO 的 Visual C++ 扩展
title: ADO Visual C++ 扩展 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: rothja
ms.author: jroth
ms.openlocfilehash: f9fa962d4710811cf376634dcc299707f6b0e654
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453929"
---
# <a name="visual-c-extensions-for-ado"></a>ADO 的 Visual C++ 扩展
Visual C++ 使用 **#import** 指令编程 ado 的首选方法，如 [Microsoft Visual C++ ADO 编程](../../../ado/guide/appendixes/visual-c-ado-programming.md)中所述。 但是，早期版本的 ADO 附带了使用 Visual C++ 进行编程的替代方法： Visual C++ 扩展。 本部分记录了此功能，适用于必须保留 Visual C++ 扩展代码的用户，但应使用 #**import**编写新的 ADO 代码。

 使用 ADO 检索数据时，Visual C++ 程序员面临的一项最枯燥的工作是将返回的数据类型转换为 c + + 数据类型，然后将转换后的数据存储在类或结构中。 除了非常繁琐的情况外，通过 VARIANT 数据类型检索 c + + 数据会降低性能。

 ADO 提供了一个接口，该接口支持在不通过变量的情况下将数据检索到本机 C/c + + 数据类型，还提供了可简化接口使用的预处理器宏。 其结果是一个灵活的工具，更易于使用并具有极高的性能。

 常见的 C/c + + 客户端方案是将记录 [集中](../../../ado/reference/ado-api/recordset-object-ado.md) 的记录绑定到 c/c + + 结构或包含本机 C/c + + 类型的类。 通过变体时，这涉及到从变体到 C/c + + 本机类型的转换代码。 ADO 的 Visual C++ 扩展针对 Visual C++ 程序员，使此方案更容易。

 请参阅以下主题以了解有关 ADO Visual C++ 扩展的详细信息。

-   [使用 ADO Visual C++ 扩展](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Visual C++ 扩展标头](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [带有 Visual C++ 扩展的 ADO 示例](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>另请参阅
 [用于 COM Visual C++ 扩展的 Visual C++ 语法索引的 ADO](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [Visual C++ Extensions Example](../../../ado/guide/appendixes/visual-c-extensions-example.md) [Visual C++ 扩展](../../../ado/guide/appendixes/using-visual-c-extensions.md) [Visual C++ 扩展标头](../../../ado/guide/appendixes/visual-c-extensions-header.md)
