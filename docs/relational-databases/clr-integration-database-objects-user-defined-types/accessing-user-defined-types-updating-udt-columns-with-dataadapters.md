---
title: 用 Dataadapter 更新 UDT 列 |Microsoft Docs
description: 通过使用 SqlClient 和 SqlDataAdapter 检索和修改数据，支持 SQL Server 数据库中的 Udt 的支持。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- ADO.NET [CLR integration]
- updating data [CLR integration]
- populating DataSet
- datasets [CLR integration]
- UDTs [CLR integration], ADO.NET
- updating UDT columns
- user-defined types [CLR integration], ADO.NET
- data adapters [CLR integration]
ms.assetid: 4489c938-ba03-4fdb-b533-cc3f5975ae50
author: rothja
ms.author: jroth
ms.openlocfilehash: 07b1dc9d3f7beca9f048ec0e367c33922e388f32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727834"
---
# <a name="accessing-user-defined-types---updating-udt-columns-with-dataadapters"></a>访问用户定义类型 - 使用 DataAdapter 更新 UDT 列
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  使用**SqlClient 和 SqlDataAdapter**检索和修改数据**时，支持**用户定义的类型（udt）和用户定义的类型（udt）。  
  
## <a name="populating-a-dataset"></a>填充数据集  
 您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 语句选择 UDT 列值，以便利用数据适配器填充数据集。 下面的示例假定您有一个使用以下结构定义的**点**表和一些示例数据。 以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将创建**Points**表并插入一些行。  
  
```  
CREATE TABLE dbo.Points (id int PRIMARY Key, p Point);  
  
INSERT INTO dbo.Points VALUES (1, CONVERT(Point, '1,3'));  
INSERT INTO dbo.Points VALUES (2, CONVERT(Point, '2,4'));  
INSERT INTO dbo.Points VALUES (3, CONVERT(Point, '3,5'));  
INSERT INTO dbo.Points VALUES (4, CONVERT(Point, '4,6'));  
GO  
```  
  
 以下 ADO.NET 代码片段检索有效的连接字符串，创建新的**SqlDataAdapter**，并使用**Points**表中的数据行填充**system.string。**  
  
```vb  
Dim da As New SqlDataAdapter( _  
    "SELECT id, p FROM dbo.Points", connectionString)  
Dim datTable As New DataTable("Points")  
da.Fill(datTable)  
```  
  
```csharp  
SqlDataAdapter da = new SqlDataAdapter(  
   "SELECT id, p FROM dbo.Points", connectionString);  
DataTable datTable = new DataTable("Points");  
da.Fill(datTable);  
```  
  
## <a name="updating-udt-data-in-a-dataset"></a>更新数据集中的 UDT 数据  
 您可以使用两种方法来更新**数据集中**的 UDT 列：  
  
-   为**SqlDataAdapter**对象提供自定义的**InsertCommand**、 **UpdateCommand**和**DeleteCommand**对象。  
  
