---
title: ADO NET カスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d16d06518a5b58f768f4e87a4361d99b3e2796af
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ado-net-custom-properties"></a>ADO NET カスタム プロパティ
  **変換元のカスタム プロパティ**  
  
 ADO NET ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、ADO NET ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|CommandTimeOut|String|SQL コマンドがタイムアウトになる時間を秒数で指定する値です。値が 0 の場合、コマンドはタイムアウトになりません。|  
|SqlCommand|String|ADO NET ソースがデータの抽出に使用する SQL ステートメントです。<br /><br /> パッケージを読み込むときに、ADO NET ソースが使用する SQL ステートメントでこのプロパティを動的に更新できます。 詳しくは、「[Integration Services &#40;SSIS&#41; の式](../../integration-services/expressions/integration-services-ssis-expressions.md)」および「[パッケージでプロパティ式を使用する](../../integration-services/expressions/use-property-expressions-in-packages.md)」をご覧ください。|  
|AllowImplicitStringConversion|ブール値|次の処理を実行するかどうかを示す値です。<br /><br /> - 外部メタデータの型と文字列型である出力列の型が一致しない場合に、検証エラーを生成しない (DT_WSTR または DT_NTEXT)。<br /><br /> - 外部メタデータの型を、出力列が使用する文字列データ型に暗黙的に変換する。<br /><br /> <br /><br /> 既定値は TRUE です。<br /><br /> 詳しくは、「 [ADO NET ソース](../../integration-services/data-flow/ado-net-source.md)」をご覧ください。|  
  
 ADO NET ソースの出力および出力列には、カスタム プロパティがありません。  
  
 詳しくは、「 [ADO NET ソース](../../integration-services/data-flow/ado-net-source.md)」をご覧ください。  
  
 **変換先のカスタム プロパティ**  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントに共通するプロパティの両方があります。  
  
 次の表は、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。 これらのプロパティは、 **[ADO.NET 変換先エディター]** ではアクセスできませんが、 **[詳細エディター]** を使用して設定できます。  
  
|プロパティ|データ型|Description|  
|--------------|---------------|-----------------|  
|BatchSize|Integer|サーバーに送信されるバッチ内の行数です。 値 **0** は、バッチ サイズが内部バッファーのサイズに一致することを示します。 このプロパティの既定値は **0**です。|  
|CommandTimeOut|Integer|SQL コマンドがタイムアウトになるまでの最大秒数。この値に **0** を指定すると、時間は無制限になります。 このプロパティの既定値は **0**です。|  
|TableOrViewName|String|変換先のテーブルまたはビューの名前。|  
  
 詳しくは、「 [ADO NET 変換先](../../integration-services/data-flow/ado-net-destination.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
