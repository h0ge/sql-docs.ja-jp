---
title: "REVERSE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERSE_TSQL
- REVERSE
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], reverse
- REVERSE function
- reverse character expressions
ms.assetid: 555d8877-7cc7-4955-ae2c-6215aca313b7
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8696a2cff3589b9b756e2ddd9cc1160b465b70d8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="reverse-transact-sql"></a>REVERSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  文字列値を逆に並べ替えたものを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
REVERSE ( string_expression )  
```  
  
## <a name="arguments"></a>引数  
 *string_expression*  
 *string_expression*は、[式](../../t-sql/language-elements/expressions-transact-sql.md)文字列またはバイナリ データ型。 *string_expression*定数、変数、または文字またはバイナリ データのいずれかの列を指定できます。  
  
## <a name="return-types"></a>戻り値の型  
 **varchar**または**nvarchar**  
  
## <a name="remarks"></a>解説  
 *string_expression*に暗黙的に変換できるデータ型でなければなりません**varchar**です。 それ以外の場合、使用[キャスト](../../t-sql/functions/cast-and-convert-transact-sql.md)明示的に変換する*string_expression*です。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 SC 照合順序を使用すると、REVERSE 関数は、サロゲート ペアの 2 つの要素の順序を逆にしません。  
  
## <a name="examples"></a>使用例  
 次の例では、すべての連絡先の名前の文字を、逆に並べ替えて返します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
SELECT FirstName, REVERSE(FirstName) AS Reverse  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `FirstName      Reverse`  
  
 `-------------- --------------`  
  
 `Ken            neK`  
  
 `Rob            boR`  
  
 `Roberto        otreboR`  
  
 `Terri          irreT`  
  
 `(4 row(s) affected)`  
  
 次の例では、変数内の文字列を逆に並べ替えます。  
  
```  
DECLARE @myvar varchar(10);  
SET @myvar = 'sdrawkcaB';  
SELECT REVERSE(@myvar) AS Reversed ;  
GO  
```  
  
 次の例は、暗黙の変換から、 **int**データの型を**varchar**データ型であり、結果を反転します。  
  
```  
SELECT REVERSE(1234) AS Reversed ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、すべてのデータベースの名前を取得し、文字で名前が取り消されました。  
  
```  
SELECT name, REVERSE(name) FROM sys.databases;  
GO  
```  
  
 次の例では、変数内の文字列を逆に並べ替えます。  
  
```  
DECLARE @myvar varchar(10);  
SET @myvar = 'sdrawkcaB';  
SELECT REVERSE(@myvar) AS Reversed ;  
GO  
```  
  
 次の例は、暗黙の変換から、 **int**データの型を**varchar**データ型であり、結果を反転します。  
  
```  
SELECT REVERSE(1234) AS Reversed ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

