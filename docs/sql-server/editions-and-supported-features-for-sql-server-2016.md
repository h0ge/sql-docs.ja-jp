---
title: "SQL Server 2016 の各エディションとサポートされる機能 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "sql エディション"
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
caps.latest.revision: 175
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b9b9db3ca911b8fd8eed6304b9d3a8f51e9e9ba2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="editions-and-supported-features-for-sql-server-2016"></a>SQL Server 2016 の各エディションとサポートされる機能
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のさまざまなエディションでサポートされる機能の詳細について説明します。  
  
 180 日の試用期間中、SQL Server Evaluation Edition をご利用いただけます。  
  
 最新のリリース ノートと新機能については、以下の情報を参照してください。
- [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
- [SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)

    
 **SQL Server 2016 をお試しください。**    
    
 > [![Evaluation Center からダウンロードする](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Evaluation Center から SQL Server 2016 をダウンロードする](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Azure Virtual Machine のアイコン](../analysis-services/media/azure-virtual-machine-small.png) **[SQL Server 2016 がインストール済みの Virtual Machine をすぐにご利用いただけます](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/Microsoft.SQL2016SP1-WS2016?tab=Overview?wt.mc_id=sqL16_vm)**    
    
**Developer Edition と Evaluation Edition**   
 Developer Edition と Evaluation Edition でサポートされている機能については、下の表に記載されている SQL Server Enterprise Edition の機能をご覧ください。
[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 の Developer Edition に追加された機能の一覧については、[SQL Server 2016 SP1 の各エディション](https://aka.ms/uw6cw4)に関するページをご覧ください。   
  
##  <a name="Cross-BoxScaleLimits"></a> Scale Limits  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限| 
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] または [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとのバッファー プールの最大メモリ|オペレーティング システムの最大容量|128 GB|64 GB|1410 MB|1410 MB|
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとの列ストア セグメント キャッシュの最大メモリ|メモリ制限なし| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のデータベースごとの最大メモリ最適化データ サイズ|メモリ制限なし| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  
|利用可能な最大メモリ サイズ ( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスごと)|オペレーティング システムの最大容量|テーブル: 16 GB<br /><br /> MOLAP: 64 GB|なし|なし|なし|  
|利用可能な最大メモリ サイズ ( [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のインスタンスごと)|オペレーティング システムの最大容量|64 GB|64 GB|4 GB|なし|
|リレーショナル データベースの最大サイズ|524 PB|524 PB|524 PB|10 GB|10 GB|  
  
<sup>1</sup> Enterprise Edition with Server + Client Access License (CAL) に基づくライセンス (新しい使用許諾契約では利用できません) は、SQL Server インスタンスあたり最大 20 コアに制限されています。 コアベースのサーバー ライセンス モデルでは、制限はありません。 詳細については、「 [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)」を参照してください。  
  
<sup>2</sup> [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 に適用されます。 

##  <a name="RDBMSHA"></a> RDBMS High Availability  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Server Core サポート <sup>1</sup>|可|はい|はい|はい|可|  
|ログ配布|可|はい|可|いいえ|不可|  
|データベース ミラーリング|可|可<br /><br /> FULL SAFETY のみ|ミラーリング監視のみ|ミラーリング監視のみ|ミラーリング監視のみ| 
|バックアップ圧縮|可|可|いいえ|いいえ|不可| 
|データベース スナップショット|可|可 <sup>3</sup>|可 <sup>3</sup>|可 <sup>3</sup>|可 <sup>3</sup>|
|Always On フェールオーバー クラスター インスタンス|はい<br /><br /> ノードの数はオペレーティング システムの最大容量|はい<br /><br /> 2 つのノードのサポート|不可|いいえ|不可|  
|Always On 可用性グループ|可<br /><br /> 2 個の同期セカンダリ レプリカを含む最大 8 個のセカンダリ レプリカ|不可|いいえ|いいえ|不可|
|基本的な可用性グループ <sup>2</sup>|不可|可<br /><br /> 2 つのノードのサポート|不可|いいえ|不可|
|オンライン ページおよびファイルの復元|可|いいえ|いいえ|いいえ|不可|
|オンラインのインデックス構築|可|いいえ|いいえ|いいえ|不可|
|オンラインのスキーマ変更|可|いいえ|いいえ|いいえ|不可|
|高速復旧|可|いいえ|いいえ|いいえ|不可|
|ミラー化バックアップ|可|いいえ|いいえ|いいえ|不可|
|ホット アド メモリと CPU|可|いいえ|いいえ|いいえ|不可|
|データベース復旧アドバイザー|可|はい|はい|はい|可|
|暗号化されたバックアップ|可|可|いいえ|いいえ|不可|
|Windows Azure へのハイブリッド バックアップ (URL へのバックアップ)|可|可|いいえ|いいえ|不可|  
  
 <sup>1</sup> Server Core への SQL Server 2016 のインストールの詳細については、「 [Server Core への SQL Server 2016 のインストール](../database-engine/install-windows/install-sql-server-on-server-core.md)」を参照してください。 

<sup>2</sup> 基本的な可用性グループの詳細については、「 [基本的な可用性グループ](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)」を参照してください。  

<sup>3</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。
  
##  <a name="RDBMSSP"></a> RDBMS Scalability and Performance  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|列ストア <sup>1</sup>|可|可 <sup>2</sup>|可 <sup>2</sup>|可<sup>2</sup>|可<sup>2</sup>|  
|インメモリ OLTP <sup>1</sup>|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>、 <sup>3</sup>|可 <sup>2</sup>|
|Stretch Database|可|はい|はい|はい|可|
|恒久的なメイン メモリ|可|はい|はい|はい|可|
|複数インスタンスのサポート|50|50|50|50|50|
|テーブルとインデックスのパーティション分割|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|  
|データ圧縮|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|
|[リソース ガバナー]|可|いいえ|いいえ|いいえ|不可|  
|パーティション テーブルの並列処理|可|いいえ|いいえ|いいえ|不可|
|複数の Filestream コンテナー|可|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|可 <sup>2</sup>|
|NUMA 対応のラージ ページ メモリとバッファー配列の割り当て|可|いいえ|いいえ|いいえ|不可|
|バッファー プール拡張|可|可|いいえ|いいえ|不可|
|IO リソース管理|可|いいえ|いいえ|いいえ|不可|  
|遅延持続性|可|はい|はい|はい|可|

<sup>1</sup> インメモリ OLTP データ サイズおよび列ストア セグメント キャッシュは、「スケールの制限」セクションでエディションごとに指定されているメモリ量に制限されます。 並列処理には最大限度があります。 インデックス構築のための並列処理の度合い (DOP) は、Standard Edition では 2 DOP に、Web および Express Edition では 1 DOP に制限されます。 これは、ディスク ベース テーブルとメモリ最適化テーブルで作成された列ストア インデックスに当てはまります。

<sup>2</sup> [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 に適用されます。 

<sup>3</sup> LocalDB のインストール オプションには、この機能は含まれていません。
##  <a name="RDBMSS"></a> RDBMS Security  
  
|機能|Enterprise|Standard|Web|Express|Express with Advanced Services|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|行レベルのセキュリティ|はい|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|  
|Always Encrypted|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>| 
|動的なデータ マスキング|可|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|   
|基本的な監査|可|はい|はい|はい|可| 
|詳細な監査|可|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>|可 <sup>1</sup>| 
|透過的なデータベースの暗号化|可|いいえ|いいえ|いいえ|不可|   
|拡張キー管理|可|いいえ|いいえ|いいえ|不可| 
|ユーザー定義ロール|可|はい|はい|はい|可| 
|包含データベース|可|はい|はい|はい|可| 
|バックアップの暗号化|可|可|いいえ|いいえ|不可|  

<sup>1</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。  
##  <a name="Replication"></a> Replication  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|異種サブスクライバー|可|可|いいえ|いいえ|不可|  
|マージ レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|Oracle パブリッシュ|可|いいえ|いいえ|いいえ|不可| 
|ピア ツー ピア トランザクション レプリケーション|可|いいえ|いいえ|いいえ|不可|   
|スナップショット レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|SQL Server の変更の追跡|可|はい|はい|はい|可| 
|トランザクション レプリケーション|可|可|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|可 (サブスクライバーのみ)|   
|Azure へのトランザクション レプリケーション|可|可|いいえ|いいえ|不可|   
|トランザクション レプリケーションの更新可能サブスクリプション|可|いいえ|いいえ|いいえ|不可|  
  
##  <a name="SSMS"></a> Management Tools  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL 管理オブジェクト (SMO)|可|はい|はい|はい|可|  
|SQL 構成マネージャー|可|はい|はい|はい|可|   
|SQL CMD (コマンド プロンプト ツール)|可|はい|はい|はい|可|      
|分散再生 - 管理ツール|可|はい|はい|可|不可|  
|分散再生 - クライアント|可|はい|可|いいえ|不可|  
|分散再生 - コントローラー|可 (最大 16 クライアント)|可 (1 クライアント)|可 (1 クライアント)|不可|不可|   
|SQL Profiler|可|可|不可 <sup>1</sup>|不可 <sup>1</sup>|不可 <sup>1</sup>|  
|SQL Server エージェント|可|はい|可|いいえ|不可| 
|Microsoft System Center Operations Manager 管理パック|可|はい|可|いいえ|不可|  
|データベース チューニング アドバイザー (DTA)|可|可 <sup>2</sup>|可 <sup>2</sup>|不可|不可|      
  
 <sup>1</sup> SQL Server Web、SQL Server Express、SQL Server Express with Tools、および SQL Server Express with Advanced Services は、SQL Server Standard および SQL Server Enterprise の各エディションを使用してプロファイルできます。  
  
 <sup>2</sup> チューニングは Standard Edition 機能でのみ有効です。  
  
##  <a name="RDBMSM"></a> RDBMS Manageability  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|ユーザー インスタンス|不可|いいえ|いいえ|はい|可| 
|LocalDB|不可|いいえ|いいえ|可|不可| 
|専用管理者接続|可|はい|可|可 (トレース フラグを使用)|可 (トレース フラグを使用)|   
|PowerShell スクリプティングのサポート|可|はい|はい|はい|可| 
|SysPrep のサポート <sup>1</sup>|可|はい|はい|はい|可| 
|データ層アプリケーション コンポーネントの操作のサポート - 抽出、配置、アップグレード、削除|可|はい|はい|はい|可| 
|ポリシー オートメーション (変更時とスケジュールに基づいて確認)|可|はい|可|いいえ|不可|   
|パフォーマンス データ コレクター|可|はい|可|いいえ|不可| 
|複数インスタンス管理でマネージ インスタンスとして登録できる|可|はい|可|いいえ|不可|   
|標準的なパフォーマンス レポート|可|はい|可|いいえ|不可| 
|プラン ガイドおよびプラン ガイドの固定計画|可|はい|可|いいえ|不可|   
|NOEXPAND ヒントを使用したインデックス付きビューの直接クエリ|可|はい|はい|はい|可| 
|インデックス付きビューの自動メンテナンス|可|はい|可|いいえ|不可| 
|分散パーティション ビュー|可|いいえ|いいえ|いいえ|不可| 
|並列インデックス操作|可|いいえ|いいえ|いいえ|不可|  
|クエリ オプティマイザーによる自動的なインデックス付きのビュー使用|可|いいえ|いいえ|いいえ|不可| 
|並列整合性チェック|可|いいえ|いいえ|いいえ|不可| 
|SQL Server ユーティリティ コントロール ポイント|可|いいえ|いいえ|いいえ|不可|    
|バッファー プール拡張|可|可|いいえ|いいえ|不可| 
  
 <sup>1</sup> 詳細については、「 [SysPrep を使用した SQL Server のインストールに関する注意点](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)」を参照してください。  
 
<sup>2</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。 
  
##  <a name="DevTools"></a> Development Tools  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Microsoft Visual Studio の統合|可|はい|はい|はい|可| 
|Intellisense (Transact-SQL および MDX)|可|はい|はい|はい|可| 
|SQL Server Data Tools (SSDT)|可|はい|はい|可|不可|    
|MDX 編集、デバッグ、およびデザイン ツール|可|可|いいえ|いいえ|不可|   
  
##  <a name="Programmability"></a> Programmability  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|基本的な R 統合|可|はい|はい|可|不可|   
|高度な R 統合|可|いいえ|いいえ|いいえ|不可| 
|R Server (Standalone)|可|いいえ|いいえ|いいえ|不可|   
|Polybase コンピューティング ノード|可|可 <sup>1</sup>|可 <sup>1</sup>、 <sup>2</sup>|可 <sup>1</sup>、 <sup>2</sup>|可 <sup>1</sup>、 <sup>2</sup>| 
|Polybase ヘッド ノード|可|いいえ|いいえ|いいえ|不可| 
|JSON|可|はい|はい|はい|可|   
|クエリ ストア|可|はい|はい|はい|可|   
|テンポラル|可|はい|はい|はい|可|   
|共通言語ランタイム (CLR) 統合|可|はい|はい|はい|可|   
|ネイティブ XML サポート|可|はい|はい|はい|可| 
|XML インデックスの作成|可|はい|はい|はい|可| 
|MERGE と UPSERT の機能|可|はい|はい|はい|可|   
|FILESTREAM のサポート|可|はい|はい|はい|可| 
|FileTable|可|はい|はい|はい|可| 
|日付および時刻データ型|可|はい|はい|はい|可|  
|国際化サポート|可|はい|はい|はい|可| 
|フルテキストおよびセマンティック検索|可|はい|はい|可|不可| 
|クエリ内の言語指定|可|はい|はい|可|不可|   
|Service Broker (メッセージング)|可|可|不可 (クライアントのみ)|不可 (クライアントのみ)|不可 (クライアントのみ)|   
|Transact-SQL エンドポイント|可|はい|可|いいえ|不可| 

<sup>1</sup> 複数のコンピューティング ノードでのスケール アウトにはヘッド ノードが必要です。

<sup>2</sup> [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 2016 SP1 に適用されます。
  
## <a name="IS"></a> Integration Services

[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] の各エディションがサポートする Integration Services (SSIS) の機能については、「[Integration Services Features Supported by the Editions of SQL Server (SQL Server の各エディションがサポートする Integration Services の機能)](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md)」をご覧ください。

##  <a name="MDS"></a> Master Data Services  
 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] の各エディションがサポートする [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]と Data Quality Services の機能については、「 [Master Data Services and Data Quality Services Features Supported by the Editions of SQL Server 2016](../master-data-services/master-data-services-and-data-quality-services-features-support.md)」(SQL Server 2016 の各エディションによってサポートされる Master Data Services と Data Quality Services の機能) をご覧ください。 

  
##  <a name="DW"></a> Data Warehouse  
  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|データベースを使用しないキューブ作成|可|可|いいえ|いいえ|不可 |   
|自動生成ステージングとデータ ウェアハウス スキーマ|可|可|いいえ|いいえ|不可| 
|変更データ キャプチャ|可|可 <sup>1</sup>|不可|いいえ|不可| 
|スター結合クエリ最適化|可|いいえ|いいえ|いいえ|不可| 
|スケーラブルな読み取り専用の Analysis Services 構成|可|いいえ|いいえ|いいえ|不可| 
|パーティション テーブルとパーティション インデックスに対する並列クエリ処理|可|いいえ|いいえ|いいえ|不可|   
|グローバル バッチ集計|可|いいえ|いいえ|いいえ|不可| 

<sup>1</sup> [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] SP1 に適用されます。  
##  <a name="SSAS"></a> Analysis Services  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]の各エディションによってサポートされる Analysis Services の機能については、「 [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。 
  
##  <a name="BIMD"></a> BI Semantic Model (Multi Dimensional)  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]の各エディションによってサポートされる Analysis Services の機能については、「 [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
   
##  <a name="BIT"></a> BI Semantic Model (Tabular)  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]の各エディションによってサポートされる Analysis Services の機能については、「 [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
  
##  <a name="PPSP"></a> Power Pivot for SharePoint  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]の各エディションによってサポートされる Power Pivot for SharePoint の機能については、「 [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
  
##  <a name="DM"></a> Data Mining  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]の各エディションによってサポートされるデータ マイニングの機能については、「 [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) をご覧ください。
  
##  <a name="SSRS"></a> Reporting Services  
  
[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]の各エディションによってサポートされる Reporting Services の機能については、「 [SQL Server 2016 の各エディションがサポートする Reporting Services の機能](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)」をご覧ください。

##  <a name="BIC"></a> Business Intelligence Clients  

[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]の各エディションによってサポートされる Business Intelligence クライアントの機能については、「 [Analysis Services Features Supported by the Editions of SQL Server 2016](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md) 」(SQL Server 2016 の各エディションによってサポートされる Analysis Services の機能) または「 [SQL Server 2016 の各エディションがサポートする Reporting Services の機能](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)」をご覧ください。
  
##  <a name="SLS"></a> Spatial and Location Services  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|空間インデックス|可|はい|はい|はい|可|   
|平面データ型と測地データ型|可|はい|はい|はい|可| 
|高度な空間的なライブラリ|可|はい|はい|はい|可|   
|業界標準の空間データ形式のインポート/エクスポート|可|はい|はい|はい|可|   
  
##  <a name="ADS"></a> Additional Database Services  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|可|はい|はい|はい|可|   
|データベース メール|可|はい|可|いいえ|不可| 
  
##  <a name="Other"></a> Other Components  
  
|機能名|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|不可|不可| 
|StreamInsight HA|StreamInsight Premium Edition|不可|いいえ|いいえ|不可|   
  
> [![Download SSMS](../analysis-services/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Download the latest version of SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**    
  
## <a name="see-also"></a>参照  
 [SQL Server 2016 の製品仕様](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md)  
  
  
