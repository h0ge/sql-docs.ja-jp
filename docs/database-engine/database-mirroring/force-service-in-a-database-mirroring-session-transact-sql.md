---
title: データベース ミラーリング セッションでのサービスの強制 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-mirroring
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
caps.latest.revision: 40
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3268d41ca0acac9c41e7e688ac4d036b56aa26c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a>データベース ミラーリング セッションでのサービスの強制 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  高パフォーマンス モードおよび自動フェールオーバーを伴わない高い安全性モードでは、ミラー サーバーが使用可能であるときにプリンシパル サーバーで障害が発生した場合、データベース所有者はサービスを強制的にミラー データベースにフェールオーバーして、データベースを直ちに使用可能な状態にできます (ただし、データが損失する場合があります)。 この方法は、次のすべての条件に一致する場合にのみ使用できます。  
  
-   プリンシパル サーバーが停止している。  
  
-   WITNESS が OFF に設定されているか、またはミラーリング監視サーバーがミラー サーバーに接続されている。  
  
> [!CAUTION]  
>  サービスの強制は、厳密にはディザスター リカバリーの方法です。 サービスを強制すると、一部のデータが損失する場合があります。 このため、サービスを強制するのは、データベースに対するサービスを直ちに復元するためにデータの損失を許容できる場合のみに限定します。 サービスの強制によって重要なデータを失うリスクがある場合は、ミラーリングを停止してデータベースを手動で再同期することをお勧めします。 サービスの強制によるリスクの詳細については、「 [データベース ミラーリングの動作モード](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)」を参照してください。  
  
 サービスを強制すると、セッションが中断して新しい復旧分岐が始まります。 サービスの強制による効果は、ミラーリングを削除して以前のプリンシパル データベースを復旧する効果に似ています。 ただし、サービスを強制した場合は、ミラーリング再開時のデータベースの再同期が容易になります (データが損失する可能性があります)。  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a>データベース ミラーリング セッションでサービスを強制するには  
  
1.  ミラー サーバーに接続します。  
  
2.  次のステートメントを実行します。  
  
     ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS  
  
     ここで、*<database_name>* はミラー化されたデータベースです。  
  
     ミラー サーバーは、直ちにプリンシパル サーバーに切り替わり、ミラーリングが中断されます。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  
