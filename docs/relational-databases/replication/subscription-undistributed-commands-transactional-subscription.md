---
title: サブスクリプション、[未配布のコマンド] (トランザクション サブスクリプション) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f1fc8bf53c8a96c7669d157a73716b968d57f859
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32960677"
---
# <a name="subscription-undistributed-commands-transactional-subscription"></a>サブスクリプション、[未配布のコマンド] (トランザクション サブスクリプション)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **[未配布のコマンド]** タブには、ディストリビューション データベース内のコマンドで、選択したサブスクライバーにまだ配布されていないコマンドの数や、これらのコマンドを配布するのに要すると推定される時間についての情報が表示されます。 ディストリビューション データベース内のコマンドを表示する方法については、「[sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[このサブスクライバーへの適用を待機しているディストリビューション データベース内のコマンド数]**  
 ディストリビューション データベース内のコマンドで、選択したサブスクライバーにまだ配布されていないコマンドの数を示します。 コマンドは、1 つの Transact-SQL データ操作言語 (DML) ステートメントまたは 1 つのデータ定義言語 (DDL) ステートメントから構成されます。  
  
 **[以前のパフォーマンスに基づく、これらのコマンドの適用にかかる推定時間]**  
 コマンドをサブスクライバーに配布するのに要すると推定される時間を示します。 スナップショットを生成してサブスクライバーに適用するのに必要な時間よりもこの値が大きい場合は、サブスクライバーの再初期化を検討してください。 詳細については、「 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [レプリケーション モニターを使用したパフォーマンスの監視](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
