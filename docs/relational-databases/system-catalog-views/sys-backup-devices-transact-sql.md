---
title: sys. backup_devices (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b70d87a6f1a72662c1ca466a532d3050b4fe58ab
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67942589"
---
# <a name="sysbackup_devices-transact-sql"></a>sys.backup_devices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque unité de sauvegarde inscrite à **sp_addumpdevice** l’aide de sp_addumpdevice [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ou créée dans.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom du périphérique de sauvegarde. Unique dans le jeu.|  
|**type**|**tinyint**|Type de l'unité de sauvegarde :<br /><br /> 2 = Disque<br /><br /> 3 = Disquette (obsolète)<br /><br /> 5 = Bande<br /><br /> 6 = Canal (obsolète)<br /><br /> 7 = Périphérique virtuel (pour une utilisation facultative par des revendeurs de sauvegarde tiers)<br /><br /> En général, seuls disque (2) et bande (5) sont utilisés.|  
|**type_desc**|**nvarchar(60)**|Description du type de périphérique de sauvegarde :<br /><br /> DISK<br /><br /> DISKETTE (obsolète)<br /><br /> TAPE<br /><br /> PIPE (obsolète)<br /><br /> VIRTUAL_DEVICE (pour une utilisation facultative par des revendeurs de sauvegarde tiers)<br /><br /> En général, seuls DISK et TAPE sont utilisés.|  
|**physical_name**|**nvarchar(260)**|Nom de fichier physique ou chemin du périphérique de sauvegarde.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [Affichages catalogue de bases de données et de fichiers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Questions fréquentes sur l'interrogation des catalogues système de SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
