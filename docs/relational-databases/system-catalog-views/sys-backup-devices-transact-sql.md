---
title: sys.backup_devices (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backup_devices_TSQL
- backup_devices
- sys.backup_devices
- sys.backup_devices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], viewing information
- sys.backup_devices catalog view
ms.assetid: 457edaa4-aca1-4bd3-bf8d-734490b80fcd
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be1c29322063c33797ff56451b55c619fd07db82
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "33178248"
---
# <a name="sysbackupdevices-transact-sql"></a>sys.backup_devices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用して登録されている各バックアップ デバイスの行を格納**sp_addumpdevice**またはで作成された[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|バックアップ デバイスの名前。 セット内で一意です。|  
|**type**|**tinyint**|バックアップ デバイスの種類。<br /><br /> 2 = ディスク<br /><br /> 3 = フロッピー ディスク (廃止)<br /><br /> 5 = テープ<br /><br /> 6 = パイプ (廃止)<br /><br /> 7 = 仮想デバイス (サード パーティ バックアップ ベンダーがオプションで使用)<br /><br /> 通常は、ディスク (2) またはテープ (5) のみが使用されます。|  
|**type_desc**|**nvarchar(60)**|バックアップ デバイスの種類の説明。<br /><br /> DISK<br /><br /> DISKETTE (廃止)<br /><br /> TAPE<br /><br /> PIPE (廃止)<br /><br /> VIRTUAL_DEVICE (サード パーティ バックアップ ベンダーがオプションで使用)<br /><br /> 通常は、DISK および TAPE のみが使用されます。|  
|**physical_name**|**nvarchar(260)**|バックアップ デバイスの物理的なファイル名またはパス。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
