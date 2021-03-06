---
title: sqlsrv_get_field |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_get_field
apitype: NA
helpviewer_keywords:
- sqlsrv_get_field
- API Reference, sqlsrv_get_field
- retrieving data, as a single field
ms.assetid: fa17cc56-fb38-433b-a40d-65642f04dc23
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8aea71596e1a977839fb7294df7324f48324e0c3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvgetfield"></a>sqlsrv_get_field
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

現在の行の指定したフィールドからデータを取得します。 フィールドのデータには、順にアクセスする必要があります。 たとえば、2 つ目のフィールドのデータにアクセスした後に、1 つ目のフィールドのデータにアクセスすることはできません。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_get_field( resource $stmt, int $fieldIndex [, int $getAsType])  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: 実行されたステートメントに対応するステートメント リソースです。  
  
*$fieldIndex*: 取得するフィールドのインデックス。 インデックスは 0 から始まります。  
  
*$getAsType* [省略可能]: A **SQLSRV**定数 (**sqlsrv_phptype _\***) 返されたデータの PHP データ型を決定します。 サポートされているデータ型については、次を参照してください。[定数&#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)です。 戻り値の型が指定されていない場合、既定の PHP 型が返されます。 既定の PHP 型の詳細については、「 [Default PHP Data Types](../../connect/php/default-php-data-types.md)」を参照してください。 PHP データ型の指定については、「 [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md)」を参照してください。  
  
## <a name="return-value"></a>戻り値  
フィールドのデータ。 *$getAsType* パラメーターを指定して、返されるデータの PHP データ型を指定できます。 戻り値のデータ型が指定されていない場合、既定の PHP データ型が返されます。 既定の PHP 型の詳細については、「 [Default PHP Data Types](../../connect/php/default-php-data-types.md)」を参照してください。 PHP データ型の指定については、「 [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
組み合わせ**sqlsrv_fetch**と**sqlsrv_get_field**データへの前方参照専用のアクセスを提供します。  
  
組み合わせ**sqlsrv_fetch**/**sqlsrv_get_field**結果のフィールドを 1 つだけがスクリプト メモリに行を設定し、php の負荷が型の仕様を返します。 (PHP 戻り値の型を指定する方法については、次を参照してください[する方法: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md)。)。また、この関数の組み合わせで、データをストリームとして取得することもできます (データをストリームとして取得する方法の詳細については、次を参照してください[SQLSRV ドライバーを使用して、ストリームとしてデータの取得](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)。)。  
  
## <a name="example"></a>例  
次の例では、製品のレビューとレビュアー名を含むデータの行を取得します。 結果セットからデータを取得するには、 **sqlsrv_get_field** を使用します。 例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up and execute the query. Note that both ReviewerName and  
Comments are of the SQL Server nvarchar type. */  
$tsql = "SELECT ReviewerName, Comments   
         FROM Production.ProductReview  
         WHERE ProductReviewID=1";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Make the first row of the result set available for reading. */  
if( sqlsrv_fetch( $stmt ) === false )  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Note: Fields must be accessed in order.  
Get the first field of the row. Note that no return type is  
specified. Data will be returned as a string, the default for  
a field of type nvarchar.*/  
$name = sqlsrv_get_field( $stmt, 0);  
echo "$name: ";  
  
/*Get the second field of the row as a stream.  
Because the default return type for a nvarchar field is a  
string, the return type must be specified as a stream. */  
$stream = sqlsrv_get_field( $stmt, 1,   
                            SQLSRV_PHPTYPE_STREAM( SQLSRV_ENC_CHAR));  
while( !feof( $stream))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  

[データの取得](../../connect/php/retrieving-data.md)  

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
