---
title: FILESTREAM、函数、存储过程、视图 | Microsoft Docs
description: FILESTREAM 适用于特定的 Transact-SQL 语句、API、函数、存储过程和视图。 了解哪些语句和对象支持 FILESTREAM。
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cfc44f0284b16df456881cf178c1846691aa9862
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809927"
---
# <a name="filestream-functions-stored-procedures-and-views"></a>FILESTREAM、函数、存储过程和视图
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  列出用于支持 FILESTREAM 的 Transact-SQL 语句和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库对象。  
  
 有关支持 FileTable 功能的数据库对象的列表，请参阅 [FileTable DDL, Functions, Stored Procedures, and Views](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md)。  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Transact-SQL 数据定义语言 (DDL) 语句  
  
-   [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-transact-sql.md)  
  
-   [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
  
-   [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
  
-   [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
-   [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)  
  
-   [DROP INDEX (Transact-SQL)](../../t-sql/statements/drop-index-transact-sql.md)
  
##  <a name="system-functions"></a><a name="func"></a> 系统函数  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT (Transact-SQL)](../../t-sql/functions/get-filestream-transaction-context-transact-sql.md)  
  
-   [PathName (Transact-SQL)](../../relational-databases/system-functions/pathname-transact-sql.md)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> 系统存储过程  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
-   [sp_filestream_force_garbage_collection (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> 系统视图 - 目录视图  
  
-   [sys.database_filestream_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> 系统视图 - 动态管理视图  
  
-   [sys.dm_filestream_file_io_handles (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql.md)  
  
-   [sys.dm_filestream_file_io_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql.md)  
  
##  <a name="programming-apis"></a><a name="api"></a> 编程 API  
  
-   [使用 OpenSqlFilestream 访问 FILESTREAM 数据](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
-   [托管 API - SqlFileStream 类](/dotnet/api/system.data.sqltypes.sqlfilestream)  
  
