---
title: タイプ Id |Microsoft ドキュメント
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
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87bf03fca6ccf3a5066d2aaeaff5bebd28c005b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914677"
---
# <a name="type-identifiers"></a>型識別子
ODBC SQL と C データ型を記述するには 2 つのセットを定義します*タイプ id*です。 型識別子では、SQL 列、または C バッファーの種類について説明します。 **#Define**値しは一般に関数の引数として渡されるまたはメタデータに返されます。  
  
 たとえば、次の呼び出し**SQLBindParameter** SQL_DATE_STRUCT の型の変数を SQL ステートメントで日付のパラメーターにバインドします。 C 型識別子 SQL_C_TYPE_DATE の種類を指定する、*日付*変数、および SQL 型識別子 SQL_TYPE_DATE 動的パラメーターの型を指定します。  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
