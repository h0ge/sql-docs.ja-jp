---
title: データベース ミラーリングの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-mirroring
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- removing database mirroring [SQL Server]
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
caps.latest.revision: 42
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 17d13bf98a6a558690f15aff3237fa405f0cbcdb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="remove-database-mirroring-sql-server"></a>データベース ミラーリングの削除 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベースからデータベース ミラーリングを削除する方法について説明します。  データベース所有者は、データベースからミラーリングを削除することで、いつでも手動でデータベース ミラーリング セッションを停止できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **データベース ミラーリングの削除に使用するツール:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:**  [データベース ミラーリングを削除した後](#FollowUp)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 データベースに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-remove-database-mirroring"></a>データベース ミラーリングを削除するには  
  
1.  データベース ミラーリング セッション中にプリンシパル サーバー インスタンスに接続します。次に、オブジェクト エクスプローラーで、サーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[データベース]** を展開し、データベースを選択します。  
  
3.  データベースを右クリックして **[タスク]** をポイントし、 **[ミラー]** をクリックします。 **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。  
  
4.  **[ページの選択]** ペインの **[ミラーリング]** をクリックします。  
  
5.  ミラーリングを削除するには、 **[ミラーリングの削除]** をクリックします。 確認を求めるメッセージが表示されます。 **[はい]** をクリックすると、セッションが停止し、データベースからミラーリングが削除されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 データベース ミラーリングを削除するには、 **[データベースのプロパティ]** を使用します。 **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページを使用します。  
  
#### <a name="to-remove-database-mirroring"></a>データベース ミラーリングを削除するには  
  
1.  いずれかのミラーリング パートナーの [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     *database_name* は、削除するセッションのミラー化されたデータベースです。  
  
     次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースからデータベース ミラーリングを削除します。  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="FollowUp"></a> 補足情報: データベース ミラーリングの削除  
  
> [!NOTE]  
>  ミラーリングの削除による影響の詳細については、「[データベース ミラーリングの削除 &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md)」を参照してください。  
  
-   **データベースでミラーリングを再開する場合**  
  
     ミラーリングを再開する前に、ミラーリングが削除された後にプリンシパル データベースで作成されたログ バックアップをすべて、ミラー データベースに適用する必要があります。  
  
-   **ミラーリングを再開しない場合**  
  
     必要に応じて、以前のミラー データベースを復旧できます。 以前にミラー サーバーだったサーバー インスタンスで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用できます。  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  このデータベースを復旧すると、異なる 2 つのデータベースが同じ名前でオンラインになります。 そのため、クライアントがどちらか一方のデータベース (通常は最新のプリンシパル データベース) にしかアクセスできないようにする必要があります。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [データベース ミラーリング セッションを一時停止または再開する &#40;SQL Server&#41;](../../database-engine/database-mirroring/pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
-   [データベース ミラーリング セッションからのミラーリング監視サーバーの削除 &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する方法 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database-mirroring-establish-session-windows-authentication.md)  
  
-   [証明書を使用したデータベース ミラーリングの設定の例 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [データベース ミラーリングの設定 &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
