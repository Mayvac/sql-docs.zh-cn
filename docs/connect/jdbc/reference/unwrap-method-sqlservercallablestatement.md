---
title: unwrap 方法 (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cbbf2728-b8c8-4c35-875a-6e967c8285dc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0dc8ddf82859b8bf47853a3d72a7461567388b87
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "67995193"
---
# <a name="unwrap-method-sqlservercallablestatement"></a>unwrap 方法 (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回一个实现指定接口的对象，从而允许访问特定于 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 的方法。  
  
## <a name="syntax"></a>语法  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>parameters  
 iface   
  
 定义接口的类型为 T 的类  。  
  
## <a name="return-value"></a>返回值  
 实现指定接口的对象。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)方法由在 JDBC 4.0 规范中引入的 java.sql.Wrapper 接口定义。  
  
 应用程序可能需要访问特定于 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 的 JDBC API 扩展。 如果类公开供应商扩展，则 unwrap 方法支持对此对象扩展的公共类取消包装。  
  
 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) 实现自 [ISQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 扩展而来的 [ISQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)。 当此方法获调用时，对象会取消对下列类的包装：[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)、[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 和 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)。  
  
 有关详细信息，请参阅[包装器和接口](../../../connect/jdbc/wrappers-and-interfaces.md)。  
  
 下面的代码示例展示了如何通过使用 isWrapperFor 和 unwrap 方法，检查驱动程序扩展并调用供应商专用方法（如 [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) 和 [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)）。  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
    CallableStatement cstmt =   
       con.prepareCall("{call dbo.stored_proc_name(?, ?)}");  
  
    // The recommended way to access the JDBC   
    // Driver-specific methods is to use the JDBC 4.0 Wrapper   
    // functionality.   
    // The following code statements demonstrates how to use the   
    // isWrapperFor and unwrap methods  
    // to access the driver-specific response buffering methods.  
  
    if (cstmt.isWrapperFor(  
      com.microsoft.sqlserver.jdbc.SQLServerCallableStatement.class)) {  
     // The CallableStatement object can unwrap to   
     // SQLServerCallableStatement.  
     SQLServerCallableStatement SQLcstmt =   
     cstmt.unwrap(  
        com.microsoft.sqlserver.jdbc.SQLServerCallableStatement.class);  
     SQLcstmt.setResponseBuffering("adaptive");  
     System.out.println("Response buffering mode has been set to " +  
         SQLcstmt.getResponseBuffering());  
     }  
  
    if (cstmt.isWrapperFor(  
      com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement.class)) {  
      // The CallableStatement object can unwrap to   
      // SQLServerPreparedStatement.                    
      SQLServerPreparedStatement SQLpstmt =   
       cstmt.unwrap(  
       com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement.class);  
      SQLpstmt.setResponseBuffering("adaptive");  
      System.out.println("Response buffering mode has been set to " +  
          SQLpstmt.getResponseBuffering());  
    }  
    if (cstmt.isWrapperFor(  
      com.microsoft.sqlserver.jdbc.SQLServerStatement.class)) {  
  
      // The CallableStatement object can unwrap to SQLServerStatement.   
      SQLServerStatement SQLstmt =   
        cstmt.unwrap(  
        com.microsoft.sqlserver.jdbc.SQLServerStatement.class);  
      SQLstmt.setResponseBuffering("adaptive");  
      System.out.println("Response buffering mode has been set to " +  
      SQLstmt.getResponseBuffering());  
    }  
  }  
  catch (Exception e) {  
     e.printStackTrace();  
  }  
}   
```  
  
## <a name="see-also"></a>另请参阅  
 [isWrapperFor 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 类](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
