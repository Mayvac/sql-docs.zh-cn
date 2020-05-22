---
title: 快速入门：运行 Python 脚本
description: 使用 SQL Server 机器学习服务运行一组简单的 Python 脚本。 了解如何在 SQL Server 实例中使用存储过程 sp_execute_external_script 执行该脚本。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/17/2020
ms.topic: quickstart
author: cawrites
ms.author: chadam
ms.reviewer: garye
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6b15423d82a13485d343dc797bdf6e6efe25088f
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606437"
---
# <a name="quickstart-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>快速入门：通过 SQL Server 机器学习服务运行简单的 Python 脚本
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
在本快速入门中，你将在 [SQL Server 机器学习服务](../sql-server-machine-learning-services.md)中或[大数据群集](../../big-data-cluster/machine-learning-services.md)上运行一组简单的 Python 脚本。 你将了解如何在 SQL Server 实例中使用存储过程 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 执行该脚本。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
在本快速入门中，将使用 [SQL Server 机器学习服务](../sql-server-machine-learning-services.md)运行一组简单的 Python 脚本。 你将了解如何在 SQL Server 实例中使用存储过程 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 执行该脚本。
::: moniker-end

## <a name="prerequisites"></a>先决条件


::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
- SQL Server 机器学习服务。 有关如何安装机器学习服务的信息，请参阅 [Windows 安装指南](../install/sql-machine-learning-services-windows-install.md)或 [Linux 安装指南](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json)。 还可以[启用 SQL Server 大数据群集上的机器学习服务](../../big-data-cluster/machine-learning-services.md)。
::: moniker-end

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
- SQL Server 机器学习服务。 有关如何安装机器学习服务的信息，请参阅 [Windows 安装指南](../install/sql-machine-learning-services-windows-install.md)或 [Linux 安装指南](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json)。 还可以[启用 SQL Server 大数据群集上的机器学习服务](../../big-data-cluster/machine-learning-services.md)。
::: moniker-end

- 你还需要一个工具来运行包含 Python 脚本的 SQL 查询。 可使用任何数据库管理或查询工具运行这些脚本，只要它可以连接到 SQL Server 实例，并运行 T-SQL 查询或存储过程即可。 本快速入门使用 [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download-azure-data-studio)。

## <a name="run-a-simple-script"></a>运行简单脚本

若要运行 Python 脚本，请将它作为参数传递给系统存储过程 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)。
此系统存储过程在 SQL Server 的上下文中启动 Python 运行时，将数据传递给 Python，安全地管理 Python 用户会话并将任何结果返回给客户端。

在下面的步骤中，在 SQL Server 实例中运行此示例 Python 脚本：

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. 在连接到 SQL Server 实例的 **Azure Data Studio** 中打开一个新的查询窗口。

1. 将完整的 Python 脚本传递到 `sp_execute_external_script` 存储过程。

   通过 `@script` 参数传递脚本。 `@script` 参数内的所有内容都必须是有效的 Python 代码。

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

1. 计算出正确的结果，Python `print` 函数将结果返回到“消息”窗口。

   结果应该如下所示。

    **结果**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>运行 Hello World 脚本

典型的示例脚本只输出字符串“Hello World”。 运行以下命令。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

`sp_execute_external_script` 存储过程的输入包括：

| | |
|-|-|
| @language | 定义本例中要调用 Python 的语言扩展 |
| @script | 定义传递给 Python 运行时的命令<br>必须以 Unicode 文本形式将整个 Python 脚本封装在此参数中。 还可将文本添加到 nvarchar 类型的变量并调用该变量 |
| @input_data_1 | 查询返回的数据将传递给 Python 运行时，后者将数据以数据帧的形式返回 |
|WITH RESULT SETS | 子句为 SQL Server 定义返回的数据表的架构，并将“Hello World”添加为列名称且 int 为数据类型 |


命令输出以下文本：

| Hello World |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>使用输入和输出

默认情况下，`sp_execute_external_script` 接受单个数据集作为输入，通常以有效的 SQL 查询的形式提供。 然后，它返回单个 Python 数据帧作为输出。

