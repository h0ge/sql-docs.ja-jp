---
title: 序数 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83036ec2ee0fa69c9ebb8cc2a905361eeae0aafa
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742671"
---
# <a name="ordinal-mdx"></a>Ordinal (MDX)


  レベルに関連付けられた 0 から始まる序数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **序数**と共にで頻繁に使用される関数、 **IIF**と**CurrentMember**クエリ結果内の特定の各セルの序数位置に基づいて、条件付きで別の階層レベルで異なる値を表示する関数。 たとえば、使用することができます、**序数**関数を特定のレベルで計算を実行し、その他のレベルで、既定値は"N/A"を表示します。  
  
## <a name="example"></a>例  
 次の例では、Calendar 階層内の Calendar Quarter レベルの序数が返されます。  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
