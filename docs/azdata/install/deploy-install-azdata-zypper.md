---
title: 使用 zypper 安装 azdata
titleSuffix: SQL Server big data clusters
description: 了解如何安装 azdata 工具以使用 zypper 安装和管理大数据群集。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2445fecc554ff9f7816bbf75483ab49bbee542c1
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733661"
---
# <a name="install-azdata-with-zypper"></a>使用 zypper 安装 `azdata`

带有 `zypper` 的 Linux 分发版有 `azdata-cli` 包。 该 CLI 包已在使用 `zyper` 的 Linux 版本中测试：

- openSUSE 42.2 (leap) +
- SLES 12 SP 2 +

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-zypper"></a>使用 zypper 进行安装
>[!IMPORTANT]
>`azdata-cli` 的 RPM 包依赖于 python3 包。 在你的系统上，这可能是早于所要求的 Python 3.6.x  的 Python 版本。 如果这对你来说是问题，请找到一个替代 python3 包，或按照使用 [`pip`](../install/deploy-install-azdata-pip.md) 的手动安装说明执行操作。

1. 安装必要的依赖项以安装 `azdata-cli`

   ```bash
   sudo zypper install -y curl
   ```

1. 导入 Microsoft 存储库密钥

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. 创建本地存储库信息

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2019.repo
   ```

1. 安装

   ```bash
   sudo zypper install --from packages-microsoft-com-mssql-server-2019 -y azdata-cli
   ```

## <a name="verify-install"></a>验证安装

   ```bash
   azdata
   azdata --version
   ```

## <a name="update"></a>更新

使用 `zypper update` 命令更新 `azdata-cli`。

   ```bash
   sudo zypper refresh
   sudo zypper update azdata-cli
   ```

## <a name="uninstall"></a>卸载

从系统中删除包

```bash
   sudo zypper removerepo azdata-cli
```

## <a name="next-steps"></a>后续步骤

有关大数据群集的详细信息，请参阅[什么是 [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]？](../../big-data-cluster/big-data-cluster-overview.md)。
