---
title: '[ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e089716aefc86c0a4753cb5bd0a0d3150101d725
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32957727"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a>[ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[ログ リーダー エージェントのセキュリティ]** ページを使用すると、各ピアでログ リーダー エージェントが実行され、接続するときに使用されるアカウントを指定できます。 エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)」および「[レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)」を参照してください。  
  
> [!NOTE]  
>  トランザクション レプリケーションを使用してパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントが存在します。 データベースにログ リーダー エージェントが既に設定されている場合 (このウィザードを以前に実行したときのパブリケーション、または同じデータベースにある他のトランザクション パブリケーションで)、使用されている資格情報をこのウィザードで変更することはできません。 新しい資格情報を指定した場合は無視されます。 資格情報を変更するには、 **[パブリケーションのプロパティ]** ダイアログ ボックスを使用します。 詳細については、「 [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
## <a name="options"></a>および  
 各ピアの行にあるプロパティ ボタン (**[...]**) をクリックすると、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスが開きます。 エージェントで使用されるアカウントに必要な権限の詳細については、 **[ログ リーダー エージェントのセキュリティ]** ダイアログ ボックスを開いて **[ヘルプ]** をクリックしてください。  
  
 このダイアログ ボックスに設定値を入力すると、サブスクライバーへの接続情報がグリッドに表示されます。  
  
 **[パブリッシャーのエージェント]**  
 各ピア サーバー インスタンスの名前です。  
  
 **[ピア データベース]**  
 各ピアでパブリケーション データベースおよびサブスクリプション データベースとして機能するデータベースです。  
  
 **[ディストリビューターへの接続]**  
 ディストリビューターに接続するコンテキストを作成します。 ディストリビューターへのローカル接続は常に、エージェントの実行に使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用して作成されます。そのため、このフィールドには常に **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** と表示されます。  
  
 **[パブリッシャーへの接続]**  
 パブリッシャーへの接続が作成されるときのコンテキストです。 パブリッシャーへの接続は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン、またはエージェントが実行される Windows アカウントのコンテキストを使用して作成できます。 フィールドには、**[ログイン '\<Login>' を使用する]**、**['\<Domain>\\<Login\>' の権限を借用する]**、**['\<Computer>\\<Login\>' の権限を借用する]** のうちの 1 つが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [ピア ツー ピア トポロジの管理 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [@loopback_detection](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
