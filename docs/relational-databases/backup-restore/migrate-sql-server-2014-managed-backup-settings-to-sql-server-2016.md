---
title: "Migrer les param&#232;tres de sauvegarde manag&#233;e de SQL&#160;Server&#160;2014 vers SQL&#160;Server&#160;2016 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae937ebb-24ff-4a33-be3c-8f85328dfc75
caps.latest.revision: 7
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 6
---
# Migrer les param&#232;tres de sauvegarde manag&#233;e de SQL&#160;Server&#160;2014 vers SQL&#160;Server&#160;2016
  Cette rubrique décrit les considérations relatives à la migration de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] dans le cadre d’une mise à niveau de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] vers [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
 Les procédures et le comportement sous-jacent de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ont changé dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Les sections suivantes décrivent les modifications fonctionnelles et leurs implications.  
  
## Vue d'ensemble  
 Le tableau suivant décrit quelques-unes des principales différences fonctionnelles de [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] entre les versions [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
|Domaine|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|----------|---------------------------|---------------------------|  
|**Espace de noms :**|smart_admin|managed_backup|  
|**Procédures stockées système :**|sp_set_db_backup<br /><br /> sp_set_instance_backup|[sp_backup_config_basic](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)<br /><br /> [sp_backup_config_advanced](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)<br /><br /> [sp_backup_config_schedule](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)|  
|**Sécurité :**|Informations d’identification SQL utilisant un compte de stockage Microsoft Azure et une clé d’accès.|Informations d’identification SQL utilisant un jeton de signature d’accès partagé (SAS) Microsoft Azure.|  
|**Stockage sous-jacent :**|Microsoft Azure Storage avec objets blob de pages.|Microsoft Azure Storage avec objets blob de blocs.|  
  
## Avantages  
 L’utilisation des nouvelles fonctionnalités de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]présente plusieurs avantages.  
  
-   Les objets blob de blocs peuvent être stockés à moindres coûts.  
  
-   Avec l’agrégation par bandes, vous pouvez stocker des sauvegardes bien plus volumineuses (12 To contre 1 To pour les objets blob de pages).  
  
-   L’agrégation par bandes permet également d’améliorer le temps de restauration pour les bases de données volumineuses  
  
-   Pour connaître les autres améliorations apportées à la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], consultez [Sauvegarde managée SQL Server sur Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).  
  
## Observations  
 Après une mise à niveau à partir de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], tenez compte des remarques suivantes relatives à [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :  
  
-   Les bases de données configurées précédemment pour la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sur [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] continueront d’utiliser les procédures système et le comportement sous-jacent de **smart_admin** sur [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
-   Les procédures **smart_admin** ne sont pas prises en charge par les nouvelles configurations de la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sur [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Vous devez utiliser les nouvelles procédures et fonctionnalités **managed_backup**.  
  
## Voir aussi  
 [Sauvegarde managée SQL Server sur Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  