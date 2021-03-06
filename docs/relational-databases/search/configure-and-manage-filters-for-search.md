---
title: 検索用フィルターの構成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.component: search
ms.reviewer: ''
ms.suite: sql
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d5581011c38ace01ab61acf62c1d084893d8b9de
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33178378"
---
# <a name="configure-and-manage-filters-for-search"></a>検索用フィルターの構成と管理
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **varbinary**、**varbinary(max)**、**image**、または **xml** データ型列のドキュメントにインデックスを作成するには、追加の処理が必要です。 この処理はフィルターによって実行します。 フィルターは、ドキュメントから (フォーマットを解除して) 文字情報を抽出します。 次に、テーブル列に関連付けられている言語のワード ブレーカー コンポーネントにテキストを送ります。  
 
## <a name="filters-and-document-types"></a>フィルターおよびドキュメントの種類
フィルターは、ドキュメント型 (.doc、.pdf、.xls、.xml など) に固有です。 これらのフィルターは IFilter インターフェイスを実装しています。 ドキュメント型の一覧を参照するには、 [sys.fulltext_document_types](../../relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql.md) カタログ ビューに対してクエリを実行してください。  
  
バイナリ ドキュメントは、単一の **varbinary(max)** 列または **image** 列に格納できます。 各ドキュメントについて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はファイル拡張子を基に正しいフィルターを選択します。 ファイルが **varbinary(max)** 列または **image** 列に格納されている場合にはファイル拡張子が表示されないため、ファイル拡張子 (.doc、.xls、.pdf など) を型列と呼ばれるテーブル内の別の列に格納する必要があります。 この型列は、任意の文字ベースのデータ型で、文書ファイルの拡張子 (たとえば [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word 文書の場合は .doc) を格納します。 **の** Document [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]テーブルでは、 **Document** 列は型 **varbinary(max)**、型列 **FileExtension**は型 **nvarchar(8)** です。  

**既存のフルテキスト インデックスの型列を表示するには**  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
  
> [!NOTE]  
>  フィルターは、実装によっては、親オブジェクトに埋め込まれたオブジェクトを処理できます。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、フィルターが他のオブジェクトへのリンクをたどるように構成されていません。  

## <a name="installed-filters"></a>インストールされているフィルター 
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、独自の XML フィルターと HTML フィルターがインストールされます。 さらに、オペレーティング システムに既にインストールされている [!INCLUDE[msCoName](../../includes/msconame-md.md)] 専用形式 (.doc、.xdoc、.ppt など) のフィルターもすべて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み込まれます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに現在読み込まれているフィルターを確認するには、次のように [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) ストアド プロシージャを使用します。  
  
```sql
EXEC sp_help_fulltext_system_components 'filter';   
```  
## <a name="non-microsoft-filters"></a>Microsoft 以外のフィルター
ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 形式以外のフィルターを使用するには、事前にこれらのフィルターをサーバー インスタンスに読み込む必要があります。 追加のフィルターのインストールの詳細については、「 [登録済みのフィルターおよびワード ブレーカーの表示または変更](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)」を参照してください。  
  
  
## <a name="see-also"></a>参照  
 [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [FILESTREAM と SQL Server のその他の機能との互換性](../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
