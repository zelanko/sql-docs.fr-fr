---
title: Scalabilité | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ad3dd62bbf82314be6b981944186711eaa5ce62b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766070"
---
# <a name="scalability"></a>Scalabilité
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  SQL Server 2016 intègre plusieurs améliorations en matière d’extensibilité au niveau du stockage sur disque pour les tables mémoire optimisées.  
  
-   **Conservation des tables mémoire optimisées à l’aide de plusieurs threads**  
  
     La version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]comprenait un seul thread de point de contrôle hors connexion qui recherchait dans le journal des transactions les modifications des tables optimisées en mémoire et qui les conservait dans des fichiers de point de contrôle (tels que des fichiers de données et des fichiers delta). Avec un nombre de CŒURS plus élevé, ce thread de point de contrôle hors connexion unique risquerait de prendre du retard.  
  
     [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]intègre donc plusieurs threads simultanés responsables de la conservation des modifications apportées aux tables optimisées en mémoire.  
  
-   **Récupération multithread**  
  
     Dans la version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la demande de journalisation dans le cadre de l’opération de récupération était monothread. Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], cette demande de journalisation est multithread.  
  
-   **Opération de fusion**  
  
     L’opération de fusion est désormais multithread.  
  
-   **Vues de gestion dynamique**  
  
     [sys.dm_db_xtp_checkpoint_stats & #40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md) et [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) ont considérablement évolué.  
  
 La fusion manuelle a été désactivée, car une fusion multithread est censée suivre la charge.  
  
 Le moteur OLTP en mémoire continue d’utiliser le groupe de fichiers mémoire optimisé reposant sur FILESTREAM, mais les différents fichiers du groupe de fichiers sont dissociés de FILESTREAM. Ces fichiers sont entièrement gérés (notamment pour les actions de création, de suppression et de garbage collection) par le moteur OLTP en mémoire. [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) n’est pas pris en charge.  
  
  
