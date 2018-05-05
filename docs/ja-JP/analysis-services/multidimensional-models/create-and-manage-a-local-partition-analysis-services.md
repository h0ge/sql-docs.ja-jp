---
title: 作成し、ローカル パーティション (Analysis Services) の管理 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 114f093cfe6531a0a2fc52b874730f1e4105f1d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-manage-a-local-partition-analysis-services"></a>ローカル パーティションの作成と管理 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  メジャー グループに追加のパーティションを作成すると、処理パフォーマンスを向上させることができます。 複数のパーティションがあると、ローカル サーバーとリモート サーバー上の対応する数の物理データ ファイルにファクト データを割り当てることができます。 Analysis Services では、パーティションを個別に処理することも並列に処理することもできるため、サーバー上の処理ワークロードをより細かく制御できます。  
  
 パーティションは、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でモデルのデザイン時に作成するか、または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または XMLA を使用してソリューションを配置した後に作成することができます。 方法を 1 つだけ選択することをお勧めします。 ツールを何度も切り替えると、後で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] からソリューションを再配置したときに、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で配置されたデータベースに対して行った変更が上書きされることがあります。  
  
## <a name="before-you-start"></a>開始前の準備  
 Business Intelligence Edition または Enterprise Edition を持っているかどうかを確認します。 Standard Edition では、複数のパーティションがサポートされていません。 エディションを確認するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサーバー ノードを右クリックし、 **[レポート]** | **[全般]** を選択します。 使用できる機能の詳細については、「 [SQL Server 2016 の各エディションでサポートされる機能](../../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」を参照してください。  
  
 パーティションを後でマージする場合は、パーティションで同じ集計デザインを共有する必要があることを最初に理解しておくことが重要です。 パーティションをマージできるのは、集計デザインとストレージ モードが同じ場合のみです。  
  
> [!TIP]  
>  データ ソース ビュー (DSV) 内のデータを調べて、パーティション分割するデータの範囲と深さを把握します。 たとえば、日付でパーティション分割する場合、日付列で並べ替えると、各パーティションの上限と下限を判別できます。  
  
## <a name="choose-an-approach"></a>アプローチの選択  
 パーティションを作成する際に最も重要な考慮事項は、重複する行がないようにデータを分割することです。 行が二重カウントされないように、データは 1 つのパーティションだけに格納する必要があります。 そのため、各パーティションの間に明確な境界を定義できるように、日付でパーティション分割するのが一般的です。  
  
 または、複数のパーティションにファクト データを分散する手法も使用できます。 データを分割するには、次の手法を使用できます。  
  
|手法|推奨事項|  
|---------------|---------------------|  
|SQL クエリを使用してファクト データを分割する|パーティションのソースには SQL クエリを指定できます。 処理中に、SQL クエリによってデータが取得されます。 クエリの WHERE 句では、各パーティションにデータを分割するフィルターを指定します。 Analysis Services によってクエリが生成されますが、データを適切に分割するために WHERE 句を自分で入力する必要があります。<br /><br /> このアプローチの主な利点は、1 つのソース テーブルから簡単にデータをパーティション分割できることです。 すべてのソース データが大きなファクト テーブルから取得される場合、そのデータを個別のパーティションにフィルター処理するクエリを作成できます。データ ソース ビュー (DSV) で追加のデータ構造を作成する必要はありません。<br /><br /> 1 つの欠点として、クエリを使用すると、パーティションと DSV のバインドが機能しなくなることが挙げられます。 ファクト テーブルに列を追加するなど、後で Analysis Services プロジェクトで DSV を更新する場合は、新しい列を含めるように各パーティションのクエリを手動で編集する必要があります。 次に説明する 2 番目のアプローチにはこの欠点はありません。|  
|DSV 内のテーブルを使用してファクト データを分割する|DSV 内のテーブル、名前付きクエリ、またはビューにパーティションをバインドできます。 パーティションの基盤として、この 3 つすべては機能的に等価です。 テーブル全体、名前付きクエリ、またはビューで、すべてのデータが 1 つのパーティションに提供されます。<br /><br /> テーブル、ビュー、または名前付きクエリを使用すると、DSV にデータ選択ロジック全体が配置され、長期にわたる管理とメンテナンスがより簡単になります。 このアプローチの重要な利点は、テーブルのバインドが保持されることです。 ソース テーブルを後で更新する場合に、そのソース テーブルを使用するパーティションを変更する必要はありません。 もう 1 つの利点として、すべてのテーブル、名前付きクエリ、およびビューが共通のワークスペースに存在するため、更新がより簡単になり、パーティションのクエリを個別に開いて編集する必要がありません。|  
  
## <a name="option-1-filter-a-fact-table-for-multiple-partitions"></a>オプション 1: 複数パーティション用のファクト テーブルをフィルター選択する  
 複数のパーティションを作成するには、最初に、既定のパーティションの **[ソース]** プロパティを変更します。 既定では、メジャー グループは、DSV 内の 1 つのテーブルにバインドされている 1 つのパーティションを使用して作成されます。 さらにパーティションを追加する前に、まず、ファクト データの一部だけが含まれるように元のパーティションを変更する必要があります。 その後、残りのデータを格納するための追加のパーティションを作成できます。  
  
 パーティション間でデータが重複しないように、フィルターを作成します。 パーティションのフィルターは、そのパーティションで使用されるファクト テーブル内のデータを指定します。 キューブに含まれるすべてのパーティションのフィルターが、ファクト テーブルから相互排他的なデータセットを取り出すことが重要です。 同一のファクト データは、複数のパーティションに存在すると二重カウントされることがあります。  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のソリューション エクスプローラーで、キューブをダブルクリックしてキューブ デザイナーで開き、 **[パーティション]** タブをクリックします。  
  
2.  パーティションを追加するメジャー グループを展開します。 既定では、各メジャー グループには、DSV 内のファクト テーブルにバインドされた 1 つのパーティションがあります。  
  
3.  ソース 列で、参照ボタン (. .) をクリックして、パーティション ソース ダイアログ ボックスを開きます。  
  
     ![[パーティション] ペイン内のソース列](../../analysis-services/multidimensional-models/media/ssas-partitionsource.png "[パーティション] ペイン内のソース列")  
  
4.  [バインドの種類] で **[クエリ バインド]** を選択します。 データを選択する SQL クエリが自動的に表示されます。  
  
5.  下部にある WHERE 句で、このパーティションのデータを分割するフィルターを追加します。  
  
     WHERE 句の構文例として、`WHERE OrderDateKey >= '20060101'` や `WHERE OrderDateKey BETWEEN '20051001' AND '20051201'` があります。 その他の例については、「[WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)」を参照してください。  
  
     次のフィルターは各セット内で相互排他的であることに注意してください。  
  
    |||  
    |-|-|  
    |セット 1:|"SaleYear" = 2012<br /><br /> "SaleYear" = 2013|  
    |セット 2:|"Continent" = 'NorthAmerica'<br /><br /> "Continent" = 'Europe'<br /><br /> "Continent" = 'SouthAmerica'|  
    |セット 3:|"Country" = 'USA'<br /><br /> "Country" = 'Mexico'<br /><br /> ("Country" <> 'USA' AND "Country" <> 'Mexico')|  
  
6.  **[確認]** をクリックして構文エラーの有無を確認し、**[OK]** をクリックします。  
  
7.  前の手順を繰り返して残りのパーティションを作成し、毎回次のデータ スライスを選択するように WHERE 句を変更します。  
  
8.  ソリューションを配置するかパーティションを処理して、データを読み込みます。 必ずすべてのパーティションを処理してください。  
  
9. キューブを参照して、正しいデータが返されていることを確認します。  
  
 複数のメジャー グループを使用するメジャー グループを作成したら、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で追加のパーティションを作成できます。 メジャー グループで、[パーティション] フォルダーを右クリックし、 **[新しいパーティション]** をクリックしてウィザードを開始します。  
  
> [!NOTE]  
>  パーティション内のデータをフィルター選択する代わりに、同じクエリを使用して DSV で名前付きクエリを作成し、その名前付きクエリに基づいてパーティションを作成できます。  
  
## <a name="option-2-use-tables-views-or-named-queries"></a>オプション 2: テーブル、ビュー、または名前付きクエリを使用する  
 DSV で既にファクトが個々のテーブル (年ごとや四半期ごとなど) に編成されている場合は、個々のテーブルに基づくパーティションを作成できます。各パーティションには独自のデータ ソース テーブルが用意されます。 基本的には、これがメジャー グループをパーティション分割する既定の方法となりますが、複数のパーティションの場合は、元のパーティションを複数のパーティションに分割し、新しい各パーティションを、データを提供するデータ ソース テーブルにマップします。  
  
 ビューおよび名前付きクエリはテーブルと機能的に同等です。これら 3 つのオブジェクトはすべて、DSV で定義され、[パーティション ソース] ダイアログ ボックスの [テーブル バインド] オプションを使用してパーティションにバインドされます。 ビューまたは名前付きクエリを作成して、各パーティションに必要なデータ セグメントを生成できます。 詳細については、「[データ ソース ビューでの名前付きクエリの定義 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)」を参照してください。  
  
> [!IMPORTANT]  
>  DSV で複数のパーティションに対して相互排他的な名前付きクエリを作成する場合は、パーティションの結合データに、キューブに含めるメジャー グループのデータがすべて含まれるようにしてください。 メジャー グループのテーブル全体に基づいた既定のパーティションを残さないようにしてください。残しておくと、パーティションに基づくクエリが、完全なテーブルに基づくクエリと重複します。  
  
1.  パーティション ソースとして使用する 1 つ以上の名前付きクエリを作成します。 詳細については、「[データ ソース ビューでの名前付きクエリの定義 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)」を参照してください。  
  
     名前付きクエリは、メジャー グループに関連付けられたファクト テーブルに基づいている必要があります。 たとえば、FactInternetSales メジャー グループをパーティション分割する場合、DSV の名前付きクエリでは FROM ステートメントで FactInternetSales テーブルを指定する必要があります。  
  
2.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のソリューション エクスプローラーで、キューブをダブルクリックしてキューブ デザイナーで開き、 **[パーティション]** タブをクリックします。  
  
3.  パーティションを追加するメジャー グループを展開します。  
  
4.  **[新しいパーティション]** をクリックして、パーティション ウィザードを開始します。 メジャー グループにバインドされたファクト テーブルを使用して名前付きクエリを作成した場合は、前の手順で作成した名前付きクエリがそれぞれ表示されます。  
  
5.  [基になる情報の指定] で、前の手順で作成した名前付きクエリの 1 つを選択します。 名前付きクエリが表示されない場合は、DSV に戻り、FROM ステートメントを確認します。  
  
6.  **[次へ]** をクリックして、以降の各ページで既定値をそのまま使用します。  
  
7.  最後の [ウィザードの完了] ページで、パーティションにわかりやすい名前を指定します。  
  
8.  **[完了]** をクリックします。  
  
9. 前の手順を繰り返して残りのパーティションを作成し、毎回次のデータ スライスを選択するように別の名前付きクエリを選択します。  
  
10. ソリューションを配置するかパーティションを処理して、データを読み込みます。 必ずすべてのパーティションを処理してください。  
  
11. キューブを参照して、正しいデータが返されていることを確認します。  
  
## <a name="next-step"></a>次の手順  
 パーティション用に相互排他的なクエリを作成する場合は、キューブに含めようとしたデータが結合後のパーティション データにすべて含まれていることを確認する必要があります。  
  
 最後に、通常、テーブル自体に基づいた既定のパーティション (まだ存在する場合) は削除してください。そうしないと、クエリ パーティションに基づいたクエリが、完全なテーブルに基づいたクエリと重複することになります。  
  
## <a name="see-also"></a>参照  
 [パーティションと &#40; です。Analysis Services - 多次元データと &#41; です。](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [リモート パーティション](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)   
 [Analysis Services & #40; 内のパーティションをマージします。SSAS - 多次元 & #41;](../../analysis-services/multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  