现在，使用 `sp_execute_external_script` 的默认输入和输出变量：InputDataSet 和 OutputDataSet 。

1. 创建一个小型测试数据表。

    ```sql
    CREATE TABLE PythonTestData (col1 INT NOT NULL)
    
    INSERT INTO PythonTestData
    VALUES (1);
    
    INSERT INTO PythonTestData
    VALUES (10);
    
    INSERT INTO PythonTestData
    VALUES (100);
    GO
    ```

1. 使用 `SELECT` 语句来查询表。
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **结果**

    ![PythonTestData 表的内容](./media/select-pythontestdata.png)

1. 运行以下 Python 脚本。 它使用 `SELECT` 语句从表中检索数据，通过 Python 运行时传递数据，并以数据帧的形式返回数据。 `WITH RESULT SETS` 子句为 SQL 定义返回的数据表的架构，并添加了列名称“NewColName”。

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **结果**

    ![从表返回数据的 Python 脚本的输出](./media/python-output-pythontestdata.png)

1. 现在，更改输入变量和输出变量的名称。 默认的输入和输出变量名称是 InputDataSet 和 OutputDataSet，而以下脚本会将名称更改为 SQL_in 和 SQL_out   ：

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    请注意 Python 区分大小写。 Python 脚本中使用的输入和输出变量（SQL_out、SQL_in）需要匹配使用 `@input_data_1_name` 和 `@output_data_1_name` 定义的名称，包括大小写 。

   > [!TIP]
   > 只能将一个输入数据集作为参数传递，并且只能返回一个数据集。 但是，可以从 Python 代码内调用其他数据集，并且除数据集以外，还可以返回其他类型的输出。 也可向任何参数添加 OUTPUT 关键字，让该参数随结果一起返回。

1. 还可以仅使用没有输入数据的 Python 脚本（`@input_data_1` 设置为空白）生成值。

   以下脚本输出文本“hello”和“world”。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   mytextvariable = pandas.Series(["hello", " ", "world"]);
   OutputDataSet = pd.DataFrame(mytextvariable);
   '
       , @input_data_1 = N''
   WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
   ```

   **结果**

   ![使用 @script 作为输入的查询结果](./media/python-data-generated-output.png)

> [!NOTE]
> Python 使用前导空格对语句进行分组。 因此，当嵌入的 Python 脚本跨越多行时（如前面的脚本中所述），请勿尝试将 Python 命令缩进到与 SQL 命令保持一致。 例如，此脚本将生成错误：

  ```text
  EXECUTE sp_execute_external_script @language = N'Python'
      , @script = N'
      import pandas as pd
      mytextvariable = pandas.Series(["hello", " ", "world"]);
      OutputDataSet = pd.DataFrame(mytextvariable);
      '
      , @input_data_1 = N''
  WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
  ```

## <a name="check-python-version"></a>检查 Python 版本

若要查看 SQL Server 实例中安装的 Python 版本，请运行以下脚本。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

Python `print` 函数将该版本返回到“消息”窗口。 在下面的示例输出中，可以看到本例中安装的是 Python 版本 3.5.2。

**结果**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>列出 Python 包

Microsoft 在 SQL Server 实例中提供了许多随 SQL Server 机器学习服务预安装的 Python 包。

若要查看安装的 Python 包（包括版本）列表，请运行以下脚本。

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pkg_resources
import pandas
dists = [str(d) for d in pkg_resources.working_set]
OutputDataSet = pandas.DataFrame(dists)
'
WITH RESULT SETS(([Package] NVARCHAR(max)))
GO
```

此列表来自 Python 中的 `pkg_resources.working_set`，并作为数据帧返回到 SQL。

**结果**

:::image type="content" source="media/python-package-list.png" alt-text="已安装的 Python 包的列表":::

## <a name="next-steps"></a>后续步骤

若要了解在 SQL 机器学习中使用 Python 时如何使用数据结构，请按照此快速入门操作：

> [!div class="nextstepaction"]
> [快速入门：在 SQL Server 机器学习服务中使用 Python 处理数据结构和对象](quickstart-python-data-structures.md)

