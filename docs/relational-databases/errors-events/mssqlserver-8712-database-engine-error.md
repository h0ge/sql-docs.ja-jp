---
title: MSSQLSERVER_8712 | Microsoft Docs
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
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 65489fa755c5dda3459d7de227631591f821e5bd
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8712|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|USEPLAN_ERR_NO_INDEX|  
|メッセージ テキスト|USE PLAN ヒントで指定したインデックス '%.*ls' が存在しません。 既存のインデックスを指定するか、指定した名前を持つインデックスを作成してください。|  
  
## <a name="explanation"></a>説明  
USE PLAN ヒントで指定したインデックスが存在しません。  
  
## <a name="user-action"></a>ユーザーの操作  
USE PLAN ヒントで指定したすべてのインデックスが存在することを確認します。  
  
## <a name="see-also"></a>参照  
[クエリ ヒント &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
  
