---
title: 连接到 Azure SQL 数据库
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: db4f18fc780f1c3b0a88b5c18cd2ff3410800dad
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823642"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a>使用 SQL Server Native Client 连接到 Azure SQL 数据库
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  有关演示如何使用 Native Client 连接到的示例 [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅[开发： (Azure SQL 数据库) 的操作指南主题](https://msdn.microsoft.com/library/ee621787.aspx)。  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>连接到 SQL Database 时的已知问题  
 以下是使用 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client 连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时的一些已知问题：  
  
-   如果在阶段中使用**SQLBrowseConnect** ，则使用**SQLBrowseConnect**建立的连接可能被拒绝。  例如，如果在第一次调用中发送驱动程序名称，在第二次调用中发送服务器和凭据（用户名和密码），建立连接，然后在第三次调用中发送数据库名称和语言。  第三次调用将导致 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 发出 USE 语句来更改数据库。 但是，在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 中不支持 USE 语句，因此生成以下错误：  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [使用 SQL Server Native Client 生成应用程序](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
