---
title: 为 macOS 安装 azdata
titleSuffix: SQL Server big data clusters
description: 了解如何安装 azdata 工具以为 macOS 安装和管理大数据群集。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f6662a5ff7ced4c260e2b1a3fbd1efe5a285cf4a
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733544"
---
# <a name="install-azdata-on-macos"></a>在 macOS 上安装 `azdata`

对于 macOS 平台，可以通过 homebrew 包管理器安装 `azdata-cli`。 该 CLI 包已在以下 macOS 版本中测试： 
* 10.13 High Sierra
* 10.14 Mojave
* 10.15 Catalina

## <a name="install-with-homebrew"></a>使用 Homebrew 安装

```bash
brew tap microsoft/azdata-cli-release
brew update
brew install azdata-cli
```

>[!IMPORTANT]
>`azdata-cli` 依赖于 Homebrew `python3`、`freetds`、`unixodbc`、`zeromq` 包，并将安装它们。 `azdata-cli` 保证可与 Homebrew 上发布的这些最新版本的依赖项兼容。

## <a name="verify-install"></a>验证安装

```bash
azdata
azdata --version
```

## <a name="update"></a>更新

更新本地存储库信息，然后升级 `azdata-cli` 包。

```bash
brew tap microsoft/azdata-cli-release
brew update
brew upgrade azdata-cli
```

## <a name="uninstall"></a>卸载

使用 Homebrew 卸载 `azdata-cli` 包。

```bash
brew uninstall azdata-cli
```

## <a name="next-steps"></a>后续步骤

有关大数据群集的详细信息，请参阅[什么是 [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]？](../../big-data-cluster/big-data-cluster-overview.md)。