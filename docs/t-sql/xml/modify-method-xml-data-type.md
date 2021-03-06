---
title: modify() メソッド (xml データ型) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|xml
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modify() method
- modify method
ms.assetid: 52430735-51f4-46d1-a308-9aecf8648fda
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 01ad2afc24c09cdd6a05189335f1e0d6827d24c4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33067389"
---
# <a name="modify-method-xml-data-type"></a>modify() メソッド (xml データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML ドキュメントのコンテンツを変更します。 **xml** 型の変数または列のコンテンツを変更するには、このメソッドを使用します。 このメソッドは XML DML ステートメントを使用して、XML データのノードの挿入、更新、削除を行います。 **xml** データ型の **modify()** メソッドは、UPDATE ステートメントの SET 句内でしか使用できません。  
  
## <a name="syntax"></a>構文  
  
```  
  
modify (XML_DML)  
```  
  
## <a name="arguments"></a>引数  
 XML_DML  
 XML DML (データ操作言語) の文字列です。 XML ドキュメントは、この表記に従って更新されます。  
  
> [!NOTE]  
>  **modify()** メソッドが NULL 値を使用して呼び出される場合、または結果が NULL 値になる場合、エラーが返されます。  
  
## <a name="examples"></a>使用例  
 **modify()** メソッドには XML データ操作言語 (DML) の文字列が必要なので、**modify()** のサンプルは XML DML ステートメントについて説明するトピックに含まれています。 これらの例については、「[&#40;XML DML&#41; の挿入](../../t-sql/xml/insert-xml-dml.md)」、「[&#40;XML DML&#41; の削除](../../t-sql/xml/delete-xml-dml.md)」、および「[&#40;XML DML&#41; の値の置き換え](../../t-sql/xml/replace-value-of-xml-dml.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
