---
title: ログ シーケンス番号への復旧 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
caps.latest.revision: 38
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 441daeb74bcc141c148edef396b04bf75aff3f0f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32920327"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a>ログ シーケンス番号への復旧 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用するデータベースのみに関連しています。  
  
 ログ シーケンス番号 (LSN) を使用して、復元操作の復旧ポイントを定義できます。 ただし、この機能はツール ベンダーを対象としたものであり、一般的には、あまり有益ではない場合があります。  
  
##  <a name="LSNs"></a> ログ シーケンス番号の概要  
 LSN は、RESTORE シーケンス中に、データを復元する時点を追跡するために内部で使用されます。 バックアップを復元するときに、データはバックアップが実行された時点に対応する LSN まで復元されます。 差分バックアップとログ バックアップの場合、復元されるデータベースは LSN が大きい方、つまり、より後の時点に向かって進められます。  
  
 トランザクション ログのすべてのレコードは、ログ シーケンス番号 (LSN) によって一意に識別されます。 LSN の順序は、LSN2 が LSN1 より大きい場合、LSN2 によって参照されるログ レコードで示される変更が、ログ レコード LSN1 で示される変更の後に行われたようになっています。  
  
 重要なイベントが発生した時点のログ レコードの LSN を、正しい復元シーケンスの構築に役立てることができます。 LSN は順序付けられているので、等号または不等号 ( **\<**、 **>**、 **=**, **\<=**、 **>=**) を使用して比較できます。 このような比較は、復元シーケンスを構築するときに役立ちます。  
  
> [!NOTE]  
>  LSN は、データ型 **numeric**(25,0) の値です。 算術演算 (加算や減算など) は、意味が無いので LSN では行わないでください。  
  
  
## <a name="viewing-lsns-used-by-backup-and-restore"></a>バックアップと復元で使用される LSN の表示  
 特定のバックアップと復元イベントが発生したログ レコードの LSN は、次の 1 つ以上の方法を使用して表示できます。  
  
-   [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)、 [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
-   [RESTORE HEADERONLY](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
  
-   [RESTORE FILELISTONLY](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
  
> [!NOTE]  
>  LSN は、一部のメッセージ テキストにも表示されます。  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a>LSN に復元するための Transact-SQL 構文  
 [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) ステートメントを使用して、次のように LSN または LSN の直前まで復元できます。  
  
-   WITH STOPATMARK **='** lsn:*<lsn_number>***'** 句を使用します。ここで、lsn:*\<lsnNumber>* は、指定された LSN が含まれるログ レコードが復旧ポイントであることを指定する文字列です。  
  
     STOPATMARK によって LSN までロールフォワードされ、そのログ レコードがロールフォワードに含められます。  
  
-   WITH STOPBEFOREMARK **='** lsn:*<lsn_number>***'** 句を使用します。ここで、lsn:*\<lsnNumber>* は、指定した LSN 番号が含まれるログ レコードの直前のログ レコードが、復旧ポイントであることを指定する文字列です。  
  
     STOPBEFOREMARK では、LSN までロールフォワードされますが、指定されたログ レコードはロールフォワードから除外されます。  
  
 通常は、包含または除外する特定のトランザクションを選択します。 実際には必要ありませんが、指定するログ レコードはトランザクション コミット レコードです。  
  
## <a name="examples"></a>使用例  
 次の例では、完全復旧モデルを使用するように `AdventureWorks` データベースが変更されていることを想定しています。  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [SSMS を使用してデータベース バックアップを復元する](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [完全復旧モデルで障害発生時点までデータベースを復元する &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)  
  
-   [マークされたトランザクションへのデータベースの復元 &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a>参照  
 [トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
