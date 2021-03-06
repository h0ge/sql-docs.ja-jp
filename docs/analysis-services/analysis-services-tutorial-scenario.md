---
title: Analysis Services のチュートリアルのシナリオ |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a564052f268120fb02baefdf7991978bf24bfaa
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34016039"
---
# <a name="analysis-services-tutorial-scenario"></a>Analysis Services のチュートリアル シナリオ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]
このチュートリアルには、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]という架空の会社が登場します。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、特殊合金自転車を北アメリカ、ヨーロッパ、およびアジアの市場に供給する大規模な多国籍製造会社です。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] はワシントン州のボセルに本社を置き、500 名の従業員を抱えています。 さらに、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の各市場には、その地域を担当する販売チームがいます。  
  
近年、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、メキシコの小さな製造工場 Importadores Neptuno を買収しました。 Importadores Neptuno は、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の生産ラインにおけるいくつかの重要な部品を製造しています。 これらの部品はボセルに出荷され、そこで完成品が組み立てられます。 2005 年、同社は、ツーリング自転車製品群を独占的に製造、流通する企業に成長しました。  
  
好調なこの年に続き、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、対象顧客を絞って広告を打ち、Web サイトを通じた製品販売も開始することで、市場シェアをさらに拡大しようとしています。同時に、製造コストを抑え、最終的には販売コストを削減することも同社の目標の 1 つです。  
  
## <a name="current-analysis-environment"></a>現在の分析環境  
Adventure Works Cycles では、販売チーム、マーケティング チーム、および上級管理職のデータ分析ニーズに対応するため、トランザクション データ (取引データ) は [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] データベースから取り出し、販売量などの非トランザクション データはスプレッドシートから取り出して、これらの情報を **AdventureWorksDW2012** と呼ばれるリレーショナル データ ウェアハウスに統合しています。 しかし、リレーショナル データ ウェアハウスには次の問題があります。  
  
-   レポートが静的である。 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel のピボット テーブルなどと違い、データをインタラクティブに操作してレポートを生成できないので、詳細情報を取得できません。 既存の定義済みレポートで十分な情報を得られるユーザーも多いのですが、インタラクティブなクエリと専門的なレポートを使用する上級ユーザーは、データベースに直接クエリを送信する必要があります。 しかし、 **AdventureWorksDW2012** データベースは複雑であるため、効果的なクエリの作成方法を習得するにはかなりの時間がかかります。  
  
-   クエリ パフォーマンスの落差が大きい。 たとえば、クエリによって、結果が数秒で返される場合と、数分かかる場合があります。  
  
-   集計テーブルの管理が難しい。 クエリの応答時間を短縮するため、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] のデータ ウェアハウス チームは、 **AdventureWorksDW2012** データベースにいくつかの集計テーブルを作成しました。 たとえば、月ごとの売上を要約するテーブルなどです。 これらの集計テーブルはクエリ パフォーマンスを非常に向上させますが、テーブルを保守するために構築したインフラストラクチャは時間の経過と共に劣化し、エラーを招きます。  
  
-   複雑な計算ロジックがレポート定義に組み込まれているため、レポート間での計算ロジックの共有が困難。 このビジネス ロジックはレポートごとに個別に生成されるため、概要情報がレポートごとに異なる場合があります。 したがって、データ ウェアハウスのレポートでは管理の信頼性が限られます。  
  
-   必要となるデータ ビューが事業部によって異なる。 各グループとは無関係なデータ要素によって情報が散漫になり、混乱を招きます。  
  
-   専門的なレポートを必要とするユーザーにとって、計算ロジックが高いハードルとなる。 専門的なレポートを生成する場合は、レポートごとに計算ロジックを定義する必要があります。計算ロジックの定義方法を一本化することはできません。 たとえば、移動平均など、基本的な統計手法を使用すればよいことがわかっていても、その計算式の作成方法を理解していなければ、必要なレポートを生成できません。  
  
-   関連する情報のセットを組み合わせることが困難。 売上と販売量など、関連する 2 つの情報を組み合わせる特殊なクエリを作成することは、ビジネス ユーザーにとっては困難です。 このようなクエリはデータベースに大きい負荷をかけるため、Adventure Works Cycles のユーザーは、複数分野のデータのセットをデータ ウェアハウス チームに要求しなければなりません。 結果として、複数の分野のデータを組み合わせた、少数の定義済みレポートを定義するのみになっています。 また、これらのレポートは複雑であるため、ユーザーはレポートに手を加えることを敬遠しています。  
  
-   レポートの仕様が、主に米国のビジネス情報に合わせられている。 米国外の子会社のユーザーはこの仕様に大きな不満を持っており、自国の通貨単位および言語でレポートを表示したいという要望を持っています。  
  
-   情報の監査が難しい。 現在、経理部門は、一括クエリを行うためのデータ ソースとしてのみ **AdventureWorksDW2012** データベースを使用しています。 その後、各スプレッドシートにデータがダウンロードされ、スプレッドシートの準備と操作に膨大な時間が費やされます。 したがって、経理レポートの準備、監査、および全社的な管理が困難です。  
  
## <a name="the-solution"></a>解決策  
先ごろ、データ ウェアハウス チームは、現在の分析システムの設計を再評価しました。 この評価には、現在の問題点と今後の要望のずれを調査するギャップ分析も含まれています。 データ ウェアハウス チームは、 **AdventureWorksDW2012** データベースが適切なディメンションと代理キーを持つ優れた設計のディメンショナル データベースであると判断しました。 適切なディメンションにより、時間ディメンションや製品ディメンションなど複数のデータ マートでディメンションを使用できます。 代理キーは、ディメンションとファクト テーブルをリンクする擬似的なキーです。一意性を確保し、パフォーマンスを向上させるために使用されます。 また、 **AdventureWorksDW2012** データベースでベース テーブルの読み込みと管理を行う分には、現在のところ大きな問題はないと判断しました。 したがって、データ ウェアハウス チームは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を次の目的に使用することにしました。  
  
-   分析的な調査やレポート生成では、共通のメタデータ層を経由するようデータへのアクセス経路を統合する。  
  
-   ユーザーのデータ表示を簡略化し、対話型のクエリ、定義済みクエリ、および定義済みレポートの開発効率を向上させる。  
  
-   複数の分野のデータを組み合わせたクエリを適切に作成する。  
  
-   集計を管理する。  
  
-   複雑な計算を保存し、再利用できるようにする。  
  
-   米国外のビジネス ユーザーにローカライズされたサービスを提供する。  
  
Analysis Services チュートリアルのレッスンには、これらのすべての目標に適したキューブ データベースを構築するためのガイダンスが用意されています。 まず、「 [レッスン 1: 新しいテーブル モデル プロジェクトの作成](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)」に進みます。  
  
## <a name="see-also"></a>参照  
[多次元モデリング & #40 です。Adventure Works チュートリアル & #41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
  
  
  
