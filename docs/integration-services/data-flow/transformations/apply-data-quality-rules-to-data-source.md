---
description: 将数据质量规则应用于数据源
title: 将数据质量规则应用于数据源 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58e6e75f520bcd966cf2b1ae8e2edbc0f7a568f7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484411"
---
# <a name="apply-data-quality-rules-to-data-source"></a>将数据质量规则应用于数据源

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  您可以使用 Data Quality Services (DQS) 来更正包数据流中的数据，方法是将 DQS 情理转换连接到数据源。 有关 DQS 的详细信息，请参阅 [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)。 有关该转换的详细信息，请参阅 [DQS Cleansing Transformation](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)。  
  
 使用 DQS 清理转换处理数据时，将在数据质量服务器上创建一个数据质量项目。 使用数据质量客户端管理项目。 有关详细信息，请参阅 [打开、解锁、重命名和删除数据质量项目](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md)。  
  
### <a name="to-correct-data-in-the-data-flow"></a>更正数据流中的数据  
  
1.  创建一个包。  
  
2.  添加并配置 DQS 清除转换。 有关详细信息，请参阅 [DQS Cleansing Transformation Editor Dialog Box](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md)。  
  
3.  将 DQS 清除转换连接到数据源。  
  
  
