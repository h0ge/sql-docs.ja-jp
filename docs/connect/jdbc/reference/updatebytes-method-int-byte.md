---
title: updateBytes メソッド (int, byte) |Microsoft ドキュメント
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
- SQLServerResultSet.updateBytes (int, byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 625f48ba-53d0-45a6-8fcb-643f1e0cbe8a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbdada667e3e3c5e35eb64edc56c2772ae465f80
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32848967"
---
# <a name="updatebytes-method-int-byte"></a>updateBytes (int, byte) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  配列で指定された列を更新**バイト**列インデックスの値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBytes(int index,  
                        byte[] x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 列インデックスを示す **int** です。  
  
 *x*  
  
 配列**バイト**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateBytes メソッドは、java.sql.ResultSet インターフェイスの updateBytes メソッドによって指定されます。  
  
 以前のバージョンで[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]、SQLServerResultSet.updateBytes を使用してバイト配列間の変換と[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型**日付**、**時間**、 **datetime2**、または**datetimeoffset**です。 新しいバージョンでは、これらのデータ型に対してこのメソッドを使用すると、変換がサポートされていないことを示す例外が発生します。  
  
## <a name="see-also"></a>参照  
 [updateBytes メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
