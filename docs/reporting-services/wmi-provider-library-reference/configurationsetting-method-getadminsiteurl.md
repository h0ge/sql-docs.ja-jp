---
title: "GetAdminSiteUrl メソッド (WMI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
caps.latest.revision: 14
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ae40992c6a864a73bb758a3ce336624917a68a96
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="configurationsetting-method---getadminsiteurl"></a>GetAdminSiteUrl ConfigurationSetting メソッド
  レポート サーバーが統合されている Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ファームのサーバー管理 Web サイトの絶対 URL を取得します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *AdminSiteUrl*  
 [out] レポート サーバーが統合されている SharePoint ファームのサーバー管理 Web サイトの絶対 URL を表す文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メソッド](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-methods.md)  
  
  