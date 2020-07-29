---
title: 生成用于执行数据整理任务的代码
titleSuffix: Azure Data Studio
description: 本文介绍如何在 Azure Data Studio 中使用 PROSE 代码加速器自动生成可用于执行常见数据整理任务的代码。
author: dphansen
ms.author: davidph
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning-bdc
ms.openlocfilehash: 548db45e97fed2a5d955eef947c6d21004d439d2
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243438"
---
# <a name="data-wrangling-using-prose-code-accelerator"></a>使用 PROSE 代码加速器进行数据整理

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

PROSE 代码加速器可生成用于执行数据整理任务的可读 Python 代码。 在 Azure Data Studio 中的笔记本上工作时，可以无缝混合生成的代码和手动编写的代码。 本文概述了如何使用代码加速器。

 > [!NOTE]
 > Program Synthesis using Examples（又名 PROSE）是使用 AI 生成用户可读代码的一种 Microsoft 技术。 该技术通过分析用户的意图和数据，生成多个候选程序，使用排名算法来选取最佳程序来实现此目的。 若要了解有关 PROSE 技术的详细信息，请访问 [PROSE 主页](https://microsoft.github.io/prose/)。

代码加速器预安装有 Azure Data Studio。 可以像笔记本中其他的 Python 包那样导入它。 按照约定，我们以简写形式 cx 将其导入。

```python
import prose.codeaccelerator as cx
```

在当前版本中，代码加速器可以智能地生成用于执行以下任务的 Python 代码：

- 将数据文件读入 Pandas 或 Pyspark 数据帧。
- 修复数据帧中的数据类型。
- 查找表示字符串列表中模式的正则表达式。

若要大致了解代码加速器方法，请参阅[文档](https://aka.ms/prose-codeaccelerator-overview)。

## <a name="reading-data-from-a-file-to-a-dataframe"></a>将数据从文件读取到数据帧

通常，将文件读取到数据帧需要查看文件内容，还需要确定要传到数据加载库的正确参数。 根据文件的复杂性，标识正确的参数可能需要进行多次迭代。

PROSE 代码加速器会分析数据文件的结构，并自动生成用以加载文件的代码，以解决此问题。 在大多数情况下，生成的代码可正确分析数据。 在少数情况下，可能需要调整代码以满足需求。

请考虑以下示例：

 ```python
import prose.codeaccelerator as cx

# Call the ReadCsvBuilder builder to analyze the file content and generate code to load it
builder = cx.ReadCsvBuilder(r'C:/911.txt')

#Set target to pyspark if generating code to use pyspark library
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
 ```

前一代码块打印以下 Python 代码，以读取带分隔符的文件。 了解 PROSE 如何自动算出要跳过的行数、标头、引用符、分隔符等等。

 ```python
import pandas as pd

def read_file(file):
    names = ["lat",
             "lng",
             "desc",
             "zip",
             "title"]

    df = pd.read_csv(file,
        skiprows = 11,
        header = None,
        names = names,
        quotechar = "\"",
        delimiter = "|",
        index_col = False,
        dtype = str,
        na_values = [],
        keep_default_na = False,
        skipinitialspace = True)
    return df
 ```

代码加速器可以生成将带分隔符的文件、JSON 文件和固定宽度的文件加载到数据帧中的代码。 对于读取固定宽度的文件，`ReadFwfBuilder` 可以选择使用可进行分析以获取列位置的用户可读架构文件。 若要了解详细信息，请参阅[文档](https://aka.ms/prose-codeaccelerator-docs)。

## <a name="fixing-data-types-in-a-dataframe"></a>修复数据帧中的数据类型

Pandas 或 Pyspark 数据帧的数据类型经常出现错误。 通常，这是由于列中存在一些类型不一致的值所致。 因此，整数读取为浮点数或字符串，日期读取为字符串。 手动修复数据类型所需的工作量与列数成正比。

在这些情况下可以使用 `DetectTypesBuilder`。 它会分析数据（而不是以黑盒方式修复数据类型），生成用于修复数据类型的代码。 代码作为起点。 你可以根据需要查看、使用或修改代码。

```python
import prose.codeaccelerator as cx

builder = cx.DetectTypesBuilder(df)

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

#Get the code generated to fix the data types
builder.learn().code()
```

若要了解详细信息，请参阅[文档](https://aka.ms/prose-codeaccelerator-fixtypes)。

## <a name="identifying-patterns-in-strings"></a>标识字符串中的模式

另一种常见场景是检测字符串列中的模式，以便进行清除或分组。 例如，你的一个日期列中可能有多种不同格式的日期。 为了标准化这些值，你可能想要使用正则表达式来编写条件语句。


|行|名称                      |BirthDate      |
|--:|:-------------------------|:--------------|
| 0 |Bertram du Plessis        |1995           |
| 1 |Naiara Moravcikova        |未知        |
| 2 |Jihoo Spel                |2014           |
| 3 |Viachaslau Gordan Hilario |22-Apr-67      |
| 4 |Maya de Villiers          |19-Mar-60      |

根据数据的数量和多样性，为列中的各种模式编写正则表达式可能是一项非常耗时的任务。 `FindPatternsBuilder` 是一个功能强大的代码加速工具，可以为字符串列表生成正则表达式，从而解决上述问题。

```python
import prose.codeaccelerator as cx

builder = cx.FindPatternsBuilder(df['BirthDate'])

#Set target to pyspark if working with pyspark
#builder.Target = "pyspark"

builder.learn().regexes
```

下面是由 `FindPatternsBuilder` 为上述数据生成的正则表达式。

```
^[0-9]{2}-[A-Z][a-z]+-[0-9]{2}$
^[0-9]{2}[\s][A-Z][a-z]+[\s][0-9]{4}$
^[0-9]{4}$
^Unknown$
```

除了生成正则表达式外，`FindPatternsBuilder` 还可以生成用于根据生成的正则表达式将这些值聚类的代码。 它还可以断言列中所有的值都符合生成的正则表达式。 若要了解详细信息并查看其他实用场景，请参阅[文档](https://aka.ms/prose-codeaccelerator-findpatterns)。
