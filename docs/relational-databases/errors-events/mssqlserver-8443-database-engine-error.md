---
title: MSSQLSERVER_8443 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 73c081a442b39c71b44c817db616c6eca360ece0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8443|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SB_DIALOG_WO_CONV_GROUP|  
|メッセージ テキスト|ID '%.*ls' のメッセージ交換と発信側: %d は存在しないメッセージ交換グループ '%.\*ls' を参照しています。 DBCC CHECKDB を実行して、データベースを分析し、修復してください。|  
  
## <a name="explanation"></a>説明  
メタデータ層から、メッセージ交換グループに対して NULL が返されました。 なんらかの形でデータベースが破損しています。 考えられる原因の 1 つは、ディスク エラーです。  
  
## <a name="user-action"></a>ユーザーの操作  
修復モードで DBCC CHECKDB を実行し、データベースを一貫性のある状態に戻します。 一貫性のある状態を復元するために必要であれば、メッセージは削除される場合があります。 システム エラー ログで、システム内の別の障害が原因でこのエラーが生じていないか調べてください。  
  
