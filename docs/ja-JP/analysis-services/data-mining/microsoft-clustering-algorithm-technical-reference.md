---
title: Microsoft クラスタ リング アルゴリズム テクニカル リファレンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- clustering [Data Mining]
- MAXIMUM_INPUT_ATTRIBUTES parameter
- CLUSTER_SEED parameter
- MODELLING_CARDINALITY parameter
- MINIMUM_SUPPORT parameter
- STOPPING_TOLERANCE parameter
- MAXIMUM_STATES parameter
- SAMPLE_SIZE parameter
- CLUSTERING_METHOD parameter
- soft clustering [Data Mining]
- clustering algorithms [Analysis Services]
- CLUSTER_COUNT parameter
ms.assetid: ec40868a-6dc7-4dfa-aadc-dedf69e555eb
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 16d3dae2010f43a15cf11d83891bdf30b5b5b518
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-clustering-algorithm-technical-reference"></a>Microsoft クラスタリング アルゴリズム テクニカル リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ここでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムの実装について、クラスター モデルの動作を制御するために使用できるパラメーターを含めて説明します。 クラスター モデルの作成時や処理時のパフォーマンスを向上させる方法に関するアドバイスも含まれています。  
  
 クラスター モデルの使用方法の詳細については、次のトピックを参照してください。  
  
