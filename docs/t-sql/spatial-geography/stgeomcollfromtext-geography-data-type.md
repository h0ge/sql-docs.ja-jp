---
title: "STGeomCollFromText (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STGeomCollFromText_TSQL
- STGeomCollFromText (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromText method
ms.assetid: a5b3c344-1045-43a4-82fa-47f6206a288e
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f20e9259aad1f2a4ca87c8a684157b93c44b8b59
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stgeomcollfromtext-geography-data-type"></a>STGeomCollFromText (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **geography**いる Z (標高) 値および M (メジャー) 値で補完された、Open Geospatial Consortium (OGC) Well-Known Text (WKT) 表現からのインスタンスがインスタンスで実行します。
  
## <a name="syntax"></a>構文  
  
```  
  
STGeomCollFromText ( 'geometrycollection_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *geometrycollection_tagged_text*  
 WKT 表現です、 **geography**インスタンスを取得します。 *geometrycollection_tagged_text*は、 **nvarchar (max)**式。  
  
 *SRID*  
 **Int** 、空間を表す式の ID (SRID) を参照、 **geography**インスタンスを取得します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 OGC の型の**geography** STGeomCollFromText() によって返されるインスタンスが、対応する WKT 入力に設定します。  
  
 このメソッドは、 **ArgumentException**場合は、入力が無効です。  
  
## <a name="examples"></a>使用例  
 次の例で`STGeomCollFromText()`を作成する、`geography`インスタンス。  
  
```  
DECLARE @g geography;  
DECLARE @g geography;  
SET @g = geography::STGeomCollFromText('GEOMETRYCOLLECTION ( POINT(-122.34900 47.65100), LINESTRING(-122.360 47.656, -122.343 47.656) )', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的な地理メソッド](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
