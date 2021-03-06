---
title: 多次元モデル内のデータ ソース |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 149ac1e36eb07d40223ffc97fba1646932ab0093
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022829"
---
# <a name="data-sources-in-multidimensional-models"></a>多次元モデルのデータ ソース
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  多次元モデルにインポートするデータまたは読み込むデータは、すべて外部データ ソースから取得されます。 通常、ソース データはレポート生成用に設計されたデータ ウェアハウスから取得されますが、直接的または [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージなどを介して間接的にアクセスされるリレーショナル データベースから取得される場合もあります。  
  
 **の** データ ソース [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトでは、外部データ ソースへの直接接続を指定します。 物理的な場所だけでなく、接続文字列、データ プロバイダー、資格情報、および接続動作を制御する他のプロパティも指定します。  
  
 データ ソース オブジェクトによって提供される情報は、次の操作で使用されます。  
  
-   データ ソース ビューの生成に使用されるスキーマ情報とその他のメタデータのモデルへの取り込み  
  
-   処理中のクエリの実行またはモデルへのデータの読み込み  
  
-   ROLAP ストレージ モードを使用する多次元モデルまたはデータ マイニング モデルに対するクエリの実行  
  
-   リモート パーティションに対する読み取りまたは書き込み  
  
-   リンク オブジェクトへの接続と、ターゲットからソースへの同期  
  
-   リレーショナル データベースに格納されているファクト テーブル データを更新する書き戻し操作の実行  
  
 多次元モデルを最初から作成するときは、まずデータ ソース オブジェクトを作成します。次に、このオブジェクトを使用して、次のオブジェクト ( **データ ソース ビュー**) を生成します。 データ ソース ビューは、モデルのデータ抽象化レイヤーです。 通常は、ソース データベースのスキーマを基盤として使用して、データ ソース オブジェクトの後に作成されます。 ただし、他の方法でモデルを作成することもできます。たとえば、キューブとディメンションから作成する方法や、デザインを最適にサポートするスキーマを生成する方法などがあります。  
  
 モデルの作成方法に関係なく、各モデルにはソース データへの接続を指定する 1 つ以上のデータ ソース オブジェクトが必要です。 1 つのモデルに複数のデータ ソース オブジェクトを作成して、さまざまなソースのデータを使用したり、特定のオブジェクトの接続プロパティを変更したりできます。  
  
 データ ソース オブジェクトは、モデルの他のオブジェクトとは別に管理できます。 データ ソースを作成した後にプロパティを変更し、データが正しく取得されるようにモデルを前処理できます。  
  
## <a name="related-topics-and-tasks"></a>関連項目およびタスク  
  
|トピック|Description|  
|-----------|-----------------|  
|[サポートされるデータ ソース &#40;SSAS - 多次元&#41;](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)|多次元モデルで使用できるデータ ソースの種類について説明します。|  
|[データ ソース & #40; を作成します。SSAS 多次元 & #41;](../../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)|多次元モデルにデータ ソース オブジェクトを追加する方法について説明します。|  
|[ソリューション エクスプ ローラー & #40; でデータ ソースを削除します。SSAS 多次元 & #41;](../../analysis-services/multidimensional-models/delete-a-data-source-in-solution-explorer-ssas-multidimensional.md)|この手順で、多次元モデルからデータ ソース オブジェクトを削除します。|  
|[データ ソース プロパティの設定 & #40 です。SSAS 多次元 & #41;](../../analysis-services/multidimensional-models/set-data-source-properties-ssas-multidimensional.md)|各プロパティとその設定方法について説明します。|  
|[権限借用オプションを設定する & #40 です。SSAS - 多次元 & #41;](../../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md)|[権限借用情報] ダイアログ ボックスのオプションを構成する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ & #41;](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ & #41;](../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [多次元モデル内のデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
