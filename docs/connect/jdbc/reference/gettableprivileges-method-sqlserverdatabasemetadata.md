---
title: getTablePrivileges メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getTablePrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0610d667-a16d-4201-a14b-0a40048911e1
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06a7bcc60d73aba7e0939d70224a765168738b64
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840325"
---
# <a name="gettableprivileges-method-sqlserverdatabasemetadata"></a>getTablePrivileges メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたカタログ、スキーマ、またはテーブル名のパターンで使用可能な、各テーブルのアクセス権の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getTablePrivileges(java.lang.String catalog,  
                                             java.lang.String schema,  
                                             java.lang.String table)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *catalog*  
  
 A**文字列**カタログ名を格納しています。 このパラメーターに null を指定すると、カタログ名を使用する必要はありません。  
  
 *schema*  
  
 A**文字列**スキーマ名のパターンを格納しています。 このパラメーターに null を指定すると、スキーマ名を使用する必要はありません。  
  
 *テーブル*  
  
 A**文字列**テーブル名のパターンを格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTablePrivileges メソッドは、java.sql.DatabaseMetaData インターフェイスの getTablePrivileges メソッドによって指定されます。  
  
 GetTablePrivileges メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**文字列**|カタログ名。|  
|TABLE_SCHEM|**文字列**|テーブル スキーマ名です。|  
|TABLE_NAME|**文字列**|テーブル名。|  
|GRANTOR|**文字列**|アクセス許可を与えるオブジェクトです。|  
|GRANTEE|**文字列**|アクセスを受け入れるオブジェクトです。|  
|PRIVILEGE|**文字列**|許可されたアクセスの種類です。|  
|IS_GRANTABLE|**文字列**|権限を与えられたユーザーが他のユーザーへのアクセスを許可できるかどうかを示します。|  
  
> [!NOTE]  
>  GetTablePrivileges メソッドによって返されるデータに関する詳細については、「sp_table_privileges (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例では、getTablePrivileges メソッド内の Person.Contact テーブルのアクセス権を使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetTablePrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTablePrivileges("AdventureWorks", "Person", "Contact");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