-   [クラスタ リング モデル & #40; のマイニング モデル コンテンツAnalysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
-   [クラスタ リング モデルのクエリ例](../../analysis-services/data-mining/clustering-model-query-examples.md)  
  
## <a name="implementation-of-the-microsoft-clustering-algorithm"></a>Microsoft クラスタリング アルゴリズムの実装  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムには、クラスターを作成し、クラスターにデータ ポイントを割り当てるための 2 つの方法が用意されています。 1 つ目の *K-Means* アルゴリズムは、ハード クラスタリングの手法です。 この手法では、データ ポイントが所属できるクラスターは 1 つだけであるため、そのクラスターの各データ ポイントのメンバーシップについて 1 つの確率が計算されます。 2 つ目の *Expectation Maximization* (EM) 手法は、 *ソフト クラスタリング* の手法です。 この手法では、データ ポイントが常に複数のクラスターに所属するため、データ ポイントとクラスターの組み合わせごとに確率が計算されます。  
  
 どちらのアルゴリズムを使用するかは、 *CLUSTERING_METHOD* パラメーターを設定して選択できます。 既定のクラスタリング手法はスケーラブル EM です。  
  
### <a name="em-clustering"></a>EM クラスタリング  
 EM クラスタリングでは、初期クラスター モデルがデータに合わせて反復的に調整され、データ ポイントがクラスター内に存在する確率が判定されます。 このプロセスは、その確率論的モデルがデータに適合すると終了します。 適合の判定に使用される関数は、与えられたモデルに対するデータの対数尤度です。  
  
 このプロセスで空のクラスターが生成された場合や、メンバーシップが指定のしきい値に達していないクラスターがあった場合は、母集団の小さいクラスターが新しいポイントで再シードされ、EM アルゴリズムが再実行されます。  
  
 EM クラスタリング手法の結果は確率論的です。 つまり、すべてのデータ ポイントがすべてのクラスターに所属しますが、割り当ての確率はそれぞれ異なります。 この手法ではクラスターの重複が許可されるため、すべてのクラスター内のアイテムの合計がトレーニング セットのアイテムの合計数を上回る場合もあります。 マイニング モデルの結果では、このことを反映してサポートのスコアが調整されます。  
  
 EM アルゴリズムは、Microsoft クラスター モデルで使用される既定のアルゴリズムです。 このアルゴリズムが既定で使用されるのは、K-Means クラスタリングに比べて次のような利点があるためです。  
  
-   データベースのスキャンが 1 回で済む。  
  
-   メモリ (RAM) が限られていても動作する。  
  
-   順方向専用カーソルを使用できる。  
  
-   サンプリングの手法よりパフォーマンスが高い。  
  
 Microsoft による実装には、スケーラブル EM と非スケーラブル EM という 2 つのオプションがあります。 既定のスケーラブル EM では、初期スキャンのシードに最初の 50,000 レコードが使用されます。 これが成功した場合は、モデルでそのデータのみが使用されます。 50,000 個のレコードを使用して適切なモデルを作成できなかった場合は、さらに 50,000 個のレコードが読み取られます。 非スケーラブル EM では、サイズにかかわらずデータセット全体が読み取られます。 これにより、より正確なクラスターが作成される場合もありますが、必要なメモリの量が大幅に増加する可能性があります。 スケーラブル EM では、ローカル バッファーが使用されるため、データの反復処理が大幅に高速化されます。また、非スケーラブル EM よりはるかに効率的に CPU メモリ キャッシュを活用できます。 さらに、すべてのデータがメイン メモリに収まる場合でも非スケーラブル EM に比べて 3 倍高速になります。 このパフォーマンスの改善によって最終的なモデルの質が低下することもほとんどありません。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムの EM の実装に関する技術的なレポートについては、「 [EM (Expectation Maximization) クラスタリングの大規模データベースへのスケーリング](http://go.microsoft.com/fwlink/?LinkId=45964)」を参照してください。  
  
### <a name="k-means-clustering"></a>K-Means クラスタリング  
 K-Means クラスタリングは、クラスター内のアイテム間の相違を最小化し、クラスター間の距離を最大化することによってクラスター メンバーシップを割り当てる、よく知られている手法です。 K-Means の "Means" は、クラスターの *重心* を表します。クラスターの重心とは、任意に選択され、クラスター内のすべてのデータ ポイントの真の平均を表すようになるまで反復的に調整されるデータ ポイントです。 "K" は、クラスタリング処理のシードに使用される任意の数のポイントを表します。 K-Means アルゴリズムでは、クラスター内のデータ レコードと、クラスターの平均を表すベクトルとの間のユークリッド距離の 2 乗を計算し、その総和が最小値に達したとき、最終的な k 個のクラスターのセットに収束します。  
  
 K-Means アルゴリズムでは、各データ ポイントが割り当てられるクラスターは 1 つだけであり、メンバーシップのあいまいさは許容されません。 クラスターのメンバーシップは重心からの距離として表されます。  
  
 K-Means アルゴリズムは、平均への距離を簡単に計算できる連続属性のクラスターの作成に使用されるのが一般的ですが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] の実装では、確率を使用することにより、不連続属性に対しても使用できるようになっています。  不連続属性の場合、特定のクラスターからデータ ポイントまでの距離は次のように計算されます。  
  
 1 - P(data point, cluster)  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムでは、K-Means の計算に使用される距離関数は公開されておらず、完成したモデルで距離の測定値を使用することはできません。 ただし、予測関数を使用して、距離に相当する値を取得することができます。この場合の距離は、データ ポイントがクラスターに属する確率として計算されます。 詳細については、「[ClusterProbability &#40;DMX&#41;](../../dmx/clusterprobability-dmx.md)」を参照してください。  
  
 K-Means アルゴリズムには、データセットのサンプリング方法が 2 つ用意されています。1 つ目の非スケーラブル K-Means では、データセット全体を読み込んで 1 つのクラスタリング パスを作成します。2 つ目のスケーラブル K-Means では、最初の 50,000 ケースを使用してデータに適合するモデルを作成できなかった場合にのみ追加のケースが読み取られます。  
  
### <a name="updates-to-the-microsoft-clustering-algorithm-in-sql-server-2008"></a>SQL Server 2008 の Microsoft クラスタリング アルゴリズムへの更新  
 SQL Server 2008 では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムの既定の構成が、内部パラメーター NORMALIZATION = 1 を使用するように変更されました。 正規化は z スコア統計を使用して実行され、正規分布を想定しています。 既定の動作をこのように変更したのは、規模が大きくなり外れ値が増える可能性がある属性の影響を最小限に抑えるためです。 ただし、z スコア正規化により、正規ではない分布 (均一分布など) のクラスタリング結果が異なる可能性があります。 正規化を回避し、SQL Server 2005 の K-Means クラスタリング アルゴリズムと同じ動作を得るには、 **[パラメーター設定]** ダイアログ ボックスを使用して、カスタム パラメーター NORMALIZATION を追加し、その値を 0 に設定します。  
  
> [!NOTE]  
>  NORMALIZATION パラメーターは [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムの内部プロパティであり、サポートされていません。 通常、モデルの結果を向上させるには、クラスタリング モデルで正規化を使用することをお勧めします。  
  
## <a name="customizing-the-microsoft-clustering-algorithm"></a>Microsoft クラスタリング アルゴリズムのカスタマイズ  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムでは、結果として得られるマイニング モデルの動作、パフォーマンス、および精度に影響を与えるいくつかのパラメーターがサポートされています。  
  
### <a name="setting-algorithm-parameters"></a>アルゴリズム パラメーターの設定  
 次の表は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムで使用できるパラメーターを示しています。 これらのパラメーターは、結果として得られるマイニング モデルのパフォーマンスと精度の両方に影響を与えます。  
  
 CLUSTERING_METHOD  
 アルゴリズムで使用するクラスタリング手法を指定します。 使用可能なクラスタリング手法は次のとおりです。  
  
|ID|方法|  
|--------|------------|  
|1|スケーラブル EM|  
|2|非スケーラブル EM (Non-scalable EM)|  
|3|スケーラブル K-Means|  
|4|非スケーラブル K-Means|  
  
 既定値は 1 (スケーラブル EM) です。  
  
 CLUSTER_COUNT  
 アルゴリズムによって作成されるクラスターの概数を指定します。 その数のクラスターをデータから作成できない場合は、可能な限り多数のクラスターが作成されます。 CLUSTER_COUNT を 0 に設定すると、アルゴリズムではヒューリスティックを使用して、作成するクラスターの数が最適に決定されます。  
  
 既定値は、10 です。  
  
 CLUSTER_SEED  
 モデル作成の初期段階にクラスターをランダムに生成するために使用するシード数を指定します。  
  
 この数を変更することにより、初期クラスターの作成方法を変更できます。その後、異なるシードを使用して作成したモデルを比較することができます。 シードを変更しても検出されるクラスターがあまり変わらない場合は、モデルが比較的安定していると考えることができます。  
  
 既定値は 0 です。  
  
 MINIMUM_SUPPORT  
 クラスターの作成に必要なケースの最小数を指定します。 ケースの数がこの数より少ないクラスターは空のクラスターとして扱われ、破棄されます。  
  
 この数を高く設定しすぎると、有効なクラスターを見落とす可能性があります。  
  
> [!NOTE]  
>  既定のクラスタリング手法である EM を使用すると、指定した値より低いサポート値を持つクラスターが作成される場合があります。 これは、各ケースがすべての可能なクラスターのメンバーシップについて評価されるため、中には最小限のサポートしかないクラスターもあるからです。  
  
 既定値は 1 です。  
  
 MODELLING_CARDINALITY  
 クラスタリング処理中に作成されるサンプル モデルの数を指定します。  
  
 この数を減らすと、適切な候補モデルが作成されなくなる可能性もありますが、パフォーマンスを向上させることができます。  
  
 既定値は、10 です。  
  
 STOPPING_TOLERANCE  
 収束に到達し、アルゴリズムによるモデルの作成が完了する時点を決定するための値を指定します。 収束に到達するのは、クラスターの確率の全体的な変化が、モデルのサイズで除算された STOPPING_TOLERANCE パラメーターの比率に満たないときです。  
  
 既定値は、10 です。  
  
 SAMPLE_SIZE  
 CLUSTERING_METHOD パラメーターをスケーラブルなクラスタリング手法のいずれかに設定する場合に、アルゴリズムにより各パスで使用されるケースの数を指定します。 SAMPLE_SIZE パラメーターを 0 に設定すると、データセット全体が単一のパスでクラスター化されます。 データセット全体を単一のパスで読み込むと、メモリやパフォーマンスの問題が発生する可能性があります。  
  
 既定値は 50000 です。  
  
 MAXIMUM_INPUT_ATTRIBUTES  
 選択した機能を呼び出す前にアルゴリズムが処理できる入力属性の最大数を指定します。 この値を 0 に設定した場合、属性数の上限はありません。  
  
 属性の数を増やすと、パフォーマンスが大幅に低下する可能性があります。  
  
 既定値は 255 です。  
  
 MAXIMUM_STATES  
 アルゴリズムによってサポートされる属性状態の最大数を指定します。 属性の状態の数が最大数よりも大きい場合、アルゴリズムでは最も一般的な状態が使用され、残りの状態は無視されます。  
  
 状態の数を増やすと、パフォーマンスが大幅に低下する可能性があります。  
  
 既定値は、100 です。  
  
### <a name="modeling-flags"></a>ModelingFlags  
 アルゴリズムでは、次のモデリング フラグがサポートされています。 モデリング フラグは、マイニング構造やマイニング モデルを作成するときに定義し、 分析時に各列の値をどのように処理するかを指定します。  
  
|モデリング フラグ|Description|  
|-------------------|-----------------|  
|MODEL_EXISTENCE_ONLY|列が、Missing および Existing の 2 つの可能な状態を持つ列として扱われます。 NULL は Missing 値になります。<br /><br /> マイニング モデル列に適用されます。|  
|NOT NULL|列に NULL を含めることはできません。 モデルのトレーニング中に NULL が検出された場合はエラーが発生します。<br /><br /> マイニング構造列に適用されます。|  
  
## <a name="requirements"></a>必要条件  
 クラスタリング モデルは、キー列と入力列を含んでいる必要があります。 入力列は、予測可能列として定義することもできます。 **[予測のみ]** に設定されている列は、クラスターの作成には使用されません。 クラスター内のそれらの値の分布は、クラスターの作成後に算出されます。  
  
### <a name="input-and-predictable-columns"></a>入力列と予測可能列  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムでは、次の表に示す特定の入力列と予測可能列がサポートされています。 マイニング モデルにおけるコンテンツの種類の意味については、「[コンテンツの種類 &#40;データ マイニング&#41;](../../analysis-services/data-mining/content-types-data-mining.md)」を参照してください。  
  
|列|コンテンツの種類|  
|------------|-------------------|  
|入力属性|Continuous、Cyclical、Discrete、Discretized、Key、Table、Ordered|  
|予測可能な属性|Continuous、Cyclical、Discrete、Discretized、Table、Ordered|  
  
> [!NOTE]  
>  コンテンツの種類 Cyclical および Ordered はサポートされますが、アルゴリズムはこれらを不連続の値として扱い、特別な処理は行いません。  
  
## <a name="see-also"></a>参照  
 [Microsoft クラスタ リング アルゴリズム](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)   
 [クラスタ リング モデルのクエリ例](../../analysis-services/data-mining/clustering-model-query-examples.md)   
 [クラスタ リング モデル & #40; のマイニング モデル コンテンツAnalysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  