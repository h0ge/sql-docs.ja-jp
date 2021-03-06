---
title: フィルター (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d740148052712a69a39e0de314496733b3b26a8b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740531"
---
# <a name="filter-mdx"></a>Filter (MDX)


  指定されたセットを検索条件に基づいて絞り込み、結果セットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Logical_Expression*  
 true または false に評価される有効な多次元式 (MDX) 論理式です。  
  
## <a name="remarks"></a>コメント  
 **フィルター**関数は、指定されたセット内の各組に対して指定された論理式を評価します。 論理式の評価が、指定されたセット内の各組で構成されるセットを返します**true**です。 評価される組がない場合**true**空のセットが返されます。  
  
 **フィルター**関数の動作と同様の方法で、 [IIf](../mdx/iif-mdx.md)関数。 **IIf**関数では、2 つのオプションの 1 つだけを返しますは MDX 論理式の評価に基づき、while、**フィルター**関数を指定した検索条件を満たす組のセットを返します。 実際には、**フィルター**関数が実行される`IIf(Logical_Expression, Set_Expression.Current, NULL)`セット、および返します内の組ごとに、その結果セットです。  
  
## <a name="examples"></a>使用例  
 次の例では、クエリの行軸で Filter 関数を使用して、Internet Sales Amount が 10,000 米ドルを超える日付のみを返す方法を示します。  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Filter 関数は、計算されるメンバーの定義内でも使用できます。 次の例は、の合計を返して、`Measures.[Order Quantity]`集計に含まれている 2003年の 9 か月の最初のメンバー、`Date`ディメンションから、 **Adventure Works**キューブ。 **PeriodsToDate**関数セット内の組の定義を**集計**関数は動作します。 **フィルター**関数は、前の期間の Reseller Sales Amount メジャーの値が小さいものに返される組を限定します。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
