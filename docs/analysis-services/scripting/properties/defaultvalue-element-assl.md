---
title: "DefaultValue 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DefaultValue Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DefaultValue
helpviewer_keywords:
- DefaultValue element
ms.assetid: 87e964a3-f317-46c3-98c7-b3621765c77b
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9477af89e608fbf45d10fbdca08e6a5cc8fac769
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="defaultvalue-element-assl"></a>DefaultValue 要素 (ASSL)
  関連付けられている読み取り専用の既定値を含む[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ServerProperty>  
   ...  
   <DefaultValue>   </DefaultValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|任意の simpleType|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素には、読み取り専用のインストールの既定値が含まれています、 **ServerProperty**の現在のインスタンスの[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 既定値はインスタンスによって指定され、通常は変更できません。  
  
 親に対応する要素**DefaultValue**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ServerProperty>します。  
  
## <a name="see-also"></a>参照  
 [ServerProperties 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)   
 [Server 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  