-   使用命令生成器（**SqlClient. SqlCommandBuilder**）自动为您创建 INSERT、UPDATE 和 DELETE 命令。 若要进行冲突检测，请向包含 UDT 的表添加**时间戳**列（别名**rowversion**） [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 **Timestamp**数据类型允许您对表中的行进行版本标记，并且保证在数据库中是唯一的。 当更改表中的值时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为受此更改影响的行自动更新八个字节的二进制编号。  
  
 请注意，除非基础表中有**timestamp**列，否则**SqlCommandBuilder**不会将 UDT 视为冲突检测。 可以比较 UDT，也可以不比较，因此，当使用“比较原始值”选项生成命令时，不会在 WHERE 子句中包含 UDT。  
  
### <a name="example"></a>示例  
 下面的示例要求创建另一个包含**Point** UDT 列以及**时间戳**列的表。 这两个表用于说明如何创建自定义命令对象来更新数据，以及如何使用**时间戳**列更新。 运行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句以便另外创建一个表，并使用示例数据填充该表。  
  
```  
CREATE TABLE dbo.Points_ts (id int PRIMARY KEY, p Point, ts timestamp);  
  
INSERT INTO dbo.Points_ts (id, p) VALUES (1, CONVERT(Point, '1,3'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (2, CONVERT(Point, '2,4'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (3, CONVERT(Point, '3,5'));  
INSERT INTO dbo.Points_ts (id, p) VALUES (4, CONVERT(Point, '4,6'));  
```  
  
 以下 ADO.NET 示例具有两个方法：  
  
-   **UserProvidedCommands**，它演示了如何提供**InsertCommand**、 **UpdateCommand**和**DeleteCommand**对象，以便更新**Points**表中的**Point** UDT （不包含**时间戳**列）。  
  
-   **CommandBuilder**，它演示如何在包含**timestamp**列的**Points_ts**表中使用**SqlCommandBuilder** 。  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
    ' Retrieves the connection string  
    Private connString As String = GetConnectionString()  
  
    Sub Main()  
        UserProvidedCommands()  
        CommandBuilder()  
    End Sub  
  
    Private Sub UserProvidedCommands()  
        ' Create a new SqlDataAdapter  
        Dim da As New SqlDataAdapter( _  
          "SELECT id, p FROM dbo.Points", connString)  
  
        ' Setup the INSERT/UPDATE/DELETE commands  
        Dim idParam As SqlParameter  
        Dim pointParam As SqlParameter  
  
        da.InsertCommand = New SqlCommand( _  
          "INSERT INTO dbo.Points (id, p) VALUES (@id, @p)", _  
          da.SelectCommand.Connection)  
        idParam = da.InsertCommand.Parameters.Add( _  
          "@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
        pointParam = da.InsertCommand.Parameters.Add( _  
          "@p", SqlDbType.Udt)  
        pointParam.SourceColumn = "p"  
        pointParam.UdtTypeName = "dbo.Point"  
  
        da.UpdateCommand = New SqlCommand( _  
          "UPDATE dbo.Points SET p = @p WHERE id = @id", _  
          da.SelectCommand.Connection)  
        idParam = _  
           da.UpdateCommand.Parameters.Add("@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
        pointParam = da.UpdateCommand.Parameters.Add( _  
          "@p", SqlDbType.Udt)  
        pointParam.SourceColumn = "p"  
        pointParam.UdtTypeName = "dbo.Point"  
  
        da.DeleteCommand = New SqlCommand( _  
          "DELETE dbo.Points WHERE id = @id", _  
          da.SelectCommand.Connection)  
        idParam = da.DeleteCommand.Parameters.Add( _  
          "@id", SqlDbType.Int)  
        idParam.SourceColumn = "id"  
  
        ' Fill the DataTable with UDT rows  
        Dim datTable As New DataTable("Points")  
        da.Fill(datTable)  
  
        ' Display the contents of the p (Point) column  
        Dim r As DataRow  
        For Each r In datTable.Rows  
            Dim p As Point = CType(r(1), Point)  
            Console.WriteLine( _  
              "ID: {0}, x={1}, y={1}", r(0), p.X, p.Y)  
        Next r  
  
        ' Update a row if the DataTable has at least 1 row  
        If datTable.Rows.Count > 0 Then  
            Dim oldPoint As Point = _  
              CType(datTable.Rows(0)(1), Point)  
            datTable.Rows(0)(1) = _  
              New Point(oldPoint.X + 1, oldPoint.Y + 1)  
        End If  
  
        ' Delete the last row  
        If datTable.Rows.Count > 0 Then  
            ' If we have at least 1 row  
            datTable.Rows(1).Delete()  
        End If  
  
        ' Insert a row. This will fail if run twice  
        ' because 100 is a primary key value.  
        datTable.Rows.Add(100, New Point(100, 200))  
  
        ' Send the changes back to the database  
        da.Update(datTable)  
    End Sub  
  
    Private Sub CommandBuilder()  
        ' Create a new SqlDataAdapter  
        Dim da As New SqlDataAdapter( _  
          "SELECT id, ts, p FROM dbo.Points_ts", connString)  
  
        ' Select a few rows with UDTs from the database  
        Dim datTable As New DataTable("Points")  
        da.Fill(datTable)  
  
        ' Display the contents of the p (Point) column  
        Dim r As DataRow  
        For Each r In datTable.Rows  
            Dim p As Point = CType(r(2), Point)  
            Console.WriteLine( _  
              "ID: {0}, x={1}, y={1}", r(0), p.X, p.Y)  
        Next r  
  
        ' Update a row if DataTable has at least 1 row  
        If datTable.Rows.Count > 0 Then  
            Dim oldPoint As Point = _  
              CType(datTable.Rows(0)(2), Point)  
            datTable.Rows(0)(2) = _  
              New Point(oldPoint.X + 1, oldPoint.Y + 1)  
        End If  
  
        ' Delete the last row  
        If datTable.Rows.Count > 0 Then  
            ' if we have at least 1 row  
            datTable.Rows(1).Delete()  
        End If  
  
        ' Insert a row. This will fail if run twice  
        ' because 100 is a primary key value  
        datTable.Rows.Add(100, Nothing, New Point(100, 200))  
  
        ' Use the CommandBuilder to generate DML statements  
        Dim bld As New SqlCommandBuilder(da)  
        bld.ConflictDetection = ConflictOptions.CompareRowVersion  
  
        ' Send the changes back to the database  
        da.Update(datTable)  
    End Sub  
  
  Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,   
      ' you can retrieve it from a configuration file.  
     Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
       & "Integrated Security=SSPI"  
   End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
  {  
// Retrieves the connection string  
private string connString = GetConnectionString();  
  
static void Main()  
{  
        UserProvidedCommands();  
        CommandBuilder();  
 }  
    static void UserProvidedCommands()  
    {  
        // Create a new SqlDataAdapter  
        SqlDataAdapter da = new SqlDataAdapter(  
          "SELECT id, p FROM dbo.Points", connString);  
  
        // Setup the INSERT/UPDATE/DELETE commands  
        SqlParameter idParam;  
        SqlParameter pointParam;  
  
        da.InsertCommand = new SqlCommand(  
            "INSERT INTO dbo.Points (id, p) VALUES (@id, @p)",   
             da.SelectCommand.Connection);  
        idParam =   
            da.InsertCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
        pointParam =   
            da.InsertCommand.Parameters.Add("@p", SqlDbType.Udt);  
        pointParam.SourceColumn = "p";  
        pointParam.UdtTypeName = "dbo.Point";  
  
        da.UpdateCommand = new SqlCommand(  
            "UPDATE dbo.Points SET p = @p WHERE id = @id",   
            da.SelectCommand.Connection);  
        idParam =   
            da.UpdateCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
        pointParam =   
            da.UpdateCommand.Parameters.Add("@p", SqlDbType.Udt);  
        pointParam.SourceColumn = "p";  
        pointParam.UdtTypeName = "dbo.Point";   
  
        da.DeleteCommand = new SqlCommand(  
            "DELETE dbo.Points WHERE id = @id",   
            da.SelectCommand.Connection);  
        idParam =   
            da.DeleteCommand.Parameters.Add("@id", SqlDbType.Int);  
        idParam.SourceColumn = "id";  
  
        // Fill the DataTable with UDT rows  
        DataTable datTable = new DataTable("Points");  
        da.Fill(datTable);  
  
        // Display the contents of the p (Point) column  
        foreach(DataRow r in datTable.Rows)   
        {  
            Point p = (Point)r[1];  
            Console.WriteLine(  
                "ID: {0}, x={1}, y={1}", r[0], p.X, p.Y);  
        }  
  
        // Update a row if the DataTable has at least 1 row  
        if(datTable.Rows.Count > 0 )   
        {   
            Point oldPoint = (Point)datTable.Rows[0][1];  
            datTable.Rows[0][1] =   
                new Point(oldPoint.X+1, oldPoint.Y+1);  
        }  
  
        // Delete the last row  
        if(datTable.Rows.Count > 0 )   
        { // If we have at least 1 row  
            datTable.Rows[1].Delete();  
        }  
  
        // Insert a row. This will fail if run twice  
        // because 100 is a primary key value.  
        datTable.Rows.Add(100, new Point(100, 200));   
  
        // Send the changes back to the database  
        da.Update(datTable);  
    }  
  
    static void CommandBuilder()  
    {  
        // Create a new SqlDataAdapter  
        SqlDataAdapter da = new SqlDataAdapter(  
            "SELECT id, ts, p FROM dbo.Points_ts", connString);  
  
        // Select a few rows with UDTs from the database  
        DataTable datTable = new DataTable("Points");  
        da.Fill(datTable);  
  
        // Display the contents of the p (Point) column  
        foreach (DataRow r in datTable.Rows)  
        {  
            Point p = (Point)r[2];  
            Console.WriteLine(  
                "ID: {0}, x={1}, y={1}", r[0], p.X, p.Y);  
        }  
  
        // Update a row if DataTable has at least 1 row  
        if (datTable.Rows.Count > 0)  
        {   
            Point oldPoint = (Point)datTable.Rows[0][2];  
            datTable.Rows[0][2] =   
                new Point(oldPoint.X + 1, oldPoint.Y + 1);  
        }  
  
        // Delete the last row  
        if (datTable.Rows.Count > 0)  
        { // if we have at least 1 row  
            datTable.Rows[1].Delete();  
        }  
  
        // Insert a row. This will fail if run twice  
        // because 100 is a primary key value  
        datTable.Rows.Add(100, null, new Point(100, 200));   
  
        // Use the CommandBuilder to generate DML statements  
        SqlCommandBuilder bld = new SqlCommandBuilder(da);  
        bld.ConflictDetection = ConflictOptions.CompareRowVersion;  
  
        // Send the changes back to the database  
        da.Update(datTable);  
    }  
  
 static private string GetConnectionString()  
 {  
 // To avoid storing the connection string in your code,   
 // you can retrieve it from a configuration file.  
    return "Data Source=localhost;Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [在 ADO.NET 中访问用户定义类型](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
  
  
