---
title: "入力ストリームを長時間にメソッドの setBinaryStream |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d59c7327-c9dc-4e4f-9dff-19e1a3c62eb2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6abe3075cd884bdb69694bdf4072a5bcdad12ff0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setbinarystream-method-javalangstring-javaioinputstream-long"></a>setBinaryStream メソッド (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、指定された入力ストリームに設定します。入力ストリームは、指定されたバイト数を持ちます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setBinaryStream(java.lang.String parameterName,  
                            java.io.InputStream x,  
                            long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 A**文字列**パラメーターの名前を格納しています。  
  
 *x*  
  
 InputStream オブジェクト。  
  
 *length*  
  
 A**長い**バイト数の長さを示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setBinaryStream メソッドは、java.sql.CallableStatement インターフェイスの setBinaryStream メソッドによって指定されます。  
  
 ストリームの長さが指定されたものと異なるかどうか、*長さ*パラメーター、JDBC ドライバーと例外をスロー、行が更新または挿入します。  
  
 ストリームの長さが、不明の場合、*長さ*ドライバーがその長さに関係なく、ストリームを受け入れることを示すために、パラメーターを-1 に設定することがあります。 Sqljdbc4.jar、ことをお勧め、JDBC 4.0 メソッドを使用する[setBinaryStream (java.lang.String, java.io.InputStream) メソッド](../../../connect/jdbc/reference/setbinarystream-method-java-lang-string-java-io-inputstream.md)アプリケーションが列の長さが不明なストリームを更新するときにします。  
  
## <a name="see-also"></a>参照  
 [setBinaryStream & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  