---
title: MSSQLSERVER_8710 | Microsoft Docs
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
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8b4444dc2ed1b239670c75321ec3a0e1401122a0
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|8710|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|メッセージ テキスト|CUBE、ROLLUP、または GROUPING SET クエリで使用される集計関数は、サブ集計をマージするものである必要があります。 この問題を解決するには、集計関数を削除するか、UNION ALL を GROUP BY 句で使用するクエリを記述してください。|  
  
## <a name="explanation"></a>説明  
サブ集計をマージできない集計関数が CUBE、ROLLUP、または GROUPING SET で使用されています。  
  
## <a name="user-action"></a>ユーザーの操作  
この問題を解決するには、集計関数を削除するか、UNION ALL を GROUP BY 句で使用するクエリを記述してください。  
  
