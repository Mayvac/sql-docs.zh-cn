---
title: 管理 Oracle 表空间 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6f969ef7b006c6ccf3f24668322fe55c00511c4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893305"
---
# <a name="manage-oracle-tablespaces"></a>管理 Oracle 表空间
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  表空间是一个数据库存储单元，大致相当于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的文件组。 表空间允许存储和管理各个组内的数据库对象。 有关详细信息，请参阅 Oracle 文档。  
  
 如果将表配置为 Oracle 发布的一部分，则可以选择指定在存储复制记录信息时使用现有的 Oracle 表空间。 如果未指定，则复制对象的表空间就是与配置发布服务器时配置的复制管理用户架构相关联的默认表空间。  
  
 **为项目记录表指定表空间**：  
  
-   在 **“项目属性”** 对话框中指定表空间。 有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)。  
  
-   使用 [sp_changearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)。 若要使用 **sp_changearticle**，请指定下列内容：  
  
    -   为参数 \@publisher 指定 Oracle 发布服务器的名称。  
  
    -   为参数 \@publication 指定 Oracle 发布的名称。  
  
    -   为参数 \@article 指定项目的名称。  
  
    -   为参数 \@property 指定“tablespace”值。  
  
    -   为参数 \@value 指定表空间名称。  
  
## <a name="see-also"></a>另请参阅  
 [配置 Oracle 发布服务器](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [在 Oracle 发布服务器上创建的对象](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  
