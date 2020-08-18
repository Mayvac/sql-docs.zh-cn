---
description: 异步执行（通知方法）
title: 异步执行 (通知方法) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19c201d71d42c40277ad67cef25922e55e97de12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483120"
---
# <a name="asynchronous-execution-notification-method"></a>异步执行（通知方法）
ODBC 允许执行连接和语句操作的异步执行。 应用程序线程可以在异步模式下调用 ODBC 函数，并且该函数可以在操作完成之前返回，从而允许应用程序线程执行其他任务。 在 Windows 7 SDK 中，对于异步语句或连接操作，应用程序确定使用轮询方法完成了异步操作。 有关详细信息，请参阅 [异步执行 (轮询方法) ](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)。 从 Windows 8 SDK 开始，你可以使用通知方法确定异步操作是否已完成。  
  
 在轮询方法中，应用程序需要在每次需要此操作的状态时调用异步函数。 通知方法类似于回调并等待 ADO.NET。 不过，ODBC 使用 Win32 事件作为通知对象。  
  
 不能同时使用 ODBC 游标库和 ODBC 异步通知。 设置这两个属性将返回一个错误，其中包含 SQLSTATE S1119 (游标库，并且无法同时启用异步通知) 。  
  
 有关驱动程序开发人员的信息，请参阅 [异步函数完成通知](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) 。  
  
> [!NOTE]  
>  游标库不支持通知方法。 如果启用了通知方法，则应用程序将在尝试通过 SQLSetConnectAttr 启用游标库时收到错误消息。  
  
## <a name="overview"></a>概述  
 在异步模式下调用 ODBC 函数时，控件将立即返回到调用应用程序，SQL_STILL_EXECUTING 返回代码。 应用程序必须重复轮询函数，直到它返回 SQL_STILL_EXECUTING 以外的内容。 轮询循环增加了 CPU 使用率，在许多异步方案中导致性能不佳。  
  
 无论何时使用通知模型，都会禁用轮询模型。 应用程序不应再次调用原始函数。 调用 [SQLCompleteAsync 函数](../../../odbc/reference/syntax/sqlcompleteasync-function.md) 以完成异步操作。 如果应用程序在异步操作完成之前再次调用原始函数，则调用将返回 SQL_ERROR 与 SQLSTATE IM017 (在异步通知模式下) 禁用轮询。  
  
 使用通知模型时，应用程序可以调用 **SQLCancel** 或 **SQLCancelHandle** 来取消语句或连接操作。 如果取消请求成功，ODBC 将返回 SQL_SUCCESS。 此消息不表示该函数实际上已被取消;它指示已处理取消请求。 函数是否实际被取消取决于驱动程序和数据源的依赖项。 取消操作时，驱动程序管理器仍将发出事件信号。 驱动程序管理器返回 SQL_ERROR 在返回代码缓冲区中，状态为 "已取消" (操作) ，以指示取消操作成功。 如果该函数完成了其正常处理，则驱动程序管理器将返回 SQL_SUCCESS 或 SQL_SUCCESS_WITH_INFO。  
  
### <a name="downlevel-behavior"></a>下层行为  
 在完成时，支持此通知的 ODBC 驱动程序管理器版本为 ODBC 3.81。  
  
|应用程序 ODBC 版本|驱动程序管理器版本|驱动程序版本|行为|  
|------------------------------|----------------------------|--------------------|--------------|  
|任何 ODBC 版本的新应用程序|ODBC 3.81|ODBC 3.80 驱动程序|如果驱动程序支持此功能，则应用程序可以使用此功能，否则，驱动程序管理器将会出现错误。|  
|任何 ODBC 版本的新应用程序|ODBC 3.81|ODBC 之前3.80 驱动程序|如果驱动程序不支持此功能，驱动程序管理器将会出现错误。|  
|任何 ODBC 版本的新应用程序|ODBC 之前3.81|Any|当应用程序使用此功能时，旧的驱动程序管理器会将新属性视为驱动程序特定的属性，并且驱动程序应该会出现错误。新的驱动程序管理器不会将这些属性传递给驱动程序。|  
  
 在使用此功能之前，应用程序应检查驱动程序管理器版本。 否则，如果编写不良的驱动程序未出现错误，并且驱动程序管理器版本是预 ODBC 3.81，则行为是不确定的。  
  
