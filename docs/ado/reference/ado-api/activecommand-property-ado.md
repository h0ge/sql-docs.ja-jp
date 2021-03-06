---
title: ActiveCommand プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8aa86180edc4117e89863bb232a2faa95d010272
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="activecommand-property-ado"></a>ActiveCommand プロパティ (ADO)
示します、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)を作成した、関連付けられているオブジェクト[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**バリアント**を格納している、**コマンド**オブジェクト。 既定値は、null オブジェクト参照です。  
  
## <a name="remarks"></a>解説  
 **ActiveCommand**プロパティは読み取り専用です。  
  
 場合、**コマンド**オブジェクトが、現在の作成に使用されなかった**Recordset**、 **Null**オブジェクト参照が返されます。  
  
 このプロパティを使用して、関連付けられている検索**コマンド**オブジェクトの結果のみが指定されると**Recordset**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ActiveCommand プロパティの例 (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [ActiveCommand プロパティの例 (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [ActiveCommand プロパティの例 (vc++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
