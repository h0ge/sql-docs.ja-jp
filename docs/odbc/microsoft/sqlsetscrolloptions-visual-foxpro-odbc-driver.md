---
title: SQLSetScrollOptions (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81542e2e2187872725bd4db5f5922dbbefb2f944
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901877"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 部分的な  
  
 ODBC API への準拠: レベル 2  
  
 ステートメント ハンドルに関連付けられているカーソルの動作を制御するオプションを設定*hstmt*です。  
  
 Visual FoxPro ODBC ドライバーは、のみ SQL_CONCUR_READ_ONLY; をサポートしています。サポートされていません、 *fConcurrency* SQL_CONCUR_ROWVER の値します。 ドライバーは SQL_KEYSET_SIZE、SQL_CURSOR_DYNAMIC、および SQL_CURSOR_KEYSET_DRIVEN を警告 ODBC_01S02 SQL_SCROLL_STATIC に変換します。  
  
 詳細については、次を参照してください。 [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)で、 *ODBC プログラマ リファレンス*です。
