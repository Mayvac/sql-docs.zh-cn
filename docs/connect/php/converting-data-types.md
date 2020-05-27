---
title: 转换数据类型 | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 508542ec-cc28-4a17-80f4-52325d6a48db
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ca79a13146df59b0c7159de112feee3ec478249d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015105"
---
# <a name="converting-data-types"></a>转换数据类型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

当向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发送数据或从其中检索数据时，[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 允许指定数据类型。 指定数据类型是可选的。 如果不指定数据类型，将使用默认类型。 此部分的主题介绍如何指定数据类型并提供有关默认数据类型的详细信息。  
  
## <a name="in-this-section"></a>本节内容  
  
|主题|说明|  
|---------|---------------|  
|[默认 SQL Server 数据类型](../../connect/php/default-sql-server-data-types.md)|在向服务器发送数据时，提供有关默认 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型的信息。|  
|[默认 PHP 数据类型](../../connect/php/default-php-data-types.md)|在从服务器检索数据时，提供有关默认 PHP 数据类型的信息。|  
|[如何：指定 SQL Server 数据类型](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)|演示如何在向服务器发送数据时指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。|  
|[如何：指定 PHP 数据类型](../../connect/php/how-to-specify-php-data-types.md)|演示如何在从服务器检索数据时指定 PHP 数据类型。|  
|[如何：使用内置 UTF-8 支持发送和检索 UTF-8 数据](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)|演示如何使用 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 对 UTF-8 数据的内置支持。<br /><br />已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的版本 1.1 中添加了对 UTF-8 字符的支持。|  
|[如何：在 Linux 和 macOS 中发送和检索 ASCII 数据](../../connect/php/how-to-send-and-retrieve-ascii-data-in-linux-mac.md)|演示如何在 Linux 或 macOS 中使用 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 对 ASCII 数据的支持。<br /><br />[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 的 5.2 版增加了对非 Windows 环境中 ASCII 字符的支持。|
  
## <a name="see-also"></a>另请参阅  
[Microsoft Drivers for PHP for SQL Server 编程指南](../../connect/php/programming-guide-for-php-sql-driver.md)

[SQLSRV 驱动程序 API 参考](../../connect/php/sqlsrv-driver-api-reference.md)

[常量（Microsoft Drivers for PHP for SQL Server）](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[示例应用程序（SQLSRV 驱动程序）](../../connect/php/example-application-sqlsrv-driver.md)  
  
