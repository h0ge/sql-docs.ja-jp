---
title: setAsciiStream メソッド (SQLServerClob) |Microsoft ドキュメント
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
- SQLServerClob.setAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6e1779df-3b2a-41d1-8dca-99692cc9da14
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9da84141139b9bb6b0902fddab871fb8c5be0189
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841177"
---
# <a name="setasciistream-method-sqlserverclob"></a>setAsciiStream メソッド (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ASCII 文字を CLOB の指定された位置から書き込むために使用するストリームを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pos*  
  
 CLOB オブジェクトへの書き込みを開始する位置です。  
  
## <a name="return-value"></a>戻り値  
 ASCII エンコードされた文字のストリームを書き込むことができます。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この setAsciiStream メソッドは、java.sql.Clob インターフェイスの setAsciiStream メソッドによって指定されます。  
  
 CLOB の文字データは、開始位置から指定された出力ストリームによって上書きされ、CLOB の初期の長さをオーバーランすることができます。 位置 + 1 の値を指定すると、ASCII 文字が追加されます。 開始位置に CLOB の長さ + 2 以上 (または 0 以下) の値を指定すると、位置エラーがスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
