---
title: "対象サーバーのポーリング間隔の設定 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 98961d875eaef7e6c941212780ddcb60b44d57ac
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="set-the-polling-interval-for-target-servers"></a>対象サーバーのポーリング間隔の設定
このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによってマスター サーバーから対象サーバーに対して情報が更新される頻度を設定する方法について説明します。 ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントで実行される特定の一連の処理のことです。 マルチサーバー ジョブとは、1 つ以上の対象サーバーでマスター サーバーにより実行されるジョブです。  
  
-   **作業を開始する準備:**  [セキュリティ](#Security)  
  
-   **対象サーバーのポーリング間隔を設定するために使用するもの:** [SQL Server Management Studio](#SSMS)、 [Transact-SQL](#TSQL)  
  
## <a name="BeforeYouBegin"></a>はじめに  
各対象サーバーは、同じジョブのインスタンスを同時に実行できます。 各対象サーバーからマスター サーバーに定期的にポーリングし、その対象サーバーに割り当てられた新しいジョブのコピーをダウンロードした後、切断します。 ダウンロードされたジョブは対象サーバーでローカルに実行され、マスター サーバーに再接続してジョブ結果状態をアップロードします。  
  
> [!NOTE]  
> 対象サーバーがジョブの状態をアップロードするときにマスター サーバーにアクセスできない場合、そのジョブの状態はマスター サーバーがアクセスできるようになるまでスプールされます。  
  
### <a name="Security"></a>セキュリティ  
詳細については、「 [SQL Server エージェントのセキュリティの実装](../../ssms/agent/implement-sql-server-agent-security.md) 」および「 [マルチサーバー環境に適した SQL Server エージェント サービス アカウントの選択](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)」を参照してください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
**対象サーバーのポーリング間隔を設定するには**  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[マルチ サーバーの管理]**をポイントして、 **[対象サーバーの管理]**をクリックします。  
  
3.  **[対象サーバーの状態]** タブで、 **[命令を通知]**をクリックします。  
  
4.  **[命令の種類]** ボックスの一覧で、 **[ポーリング間隔の設定]**を選択します。  
  
5.  **[ポーリング間隔]** ボックスに、対象サーバーがマスター サーバーをポーリングするまでの経過時間 (秒単位) を、10 ～ 28,800 までの範囲で入力します。  
  
6.  **[受信者]**で、次のいずれかの操作を行います。  
  
    1.  すべての対象サーバーで同じポーリング間隔を共有する場合は、 **[すべての対象サーバー]** をクリックします。  
  
    2.  すべての対象サーバーで同じポーリング間隔を共有しない場合は、 **[特定の対象サーバー]** をクリックし、このポーリング間隔を使用する対象サーバーを選択します。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
**対象サーバーのポーリング間隔を設定するには**  
  
1.  オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。  
  
2.  ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  クエリ ウィンドウで、 [sp_post_msx_operation (Transact-SQL)](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf) システム ストアド プロシージャを使用して対象サーバーのポーリング間隔を設定します。  
  
## <a name="see-also"></a>参照  
[sysdownloadlist](http://msdn.microsoft.com/en-us/71087a4c-e829-488e-aa7d-a9476e2b4779)  
  
