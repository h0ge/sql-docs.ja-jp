---
title: EmptyResult データ型 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7155c03203ad852573318056ab4e194fe19e7113
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573904"
---
# <a name="emptyresult-data-type-xmla"></a>EmptyResult データ型 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  表す派生データ型を定義、[ルート](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)要素からデータを返さない、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-分析: 空  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[結果セット](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
|派生要素|[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 XML for Analysis (XMLA) コマンドの中には、結果を返さないものや、エラーのために結果を返すことができないものがあります。 結果を返さない XMLA コマンドを返す、 **EmptyResult**データ型、上の名前空間、**ルート**要素。  
  
## <a name="example"></a>例  
 次の例を表す、**ルート**空の結果の要素が返されます。  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>参照
 [XML データ型&#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
