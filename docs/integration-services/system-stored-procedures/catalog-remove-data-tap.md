---
title: "catalog.remove_data_tap |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2f2c9b5d9333c201120e5f3a3e392c59012a8ac7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogremovedatatap"></a>catalog.remove_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  実行内のコンポーネント出力からデータ タップを削除します。 データ タップの一意な識別子が実行のインスタンスに関連付けられています。  
  
## <a name="syntax"></a>構文  
  
```tsql  
remove_data_tap [ @data_tap_id = ] data_tap_id  
  
```  
  
## <a name="arguments"></a>引数  
 [ @data_tap_id =] *data_tap_id*  
 catalog.add_data_tap ストアド プロシージャを使用して作成されるデータ タップの一意識別子。 *Data_tap_id*は**bigint**です。  
  
## <a name="remarks"></a>解説  
 パッケージに同じ名前の複数のデータ フロー タスクが含まれる場合、データ タップは指定された名前で最初に見つかったデータ フロー タスクに追加されます。  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 データを削除するには、タップ、実行のインスタンスが作成された状態である必要があります (1 の値、**ステータス**の列、 [catalog.operations & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)ビュー)。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   ユーザーに MODIFY 権限がない。  
  
## <a name="see-also"></a>参照  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  