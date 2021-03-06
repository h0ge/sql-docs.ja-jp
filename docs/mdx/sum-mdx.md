---
title: Sum (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bdf003a65e6923acf2bbf5c17e93d412e2d194fa
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743271"
---
# <a name="sum-mdx"></a>Sum (MDX)


  指定されているセットに対して評価された数値式の合計を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Sum( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 有効な多次元式 (MDX) セット式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 数値式を指定した場合、この数値式がセットに対して評価されてから、合計が算出されます。 数値式を指定しなかった場合、指定したセットがセットのメンバーの現在のコンテキストで評価されてから、合計が算出されます。 SUM 関数を数値式ではない式に適用した場合、結果は不確定になります。  
  
> [!NOTE]  
>  Analysis Services では、数値セットの合計が計算される際、NULL 値は無視されます。  
  
## <a name="examples"></a>使用例  
 次の例では、2001 年と 2002 年を対象として、Product.Category 属性階層のすべてのメンバーに対する Reseller Sales Amount の合計を返しています。  
  
```  
WITH MEMBER Measures.x AS SUM  
   ( { [Date].[Calendar Year].&[2001]  
         , [Date].[Calendar Year].&[2002] }  
      , [Measures].[Reseller Sales Amount]  
    )  
SELECT Measures.x ON 0  
,[Product].[Category].Members ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、2002 年 7 月のインターネット販売にかかる運賃をその月の 20 日まで合計して返しています。  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 次の例は、WITH MEMBER キーワードおよび**合計**Geography ディメンション内の Country 属性階層の Canada と United States メンバーに対する Reseller Sales Amount メジャーの合計を格納する、メジャー ディメンションの計算されるメンバーを定義する関数。  
  
```  
WITH MEMBER Measures.NorthAmerica AS SUM   
      (  
         {[Geography].[Country].&[Canada]  
            , [Geography].[Country].&[United States]}  
       ,[Measures].[Reseller Sales Amount]  
      )  
SELECT {[Measures].[NorthAmerica]} ON 0,  
[Product].[Category].members ON 1  
FROM [Adventure Works]  
```  
  
 多くの場合、**合計**関数を併用、 **CURRENTMEMBER**関数または関数と同様に**YTD**階層の currentmember に応じて異なるセットを返します。 たとえば、次のクエリは、年度の初めから ROWS 軸に表示されている日付までのすべての日付の Internet Sales Amount メジャーの合計を返します。  
  
 `WITH MEMBER MEASURES.YTDSUM AS`  
  
 `SUM(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDSUM} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
