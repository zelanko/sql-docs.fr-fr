---
title: Sysopentapes (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysopentapes
- sysopentapes_TSQL
dev_langs: TSQL
helpviewer_keywords:
- backup media [SQL Server], sysopentapes system table
- sysopentapes system table
ms.assetid: c066ca9b-9cfd-46b1-90a3-5c8dc9e7b6ae
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb39670ced045b6ae5f14b9225d1b46d35aef792
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque unité de bande actuellement ouverte. Cette vue est stockée dans le **master** base de données.  
  
> [!IMPORTANT]  
>  Cette table système est incluse en tant que vue pour la compatibilité descendante. Utilisez plutôt le [sys.dm_io_backup_tapes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) vue de gestion dynamique.  
  
> [!NOTE]  
>  Vous ne pouvez pas supprimer le **sysopentapes** vue.  

  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar (64)**|Nom de fichier physique de l'unité de bande ouverte. Pour plus d’informations sur l’ouverture et la libération de bandes, consultez [sauvegarde &#40; Transact-SQL &#41; ](../../t-sql/statements/backup-transact-sql.md) et [de restauration &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Permissions  
 L’utilisateur a besoin de l’autorisation VIEW SERVER STATE sur le serveur.  
  
  
