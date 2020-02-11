---
title: msdb, base de données | Microsoft Docs
ms.custom: ''
ms.date: 11/10/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, msdb database
- alerts [SQL Server], msdb database
- jobs [SQL Server], msdb database
- msdb database [SQL Server]
ms.assetid: 5032cb2d-65a0-40dd-b569-4dcecdd58ceb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cee4c5d802447488930ffd04d698edcd2015e86b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62871708"
---
# <a name="msdb-database"></a>Base de données msdb
  La base de données **msdb** est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée par l’agent pour planifier les alertes et les travaux, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ainsi [!INCLUDE[ssSB](../../includes/sssb-md.md)] que par d’autres fonctionnalités telles que, et Database mail.  
  
 Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère automatiquement un historique complet et en ligne des sauvegardes et des restaurations dans les tables de la base de données **msdb**. Ces informations comprennent le nom du tiers qui a réalisé la sauvegarde, la durée de la sauvegarde et les unités ou fichiers dans lesquels la sauvegarde est stockée. 
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise ces informations pour proposer un plan permettant de restaurer une base de données et d’appliquer les sauvegardes du journal des transactions. Les événements de sauvegarde sont enregistrés pour toutes les bases de données, même s'ils ont été créés par une application personnalisée ou un outil tiers. Par exemple, si vous utilisez une application [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] qui appelle SMO (SQL Server Management Objects) pour effectuer les opérations de sauvegarde, l’événement est consigné dans les tables système de **msdb** , le journal des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows et le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour vous aider à protéger les informations stockées dans **msdb**, nous vous recommandons de placer le journal des transactions **msdb** sur un stockage à tolérance de panne.  
  
 Par défaut, la base de données **msdb** utilise le mode de récupération simple. Si vous utilisez les tables d’ [historique de sauvegarde et de restauration](../backup-restore/backup-history-and-header-information-sql-server.md) , nous vous recommandons d’utiliser le mode de récupération complète pour la base de données **msdb**. Pour plus d’informations, consultez [Modes de récupération &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md). Notez que quand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé ou mis à niveau et chaque fois que Setup.exe est utilisé pour reconstruire les bases de données système, le mode de récupération de la base de données **msdb** prend automatiquement la valeur SIMPLE.  
  
> [!IMPORTANT]  
>  Après toute opération mettant à jour la base de données **msdb**, telle que la sauvegarde ou la restauration d’une base de données, nous vous recommandons de sauvegarder **msdb**. Pour plus d’informations, consultez [Sauvegarder et restaurer des bases de données système &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="physical-properties-of-msdb"></a>Propriétés physiques de la base de données msdb  
 Le tableau ci-dessous répertorie les valeurs de configuration initiales des fichiers journaux et de données **msdb** . La taille de ces fichiers peut varier légèrement en fonction des éditions de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
|Fichier|Nom logique|Nom physique|Croissance du fichier|  
|----------|------------------|-------------------|-----------------|  
|Données primaires|MSDBData|MSDBData.mdf|Croissance automatique de 10 % jusqu'à saturation du disque.|  
|Journal|MSDBLog|MSDBLog.ldf|Croissance automatique de 10 % jusqu'à un maximum de 2 téraoctets.|  
  
 Pour déplacer la base de données **msdb** ou les fichiers journaux, consultez [Déplacer des bases de données système](move-system-databases.md).  
  
### <a name="database-options"></a>Options de base de données  
 Le tableau ci-dessous indique la valeur par défaut de chaque option de la base de données **msdb** et précise si cette option est modifiable. Pour afficher les valeurs actuelles de ces options, utilisez l'affichage catalogue [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Option de base de données|Valeur par défaut|Peut être modifiée|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ACTIVÉ|Non|  
|ANSI_NULL_DEFAULT|OFF|Oui|  
|ANSI_NULLS|OFF|Oui|  
|ANSI_PADDING|OFF|Oui|  
|ANSI_WARNINGS|OFF|Oui|  
|ARITHABORT|OFF|Oui|  
|AUTO_CLOSE|OFF|Oui|  
|AUTO_CREATE_STATISTICS|ACTIVÉ|Oui|  
|AUTO_SHRINK|OFF|Oui|  
|AUTO_UPDATE_STATISTICS|ACTIVÉ|Oui|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Oui|  
|CHANGE_TRACKING|OFF|Non|  
|CONCAT_NULL_YIELDS_NULL|OFF|Oui|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Oui|  
|CURSOR_DEFAULT|GLOBAL|Oui|  
|Options de disponibilité de base de données|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Non<br /><br /> Oui<br /><br /> Oui|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Oui|  
|DB_CHAINING|ACTIVÉ|Oui|  
|ENCRYPTION|OFF|Non|  
|NUMERIC_ROUNDABORT|OFF|Oui|  
|PAGE_VERIFY|CHECKSUM|Oui|  
|PARAMETERIZATION|SIMPLE|Oui|  
|QUOTED_IDENTIFIER|OFF|Oui|  
|READ_COMMITTED_SNAPSHOT|OFF|Non|  
|RECOVERY|SIMPLE|Oui|  
|RECURSIVE_TRIGGERS|OFF|Oui|  
|Options de Service Broker|ENABLE_BROKER|Oui|  
|TRUSTWORTHY|ACTIVÉ|Oui|  
  
 Pour obtenir une description de ces options de base de données, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="restrictions"></a>Restrictions  
 Les opérations suivantes ne peuvent pas être effectuées sur la base de données **msdb** :  
  
-   Modification du classement. Le classement par défaut est le classement du serveur.  
  
-   Suppression de la base de données  
  
-   Suppression de l’utilisateur **invité** de la base de données.  
  
-   Activation de la capture des données modifiées.  
  
-   Participation à la mise en miroir de bases de données  
  
-   Suppression du groupe de fichiers primaire, du fichier de données primaire ou du fichier journal  
  
-   Changement du nom de la base de données ou du groupe de fichiers primaire  
  
-   Affectation de la valeur OFFLINE à la base de données.  
  
-   Affectation de la valeur READ_ONLY au groupe de fichiers primaire.  
  
## <a name="related-content"></a>Contenu associé  
 [Bases de données système](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Déplacer des fichiers de bases de données](move-database-files.md)  
  
 [Messagerie de base de données](../database-mail/database-mail.md)  
  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
