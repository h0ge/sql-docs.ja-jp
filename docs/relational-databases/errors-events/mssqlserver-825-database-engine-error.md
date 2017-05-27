---
title: MSSQLSERVER_825 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6cf3cceebd5555e91d3753e385d28164680241f5
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver825"></a>MSSQLSERVER_825
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|825|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|B_RETRYWORKED|  
|メッセージ テキスト|ファイル '%ls' のオフセット %#016I64x での読み取りは、読み取りに %d 回失敗 (エラー: %ls) した後で成功しました。 SQL Server エラー ログとシステム イベント ログ内の別のメッセージで詳細情報が報告されることもあります。 このエラー状態はデータベースの整合性を損なうので、解決する必要があります。 完全なデータベース整合性確認 (DBCC CHECKDB) を完了させてください。 このエラーには多くの要因があります。詳細については、SQL Server オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
このメッセージは、読み取り操作が少なくとも 1 回は再実行されたことを示し、ディスク ハードウェアに大きな問題があることを示しています。 このメッセージは、現時点では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の問題を示していませんが、ディスクの問題を解決しないと、データの損失やデータベースの破損につながる可能性があります。 システム イベント ログに、問題の診断に役立つ関連するイベントが含まれている場合があります。 I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?LinkId=69370)」 (Microsoft SQL Server I/O の基礎 (第 2 章)) を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
次の操作を行って、原因となっている問題を特定し、解決してください。  
  
-   このメッセージのエラー ログと変数テキストを確認し、問題の原因を明らかにする手掛かりを見つける。  
  
-   ディスク システムを確認してください。 この問題は、ディスク、ディスク コントローラー、アレイ カード、またはディスク ドライバーに関連している可能性があります。  
  
-   ディスク システムの状態を調べる最新のユーティリティがあるかどうか、ディスクの製造元に問い合わせる。  
  
-   ドライバーの最新の更新があるかどうか、ディスクの製造元に問い合わせる。  
  
