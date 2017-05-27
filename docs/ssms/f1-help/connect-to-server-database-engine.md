---
title: "[サーバーへの接続] (データベース エンジン) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connectoserverunknownservertype.f1
- sql13.swb.connection.login.sqlce.f1
- sql13.swb.connecttoce.f1
- SQL13.SWB.CONNECTION.LOGIN.SQLSERVER.F1
- sql13.swb.connection.login.sqlserver.f1
- sql13.swb.manageSS2k.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d421bcb09ec7ebde28b5d1cce6eca2263cfb1c48
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-database-engine"></a>[サーバーへの接続] \(データベース エンジン)
このダイアログを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] に接続するときのオプションを表示または指定できます。 ほとんどの場合、 **[サーバー名]** ボックスにデータベース サーバーのコンピューター名を入力し、 **[接続]**をクリックすることで接続できます。 [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)]に接続している場合、コンピューター名の後に **\sqlexpress**を付けて使用します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続する機能に影響する要因は多数あります。  
  
## <a name="options"></a>オプション  
**サーバーの種類**  
オブジェクト エクスプローラーからサーバーを登録するときは、接続するサーバーの種類 ( [!INCLUDE[ssDE](../../includes/ssde_md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]、または [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]) を選択します。 ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。 [登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。 別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../../includes/ssde_md.md)]]、[ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]]、[ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]]、[ [!INCLUDE[ssEW](../../includes/ssew_md.md)]]、または [ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)] ] をクリックします。  
  
**[サーバー名]**  
接続するサーバー インスタンスを選択します。 既定では、最後に接続していたサーバー インスタンスが表示されます。  
  
> [!NOTE]  
> [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] のアクティブなユーザー インスタンスに接続するには、パイプ名を指定した名前付きパイプ プロトコル (np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query など) を使用して接続します。詳細については、 [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] のドキュメントを参照してください。  
  
**[認証]**  
[!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続する際には、2 つの認証モードのいずれかを選択します。  
  
**[Windows 認証]**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。  
  
**SQL Server 認証 (SQL Server 認証 (SQL Server Authentication))**  
指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] にログイン アカウントが設定されていない場合、認証は失敗し、エラー メッセージが返されます。  
  
> [!IMPORTANT]  
> 可能であれば、Windows 認証または Active Directory パスワード認証を使用します。  
  
**Active Directory ユニバーサル認証**  
Active Directory ユニバーサル認証は、Azure Multi-Factor Authentication (MFA) をサポートする対話型ワークフローです。 Azure MFA を使えば、簡単なサインイン プロセスというユーザーの要求を満たしながら、データとアプリケーションへのアクセスを保護できます。 電話、テキスト メッセージ、スマート カードと PIN、モバイル アプリ通知などの簡単な検証オプションで強力な認証を提供し、ユーザーが好みの方法を選択できるようにします。 ユーザー アカウントが MFA 用に構成されている場合の対話型認証ワークフローでは、ポップアップ ダイアログ ボックスやスマート カードなどを使用する追加のユーザー対話が必要です。ユーザー アカウントが MFA 用に構成されている場合、ユーザーは Azure ユニバーサル認証を選択して接続する必要があります。 ユーザー アカウントに MFA が必要ない場合は、ユーザーは他の 2 つの Azure Active Directory 認証オプションを使用できます。 詳細については、「 [SQL Database と SQL Data Warehouse での Azure AD MFA のための SSMS のサポート](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/)」をご覧ください。 SSMS バージョン 16.3 (August 2016) 以降が必要です。

**Active Directory パスワード認証**  
Azure Active Directory 認証は、Azure Active Directory (Azure AD) の ID を使用して [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] に接続するメカニズムです。  Azure とフェデレーションされていないドメインから資格情報を使用して Windows にログインしている場合、あるいは初期ドメインまたはクライアント ドメインに基づく Azure AD を使用する Azure AD 認証を使用している場合は、 [!INCLUDE[ssSDS](../../includes/sssds_md.md)] への接続にこの方法を使用します。 詳細については、「 [Azure Active Directory 認証を使用して SQL Database に接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)」を参照してください。  
  
**Active Directory 統合認証**  
Azure Active Directory 認証は、Azure Active Directory (Azure AD) の ID を使用して [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] に接続するメカニズムです。 フェデレーション ドメインから Azure Active Directory の資格情報を使用して Windows にログインしている場合は、この方法を使用して [!INCLUDE[ssSDS](../../includes/sssds_md.md)] に接続します。 詳細については、「 [Azure Active Directory 認証を使用して SQL Database に接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)」を参照してください。  
  
**ユーザー名**  
接続に使用する Windows ユーザー名です。 このオプションは、 **Active Directory パスワード認証**を使用した接続が指定されている場合にのみ使用できます。 **Windows 認証**を選択した場合は読み取り専用です。  
  
**Login**  
接続に使用するログインを入力します。 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証または Active Directory パスワード認証を使用した接続が指定されている場合にのみ使用できます。  
  
**Password**  
ログインのパスワードを入力します。 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証または Active Directory パスワード認証を使用した接続が指定されている場合にのみ編集できます。  
  
**[接続]**  
クリックすると、上記で選択したサーバーに接続します。  
  
**オプション**  
クリックすると、サーバーの登録やパスワードの保存など、追加のサーバー接続オプションが表示されます。  
  
