---
title: 登録済みサーバーまたは登録済みサーバー グループの名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-registration
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying registered server or server group names
- server groups [SQL Server]
- Registered Servers [SQL Server], names
- renaming registered server or server group
- names [SQL Server], registered server or server group
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9a1455eadba4fe4d8ec2072df8f5f5fc11f29ef
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33042049"
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>登録済みサーバーまたは登録済みサーバー グループの名前の変更
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、登録済みサーバーまたは登録済みサーバー グループの名前を変更する方法について説明します。 この名前はいつでも変更できます。 [登録済みサーバー] でサーバーの名前を変更すると、名前の表示のみが変更されます。 別のサーバーに接続するには、登録済みサーバーの接続プロパティを編集する必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
メニューから **[表示]\\[登録済みサーバー]** を選択し、**[登録済みサーバー]** ペインを開きます。  
#### <a name="to-change-the-name-of-a-server"></a>サーバーの名前を変更するには  
  
1.  **[登録済みサーバー]** の **[データベース エンジン]** 、 **[ローカル サーバー グループ]** の順に展開します。  

2.  サーバーを右クリックして **[プロパティ]** を選択し、 **[サーバー登録プロパティの編集]** ダイアログ ボックスを開きます。
  
3.  **[登録済みサーバーの名前]** テキスト ボックスにサーバーの新しい登録名を入力し、 **[保存]** をクリックします。  
  
#### <a name="to-change-the-name-of-a-server-group"></a>サーバー グループの名前を変更するには  
  
1.  **[登録済みサーバー]** の **[データベース エンジン]** 、 **[ローカル サーバー グループ]** の順に展開します。  

2.  サーバー グループを右クリックし、 **[プロパティ]** を選択して **[サーバー グループ プロパティの編集]** ダイアログ ボックスを開きます。 
  
3.  **[グループ名]** テキスト ボックスにサーバー グループの新しい名前を入力し、 **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [サーバーの登録の変更 &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)  
  
  
