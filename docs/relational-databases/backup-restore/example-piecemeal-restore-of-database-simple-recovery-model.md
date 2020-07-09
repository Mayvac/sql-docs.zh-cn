---
title: 段落还原：简单恢复模式
description: 此示例演示对于使用简单恢复模式的数据库，如何在 SQL Server 中段落还原到新计算机。
ms.custom: seo-lt-2019
ms.date: 12/17/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a1f4a98b9d704f485849a9fd380eb0895977f08
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737778"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a>示例：数据库的段落还原（简单恢复模式）
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  段落还原顺序将从主文件组和所有读写辅助文件组开始，按文件组级别分阶段还原和恢复数据库。  
  
 在此示例中，灾难发生后，数据库 `adb` 被还原到新计算机。 数据库使用的是简单恢复模式。 灾难发生之前，所有文件组均处于联机状态。 文件组 `A` 和 `C` 是可读/写的，文件组 `B` 是只读的。 文件组 `B` 在最新部分备份之前变为只读的，该文件组包含主文件组和读/写辅助文件组 `A` 和 `C`。 文件组 `B` 变为只读后，对文件组 `B` 进行了单独的文件备份。  
  
## <a name="restore-sequences"></a>还原顺序  
  
1.  主文件组以及文件组 `A` 和 `C`的部分还原。  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     此时，主文件组以及文件组 `A` 和 `C` 处于联机状态。 文件组 `B` 中的所有文件都处于恢复挂起状态，该文件组处于脱机状态。  
  
2.  对文件组 `B`进行联机还原。  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     所有文件组现在都处于联机状态。  
  
## <a name="additional-examples"></a>其他示例  
  
-   [示例：仅对某些文件组进行段落还原（简单恢复模式）](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [示例：只读文件的联机还原（简单恢复模式）](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [示例：数据库的段落还原（完整恢复模式）](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [示例：仅对某些文件组进行段落还原（完整恢复模式）](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [示例：读/写文件的联机还原（完整恢复模式）](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [示例：只读文件的联机还原（完整恢复模式）](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>另请参阅  
 [联机还原 (SQL Server)](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [段落还原 (SQL Server)](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  
