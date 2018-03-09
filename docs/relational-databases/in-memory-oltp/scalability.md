---
title: "Scalabilité | Microsoft Docs"
ms.custom: 
ms.date: 08/27/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a9657320f92fd50b8d07d255e863cb5aebba46f0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="scalability"></a>Extensibilité
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] SQL Server 2016 comprend plusieurs améliorations concernant l’extensibilité au niveau du stockage sur disque pour les tables à mémoire optimisée.  
  
-   **Conservation des tables mémoire optimisées à l’aide de plusieurs threads**  
  
     La version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]comprenait un seul thread de point de contrôle hors connexion qui recherchait dans le journal des transactions les modifications des tables optimisées en mémoire et qui les conservait dans des fichiers de point de contrôle (tels que des fichiers de données et des fichiers delta). Avec un nombre de CŒURS plus élevé, ce thread de point de contrôle hors connexion unique risquerait de prendre du retard.  
  
     [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]intègre donc plusieurs threads simultanés responsables de la conservation des modifications apportées aux tables optimisées en mémoire.  
  
-   **Récupération multithread**  
  
     Dans la version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la demande de journalisation dans le cadre de l’opération de récupération était monothread. Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], cette demande de journalisation est multithread.  
  
-   **Opération de fusion**  
  
     L’opération de fusion est désormais multithread.  
  
-   **Vues de gestion dynamique**  
  
     [sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md) et [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) ont considérablement évolué.  
  
 La fusion manuelle a été désactivée, car une fusion multithread est censée suivre la charge.  
  
 Le moteur OLTP en mémoire continue d’utiliser le groupe de fichiers mémoire optimisé reposant sur FILESTREAM, mais les différents fichiers du groupe de fichiers sont dissociés de FILESTREAM. Ces fichiers sont entièrement gérés (notamment pour les actions de création, de suppression et de garbage collection) par le moteur OLTP en mémoire. [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) n’est pas pris en charge.  
  
  
