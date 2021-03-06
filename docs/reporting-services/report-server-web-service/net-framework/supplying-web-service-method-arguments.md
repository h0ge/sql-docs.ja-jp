---
title: Web サービス メソッドの引数の指定 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a273ce7fb8ddcb53545c4fe95db8e6062a1e5b45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33025409"
---
# <a name="supplying-web-service-method-arguments"></a>Web サービス メソッドの引数の指定
  レポート サーバー Web サービスのメソッドは、SOAP を使用し、HTTP 経由で特定の URL のサービスに対して要求を送信します。 サービスでは、要求を受信し、処理した後、応答を返します。 これらの要求と応答は XML ドキュメント形式です。  
  
## <a name="optional-parameters"></a>省略可能なパラメーター  
 場合によっては、Web サービス メソッドに省略可能な入力パラメーターがあります。 Web サービス メソッドの入力パラメーターが省略可能である場合でも、そのパラメーターを含め、パラメーター値を **null** ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の場合は **Nothing**) に設定する必要があります。 パラメーター値を **null** に設定すると、SOAP 要求でそのパラメーターの要素値は **null** に設定されます。  
  
 次の例では、<xref:ReportService2010.ReportingService2010.CreateFolder%2A> メソッドを使用して、Sales フォルダーに Product Sales という新しいフォルダーを作成します。 フォルダー プロパティに **null** 値を指定することで、フォルダーにユーザー固有のプロパティは指定されません。  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>複合データ型  
 レポート サーバー Web サービスのコア クラスは <xref:ReportService2010.ReportingService2010> です。このクラスは、プロキシ クラスの SOAP 操作または Web メソッドを呼び出すときに使用します。 このクラスとメソッドをサポートするため、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には、Web サービス メソッドの入出力パラメーターに固有であるユーザー定義の複合データ型が含まれます。 このような複合データ型は生成されるプロキシ クラスの一部であり、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 環境で開発するときに使用できます。  
  
 プロキシ クラスを生成すると、WSDL ファイルに定義された複合データ型はプロキシのクラスによって表されます。このクラスには、複合データ型のさまざまな SOAP 要素に対応するプロパティが入っています。 一連の複合データ型は、コードで列挙できるオブジェクトの配列になります。 したがって、SOAP メッセージで送信された XML 構造を直接扱う必要がなくなります。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、自動的に変換が行われます。  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
