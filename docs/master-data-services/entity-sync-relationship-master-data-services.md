---
title: 实体同步关系
description: 实体同步是实体版本间的单向可重复同步，可用于在 Master Data Services 模型之间共享实体数据。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0dac91e4f43d244e133511e792f29770949da905
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811922"
---
# <a name="entity-sync-relationship-master-data-services"></a>实体同步关系 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  实体同步是实体版本间的单向可重复同步。 它使你可在不同模型间共享实体数据。 你可以在一个模型中保留单个事实源，并在其他模型中重用该主数据。 例如，你可以将 US 状态数据存储在一个模型实体中，并在其他模型中重用该数据。  
  
 使用实体同步，还可以制作数据的一次性副本。  
  
 在同步执行期间，源实体中所有具有自由格式和文件属性的叶成员都同步到目标实体。 这将创建、删除和修改实体架构和成员。  
  
 一旦建立了同步关系，则目标实体只能通过同步进程修改。 可以随时删除同步关系以使目标实体可编辑。  
  
## <a name="see-also"></a>另请参阅  
 [&#40;Master Data Services 创建和执行实体同步关系&#41;](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [编辑和删除实体同步关系 (Master Data Services)](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
