---
title: 基本的な ODBC アプリケーションの手順 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC]
- application process [ODBC], about application process
ms.assetid: a92d1f78-c669-47ad-88c4-0b1a93503dfc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45b9c9b028e6cc3c380ea8f0da754cebb0f860d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908367"
---
# <a name="basic-odbc-application-steps"></a>基本的な ODBC アプリケーションのステップ
このセクションでは、ODBC アプリケーションの全体的な流れについて説明します。 可能性はほとんどありませんが、任意のアプリケーションを呼び出すすべてこれらの関数のこの順序で。 ただし、ほとんどのアプリケーションは、次の手順のいくつかのバリエーションを使用します。 アプリケーションの基本手順は、次の図に表示されます。  
  
 ![ODBC アプリケーションの基本的な手順](../../../odbc/reference/develop-app/media/pr10.gif "pr10")  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ステップ 1: データ ソースへの接続](../../../odbc/reference/develop-app/step-1-connect-to-the-data-source.md)  
  
-   [ステップ 2: アプリケーションの初期化](../../../odbc/reference/develop-app/step-2-initialize-the-application.md)  
  
-   [ステップ 3: SQL ステートメントのビルドと実行](../../../odbc/reference/develop-app/step-3-build-and-execute-an-sql-statement.md)  
  
-   [ステップ 4a: 結果のフェッチ](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)  
  
-   [ステップ 4b: 行数のフェッチ](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)  
  
-   [ステップ 5: トランザクションのコミット](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)  
  
-   [ステップ 6: データ ソースからの切断](../../../odbc/reference/develop-app/step-6-disconnect-from-the-data-source.md)
