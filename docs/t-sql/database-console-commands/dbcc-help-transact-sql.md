---
title: "DBCC HELP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC HELP
- DBCC_HELP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC statement syntax information
- DBCC HELP statement
ms.assetid: 306092c6-4354-4e47-928b-606124fbdc6e
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2fd6f0e7ef5c74c3a3f8fc2af9424a2996dfcd98
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-help-transact-sql"></a>DBCC HELP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

指定された DBCC コマンドに関する構文情報を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC HELP ( 'dbcc_statement' | @dbcc_statement_var | '?' )  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
 *dbcc_statement* | *@dbcc_statement_var*  
 構文情報を取得する DBCC コマンドの名前を指定します。 DBCC コマンドの "DBCC" より後の部分のみを指定します (たとえば、DBCC CHECKDB ではなく CHECKDB と指定します)。  
  
 ?  
 ヘルプ情報を取得できるすべての DBCC コマンドを返します。  
  
 WITH NO_INFOMSGS  
 重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="result-sets"></a>結果セット  
DBCC HELP は、指定された DBCC コマンドの構文を示す結果セットを返します。
  
## <a name="permissions"></a>Permissions  
**sysadmin** 固定サーバー ロールのメンバーシップが必要です。
  
## <a name="examples"></a>使用例  
### <a name="a-using-dbcc-help-with-a-variable"></a>A. DBCC HELP と変数  
次の例では、DBCC `CHECKDB` に関する構文情報を返します。
  
```sql  
DECLARE @dbcc_stmt sysname;  
SET @dbcc_stmt = 'CHECKDB';  
DBCC HELP (@dbcc_stmt);  
GO  
```  
  
### <a name="b-using-dbcc-help-with-the--option"></a>B. DBCC HELP と ?  オプション  
次の例は、ヘルプ情報を取得できるすべての DBCC ステートメントを返します。
  
```sql  
DBCC HELP ('?');  
GO  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