## <a name="use-cases"></a>用例  
 本部分介绍异步执行和轮询机制的用例。  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>集成来自多个 ODBC 源的数据  
 数据集成应用程序以异步方式从多个数据源中提取数据。 某些数据来自远程数据源，某些数据来自本地文件。 在异步操作完成之前，应用程序无法继续。  
  
 应用程序可以创建事件对象并将其与 ODBC 连接句柄或 ODBC 语句句柄相关联，而不是重复轮询操作来确定是否已完成。 然后，应用程序会调用操作系统同步 Api，以等待一个事件对象或多个事件对象 (ODBC 事件和其他 Windows 事件) 。 当相应的 ODBC 异步操作完成时，ODBC 将发出事件对象信号。  
  
 在 Windows 上，将使用 Win32 事件对象，并为用户提供统一的编程模型。 其他平台上的驱动程序管理器可以使用特定于这些平台的事件对象实现。  
  
 下面的代码示例演示如何使用连接和语句异步通知：  
  
```  
// This function opens NUMBER_OPERATIONS connections and executes one query on statement of each connection.  
// Asynchronous Notification is used  
  
#define NUMBER_OPERATIONS 5  
int AsyncNotificationSample(void)  
{  
    RETCODE     rc;  
  
    SQLHENV     hEnv              = NULL;  
    SQLHDBC     arhDbc[NUMBER_OPERATIONS]         = {NULL};  
    SQLHSTMT    arhStmt[NUMBER_OPERATIONS]        = {NULL};  
  
    HANDLE      arhDBCEvent[NUMBER_OPERATIONS]    = {NULL};  
    RETCODE     arrcDBC[NUMBER_OPERATIONS]        = {0};  
    HANDLE      arhSTMTEvent[NUMBER_OPERATIONS]   = {NULL};  
    RETCODE     arrcSTMT[NUMBER_OPERATIONS]       = {0};  
  
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &hEnv);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    rc = SQLSetEnvAttr(hEnv,  
        SQL_ATTR_ODBC_VERSION,  
        (SQLPOINTER) SQL_OV_ODBC3_80,  
        SQL_IS_INTEGER);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    // Connection operations begin here  
  
    // Alloc NUMBER_OPERATIONS connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_DBC, hEnv, &arhDbc[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable DBC Async on all connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE, (SQLPOINTER)SQL_ASYNC_DBC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Application must create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhDBCEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhDBCEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all connection handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_EVENT, arhDBCEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate connect establishing  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLDriverConnect(arhDbc[i], NULL, (SQLTCHAR*)TEXT("Driver={ODBC Driver 11 for SQL Server};SERVER=dp-srv-sql2k;DATABASE=pubs;UID=sa;PWD=XYZ;"), SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE); // Wait All  
  
    // Complete connect API calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], & arrcDBC[i]);  
    }  
  
    BOOL fFail = FALSE; // Whether some connection openning fails.  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcDBC[i]) )   
            fFail = TRUE;  
    }  
  
    // If some SQLDriverConnect() fail, clean up.  
    if (fFail)  
    {  
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {  
                SQLDisconnect(arhDbc[i]); // This is also async  
            }  
            else  
            {  
                SetEvent(arhDBCEvent[i]); // Previous SQLDriverConnect() failed. No need to call SQLDisconnect().  
            }  
        }  
        WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE);   
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {     
                SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], &arrcDBC[i]);; // To Complete  
            }  
        }  
  
        goto Cleanup;  
    }  
  
    // Statement Operations begin here  
  
    // Alloc statement handle  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_STMT, arhDbc[i], &arhStmt[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable STMT Async on all statement handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_ENABLE, (SQLPOINTER)SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhSTMTEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhSTMTEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all statement handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_STMT_EVENT, arhSTMTEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate SQLExecDirect() calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLExecDirect(arhStmt[i], (SQLTCHAR*)TEXT("select au_lname, au_fname from authors"), SQL_NTS);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE); // Wait All  
  
    // Now, call SQLCompleteAsync to complete the operation and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return values  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        //Do some binding jobs here, set SQL_ATTR_ROW_ARRAY_SIZE   
    }  
  
    // Now, initiate fetching  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLFetch(arhStmt[i]);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE);   
  
    // Now, to complete the operations and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    // USE fetched data here!!  
  
Cleanup:  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhStmt[NUMBER_OPERATIONS])  
        {  
            SQLFreeHandle(SQL_HANDLE_STMT, arhStmt[i]);  
            arhStmt[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhSTMTEvent[i])  
        {  
            CloseHandle(arhSTMTEvent[i]);  
            arhSTMTEvent[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDbc[i])  
        {  
            SQLFreeHandle(SQL_HANDLE_DBC, arhDbc[i]);  
            arhDbc[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDBCEvent[i])  
        {  
            CloseHandle(arhDBCEvent[i]);  
            arhDBCEvent[i] = NULL;  
        }  
    }  
  
    if (hEnv)  
    {  
        SQLFreeHandle(SQL_HANDLE_ENV, hEnv);  
        hEnv = NULL;  
    }  
  
    return 0;  
}  
  
```  
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>确定驱动程序是否支持异步通知  
 ODBC 应用程序可以通过调用 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)来确定 odbc 驱动程序是否支持异步通知。 ODBC 驱动程序管理器会将驱动程序的 **SQLGetInfo** 调用 SQL_ASYNC_NOTIFICATION。  
  
