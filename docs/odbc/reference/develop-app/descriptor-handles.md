---
description: 描述符句柄
title: 描述符句柄 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application parameter descriptor [ODBC]
- automatically allocated descriptors [ODBC]
- implementation row descriptor [ODBC]
- descriptor handles [ODBC]
- handles [ODBC], descriptor
- implementation parameter descriptor [ODBC]
- apd [ODBC]
- ard [ODBC]
- explicitly allocated descriptors [ODBC]
- ipd [ODBC]
- ird [ODBC]
- application row descriptor [ODBC]
ms.assetid: 7741035c-f3e7-4c89-901e-fe528392f67d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 859071eacbfa65f360965cf5c5df17d4fbf6361d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476719"
---
# <a name="descriptor-handles"></a>描述符句柄
*描述符*是描述 SQL 语句或结果集的列的元数据的集合，如应用程序或驱动程序所示 (也称为*实现*) 。 因此，描述符可以填充四个角色中的任意一个：  
  
-   **应用程序参数描述符 (APD) 。** 包含有关绑定到 SQL 语句中的参数的应用程序缓冲区的信息，如其地址、长度和 C 数据类型。  
  
-   **实现参数描述符 (IPD) 。** 包含 SQL 语句中参数的相关信息，例如 sql 语句的 SQL 数据类型、长度和为 null 性。  
  
-   **应用程序行描述符 (ARD) 。** 包含有关绑定到结果集中的列的应用程序缓冲区的信息，如其地址、长度和 C 数据类型。  
  
-   **实现行描述符 (IRD) 。** 包含有关结果集中的列的信息，如其 SQL 数据类型、长度和为 null 性。  
  
 四个描述符 (一个填充每个角色) 在分配语句时自动分配。 这些 *描述符称为自动分配的描述符* ，始终与该语句相关联。 应用程序还可以分配带有 **SQLAllocHandle**的描述符。 这称为 *显式分配的描述符*。 它们在连接上进行分配，并可与该连接上的一个或多个语句相关联，以满足这些语句上的 APD 或 ARD 的角色。  
  
 ODBC 中的大多数操作都可以在不显式使用应用程序的情况下执行。 但是，描述符为某些操作提供了方便的快捷方式。 例如，假设某个应用程序要从两个不同的缓冲区集中插入数据。 若要使用第一组缓冲区，请重复调用 **SQLBindParameter** 将其绑定到 **INSERT** 语句中的参数，然后执行该语句。 若要使用第二组缓冲区，请重复此过程。 此外，它还可以设置到一个描述符中第一组缓冲区的绑定，以及另一个描述符中的第二组缓冲区。 若要在绑定集之间切换，应用程序只需调用 **SQLSetStmtAttr** ，并将正确的说明符与作为 APD 的语句相关联。  
  
 有关描述符的详细信息，请参阅 [描述符类型](../../../odbc/reference/develop-app/types-of-descriptors.md)。
