---
title: srv_rpcoptions (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_rpcoptions
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dab1afd35dd8e3f0b8336e8d839b0747e47385c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32935548"
---
# <a name="srvrpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 現在のリモート ストアド プロシージャの実行時オプションを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
## <a name="returns"></a>戻り値  
 現在のリモート ストアド プロシージャの実行時フラグを論理 OR で結合して格納したビットマップを返します。 リモート ストアド プロシージャがない場合は、0 を返し、メッセージを生成します。  
  
## <a name="remarks"></a>Remarks  
 次の表では、各実行時フラグについて説明します。  
  
|実行時フラグ|Description|  
|--------------------|-----------------|  
|SRV_NOMETADATA|クライアントがメタデータ情報なしの結果を要求したことを示します。 このフラグが使用されるのは、クライアントと [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが通信中である場合だけです。 拡張ストアド プロシージャ API アプリケーションではメタデータ情報を省略できません。|  
|SRV_RECOMPILE|クライアントがリモート ストアド プロシージャの実行前に再コンパイルを要求していることを示します。 このフラグは、拡張ストアド プロシージャ API アプリケーションには適用できません。|  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