```  
SQLUINTEGER InfoValue;  
SQLLEN      cbInfoLength;  
  
SQLRETURN retcode;  
retcode = SQLGetInfo (hDbc,   
                      SQL_ASYNC_NOTIFICATION,   
                      &InfoValue,  
                      sizeof(InfoValue),  
                      NULL);  
if (SQL_SUCCEEDED(retcode))  
{  
if (SQL_ASYNC_NOTIFICATION_CAPABLE == InfoValue)  
      {  
          // The driver supports asynchronous notification  
      }  
      else if (SQL_ASYNC_NOTIFICATION_NOT_CAPABLE == InfoValue)  
      {  
          // The driver does not support asynchronous notification  
      }  
}  
```  
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>将 Win32 事件句柄与 ODBC 句柄相关联  
 应用程序负责使用相应的 Win32 函数创建 Win32 事件对象。 应用程序可以将一个 Win32 事件句柄与一个 ODBC 连接句柄或一个 ODBC 语句句柄关联起来。  
  
 连接属性 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 和 SQL_ATTR_ASYNC_DBC_EVENT 确定 ODBC 是否在异步模式下执行以及 ODBC 是否为连接句柄启用通知模式。 语句特性 SQL_ATTR_ASYNC_ENABLE 和 SQL_ATTR_ASYNC_STMT_EVENT 确定 ODBC 是否在异步模式下执行以及 ODBC 是否启用语句句柄的通知模式。  
  
|SQL_ATTR_ASYNC_ENABLE 或 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT 或 SQL_ATTR_ASYNC_DBC_EVENT|“模式”|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|启用|非 null|异步通知|  
|启用|null|异步轮询|  
|禁用|any|同步|  
  
 应用程序可以暂时禁用异步操作模式。 如果禁用连接级别的异步操作，ODBC 将忽略 SQL_ATTR_ASYNC_DBC_EVENT 的值。 如果禁用了语句级别的异步操作，ODBC 将忽略 SQL_ATTR_ASYNC_STMT_EVENT 的值。  
  
 同步调用 **SQLSetStmtAttr** 和 **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** 支持异步操作，但是调用 **SQLSetConnectAttr** 以设置 SQL_ATTR_ASYNC_DBC_EVENT 始终是同步的。  
  
