---
title: プログラムによる WMI プロバイダーへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 11/02/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 67bd266b-1484-4863-8152-060a993420a9
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: fdea3dd2704ec7db762e74e39f3458072b008d15
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="accessing-the-wmi-provider-programmatically"></a>プログラムによる WMI プロバイダーへのアクセス

## <a name="wmi-provider-overview"></a>WMI プロバイダーの概要  
 このトピックに示すコード サンプルで [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の情報を取得するために使用する名前空間は、**System.Management** 名前空間です。これは [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] にあります。 **System.Management** 名前空間により、管理情報にアクセスしてその情報を操作するときに [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] アプリケーションで使用するマネージ コード クラスのセットが提供されます。 **System.Management** 名前空間による Reporting Services の WMI クラスの使用の詳細については、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK の「System.Management による管理情報へのアクセス」を参照してください。  
  
## <a name="finding-a-report-server-instance"></a>レポート サーバー インスタンスの検索  
 レポート サーバーのインストールの情報を検索するさらに適切な方法は、WMI インスタンスのコレクションを使用して列挙することです。 以下の例は、コレクションを作成し、コレクションによってループしてプロパティを表示することによって、レポート サーバー インスタンスごとにプロパティを検索する方法を示します。  
  
```vb  
Imports System  
Imports System.Management  
Imports System.IO  
  
Module Module1  
    Sub Main()  
        Const WmiNamespace As String = "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin"  
        Const WmiRSClass As String = _  
           "\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v13\admin:MSReportServer_ConfigurationSetting"  
  
        Dim serverClass As ManagementClass  
        Dim scope As ManagementScope  
        scope = New ManagementScope(WmiNamespace)  
        'Connect to the Reporting Services namespace.  
        scope.Connect()  
  
        'Create the server class.  
        serverClass = New ManagementClass(WmiRSClass)  
        'Connect to the management object.  
        serverClass.Get()  
        If serverClass Is Nothing Then Throw New Exception("No class found")  
  
        'Loop through the instances of the server class.  
        Dim instances As ManagementObjectCollection = serverClass.GetInstances()  
        Dim instance As ManagementObject  
        For Each instance In instances  
            Console.Out.WriteLine("Instance Detected")  
            Dim instProps As PropertyDataCollection = instance.Properties  
            Dim prop As PropertyData  
            For Each prop In instProps  
                Dim name As String = prop.Name  
                Dim val As Object = prop.Value  
                Console.Out.Write("Property Name: " + name)  
                If val Is Nothing Then  
                    Console.Out.WriteLine("     Value: <null>")  
                Else  
                    Console.Out.WriteLine("     Value: " + val.ToString())  
                End If  
            Next  
        Next  
  
        Console.WriteLine("--- Press any key ---")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Management;  
using System.IO;  
[assembly: CLSCompliant(true)]  
  
class Class1  
{  
    [STAThread]  
    static void Main(string[] args)  
    {  
        const string WmiNamespace = @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v10\Admin";  
        const string WmiRSClass =  
          @"\\<ServerName>\root\Microsoft\SqlServer\ReportServer\<InstanceName>\v13\admin:MSReportServer_ConfigurationSetting";  
        ManagementClass serverClass;  
        ManagementScope scope;  
        scope = new ManagementScope(WmiNamespace);  
  
        // Connect to the Reporting Services namespace.  
        scope.Connect();  
        // Create the server class.  
        serverClass = new ManagementClass(WmiRSClass);  
        // Connect to the management object.  
        serverClass.Get();  
        if (serverClass == null)  
            throw new Exception("No class found");  
  
        // Loop through the instances of the server class.  
        ManagementObjectCollection instances = serverClass.GetInstances();  
  
        foreach (ManagementObject instance in instances)  
        {  
            Console.Out.WriteLine("Instance Detected");  
            PropertyDataCollection instProps = instance.Properties;  
            foreach (PropertyData prop in instProps)  
            {  
                string name = prop.Name;  
                object val = prop.Value;  
                Console.Out.Write("Property Name: " + name);  
                if (val != null)  
                    Console.Out.WriteLine("     Value: " + val.ToString());  
                else  
                    Console.Out.WriteLine("     Value: <null>");  
            }  
        }  
        Console.WriteLine("\n--- Press any key ---");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [Reporting Services WMI プロバイダーへのアクセス](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [RsReportServer.config 構成ファイル](../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
