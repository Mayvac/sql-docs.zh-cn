---
title: 配置 PolyBase 连接
description: 介绍如何将 PolyBase 配置为并行数据仓库以连接到外部 Hadoop 或 Microsoft Azure 存储 blob 数据源。 使用 PolyBase 运行可集成多个源（包括 Hadoop、Azure blob 存储和并行数据仓库）中的数据的查询。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 98527bf770da61c98368171e75b3a9b82ceba13c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767176"
---
# <a name="configure-polybase-connectivity"></a>配置 PolyBase 连接
PolyBase 使你的分析平台系统 (的 AP) 处理可从外部数据源读取数据并将数据写入外部数据源的 Transact-sql 查询。 访问外部数据的相同查询也可以在你的 AP 中包含关系表。 这样，你便可以将外部源中的数据与你的 AP 数据库中的高价值关系数据组合在一起。

![PolyBase 逻辑](media/polybase/polybase-logical.png)

在 AP 上，PolyBase 支持 (HDFS) 文件系统和 Azure Blob 存储读取和写入 Hadoop。 PolyBase 还能够将某些计算作为 mapreduce 作业推送到 Hadoop 节点，以优化整体查询性能。 接入点上的 PolyBase 可对分隔文本、ORC 和 Parquet 文件进行操作。 请参阅 [什么是 PolyBase](../relational-databases/polybase/polybase-guide.md) ，了解完整说明及其功能。

> [!NOTE]
> AP 目前仅支持标准常规用途 v1 本地冗余 (LRS) Azure Blob 存储。

## <a name="features-and-limitations"></a>功能和限制
请参阅 [功能和限制](../relational-databases/polybase/polybase-versioned-feature-summary.md) ，获取 PolyBase 功能的摘要和有关 ap 和其他 SQL Server 产品的已知限制。

> [!NOTE] 
> PolyBase 相关文章的其余部分介绍了如何在 AP 2016 (AU6) 和更高版本上配置 PolyBase。

## <a name="see-also"></a>另请参阅
- [Hadoop](polybase-configure-hadoop.md)
- [Azure Blob 存储](polybase-configure-azure-blob-storage.md)
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