-   **SQLSetStmtAttr** 不支持异步执行。  
  
 错误出方案  
 在建立连接之前调用 **SQLSetConnectAttr** 时，驱动程序管理器无法确定要使用的驱动程序。 因此，驱动程序管理器会为 **SQLSetConnectAttr** 返回 success，但可能无法在驱动程序中设置该属性。 当应用程序调用连接函数时，驱动程序管理器会设置这些属性。 驱动程序管理器可能出现错误，因为驱动程序不支持异步操作。  
  
 连接属性的继承  
 通常，连接的语句将继承连接属性。 但 SQL_ATTR_ASYNC_DBC_EVENT 的属性不可继承，只会影响连接操作。  
  
 若要将事件句柄与 ODBC 连接句柄相关联，ODBC 应用程序将调用 ODBC API **SQLSetConnectAttr** ，并将 SQL_ATTR_ASYNC_DBC_EVENT 指定为属性，并将事件句柄指定为属性值。 新的 ODBC 特性 SQL_ATTR_ASYNC_DBC_EVENT 的类型 SQL_IS_POINTER。  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 通常，应用程序会创建自动重置事件对象。 ODBC 不会重置事件对象。 在调用任何异步 ODBC 函数之前，应用程序必须确保对象未处于终止状态。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT 是驱动程序管理器的唯一属性，将不会在驱动程序中设置。  
  
 SQL_ATTR_ASYNC_DBC_EVENT 的默认值为 NULL。 如果该驱动程序不支持异步通知，则获取或设置 SQL_ATTR_ASYNC_DBC_EVENT 将返回 SQL_ERROR 与 SQLSTATE HY092 (无效的属性/选项标识符) 。  
  
 如果在 ODBC 连接句柄上设置的最后一个 SQL_ATTR_ASYNC_DBC_EVENT 值不为 NULL，并且通过使用 SQL_ASYNC_DBC_ENABLE_ON 设置特性 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 来启用应用程序的异步模式，则调用支持异步模式的任何 ODBC 连接函数将获得完成通知。 如果 ODBC 连接句柄上设置的最后一个 SQL_ATTR_ASYNC_DBC_EVENT 值为 NULL，则无论是否启用异步模式，ODBC 都不会向应用程序发送任何通知。  
  
 应用程序可以在设置属性 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 之前或之后设置 SQL_ATTR_ASYNC_DBC_EVENT。  
  
 应用程序可以在调用连接函数 (**SQLConnect**、 **SQLBrowseConnect**或 **SQLDriverConnect**) 之前设置 ODBC 连接句柄上的 SQL_ATTR_ASYNC_DBC_EVENT 属性。 由于 ODBC 驱动程序管理器不知道应用程序将使用哪个 ODBC 驱动程序，它将返回 SQL_SUCCESS。 当应用程序调用连接函数时，ODBC 驱动程序管理器将检查驱动程序是否支持异步通知。 如果驱动程序不支持异步通知，ODBC 驱动程序管理器将返回 SQL_ERROR 与 SQLSTATE S1_118 (驱动程序不支持异步通知) 。 如果驱动程序支持异步通知，ODBC 驱动程序管理器将调用该驱动程序，并 SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK 和 SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT 设置相应的属性。  
  
 同样，应用程序对 ODBC 语句句柄调用 **SQLSetStmtAttr** ，并指定 SQL_ATTR_ASYNC_STMT_EVENT 属性以启用或禁用语句级别的异步通知。 由于在建立连接后始终调用语句函数，因此，如果相应的驱动程序不支持异步操作或驱动程序支持异步操作，但不支持异步通知，则 **SQLSetStmtAttr** 将返回 SQL_ERROR 与 SQLSTATE S1_118 (驱动程序不支持异步通知) 。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT （可设置为 NULL）是一个仅限驱动程序管理器的属性，将不会在驱动程序中设置。  
  
 SQL_ATTR_ASYNC_STMT_EVENT 的默认值为 NULL。 如果驱动程序不支持异步通知，则获取或设置 SQL_ATTR_ASYNC_ STMT_EVENT 属性将返回 SQL_ERROR SQLSTATE HY092 (无效的属性/选项标识符) 。  
  
 应用程序不应将同一个事件句柄与多个 ODBC 句柄相关联。 否则，如果两个异步 ODBC 函数调用在共享同一事件句柄的两个句柄上完成，则会丢失一个通知。 若要避免语句句柄继承连接句柄中的同一事件句柄，ODBC 将返回 SQL_ERROR 与 SQLSTATE IM016 (如果应用程序在连接句柄上设置 SQL_ATTR_ASYNC_STMT_EVENT，则不能将语句特性设置为连接句柄) 。  
  
### <a name="calling-asynchronous-odbc-functions"></a>调用异步 ODBC 函数  
 启用异步通知并启动异步操作后，应用程序可以调用任何 ODBC 函数。 如果函数属于支持异步操作的函数集，则无论函数是失败还是成功，应用程序都将在操作完成时获得完成通知。  唯一的例外是应用程序调用的 ODBC 函数的连接或语句句柄无效。 在这种情况下，ODBC 不会获取事件句柄并将其设置为终止状态。  
  
 在对相应的 ODBC 句柄开始异步操作之前，应用程序必须确保关联的事件对象处于非终止状态。 ODBC 不会重置事件对象。  
  
### <a name="getting-notification-from-odbc"></a>从 ODBC 获取通知  
 应用程序线程可以调用 **WaitForSingleObject** 来等待一个事件句柄，或调用 **WaitForMultipleObjects** 以等待事件句柄的数组，并在一个或所有事件对象终止或超时间隔结束之前挂起。  
  
```  
DWORD dwStatus = WaitForSingleObject(  
                        hEvent,  // The event associated with the ODBC handle  
                        5000     // timeout is 5000 millisecond   
);  
  
If (dwStatus == WAIT_TIMEOUT)  
{  
    // time-out interval elapsed before all the events are signaled.   
}  
Else  
{  
    // Call the corresponding Asynchronous ODBC API to complete all processing and retrieve the return code.  
}  
```
