---
title: Sauvegardes du journal des transactions (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6dc94409e607c91944a2263ac5dfb3e8a3f4ce54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168639"
---
# <a name="transaction-log-backups-sql-server"></a>Sauvegardes du journal des transactions (SQL Server)
  Cette rubrique s'applique uniquement aux bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] employant le mode de récupération complète ou le mode de récupération utilisant les journaux de transactions. Cette rubrique décrit la sauvegarde du journal des transactions d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Vous devez au moins avoir créé une sauvegarde complète pour pouvoir créer des sauvegardes de journaux. Après cela, le journal des transactions peut être sauvegardé à tout moment, à moins qu'il ne soit déjà en cours de sauvegarde. Nous vous recommandons d'effectuer des sauvegardes de journaux fréquemment, à la fois pour réduire les risques de perte de travail et pour tronquer le journal des transactions. En règle générale, un administrateur de base de données crée une sauvegarde complète de base de données de temps en temps, par exemple chaque semaine et, éventuellement, crée une série de sauvegardes de base de données différentielles à un intervalle plus court, par exemple tous les jours. Indépendamment des sauvegardes de base de données, l'administrateur de base de données sauvegarde le journal des transactions à intervalles fréquents, par exemple toutes les 10 minutes. Pour un type donné de sauvegarde, l'intervalle optimal varie en fonction de divers facteurs tels que l'importance des données, la taille de la base de données et la charge de travail du serveur.  
  
 **Dans cette rubrique :**  
  
-   [Fonctionne d’une séquence de sauvegardes de journaux](#LogBackupSequence)  
  
-   [Recommandations](#Recommendations)  
  
-   [Tâches associées](#RelatedTasks)  
  
-   [Contenu connexe](#RelatedContent)  
  
##  <a name="LogBackupSequence"></a> Fonctionne d’une séquence de sauvegardes de journaux  
 La séquence de sauvegarde des journaux des transactions ( *séquence de journaux* ) ne dépend pas des sauvegardes de données. Supposons, par exemple, que la séquence des événements est la suivante.  
  
|Time|Événement|  
|----------|-----------|  
|8h00|Sauvegarde de la base de données.|  
|Midi|Sauvegarde du journal des transactions.|  
|16h00|Sauvegarde du journal des transactions.|  
|18h00|Sauvegarde de la base de données.|  
|20h00|Sauvegarde du journal des transactions.|  
  
 La sauvegarde du journal des transactions créée à 20h00 contient les enregistrements du journal des transactions effectués de 16H00 à 20h00, ce qui couvre le moment de la création de la sauvegarde complète intervenant à 18H00. La séquence des sauvegardes du journal des transactions est continue depuis la sauvegarde complète de la base de données initiale créée à 08H00 jusqu'à la dernière sauvegarde du journal des transactions effectuée à 20H00. Pour plus d’informations sur l’application de ces sauvegardes du journal, reportez-vous à l’exemple cité dans [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).  
  
##  <a name="Recommendations"></a> Recommandations  
  
-   Si un journal des transactions est endommagé, vous perdez alors les travaux réalisés depuis la sauvegarde valide la plus récente. Par conséquent, nous vous recommandons vivement de placer vos fichiers journaux sur une unité de stockage à tolérance de pannes.  
  
-   Si une base de données est endommagée ou si vous êtes sur le point de restaurer la base de données, nous vous recommandons de créer une [sauvegarde de la fin du journal](tail-log-backups-sql-server.md) pour vous permettre de restaurer la base de données au moment actuel.  
  
-   Par défaut, chaque opération de sauvegarde réussie ajoute une entrée au journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et au journal des événements système. Si vous sauvegardez très fréquemment le journal, ces messages de réussite peuvent rapidement s'accumuler, créer des journaux d'erreurs très volumineux et compliquer la recherche d'autres messages. Dans de tels cas, vous pouvez supprimer ces entrées de journal en utilisant l'indicateur de trace 3226 si aucun de vos scripts ne dépend de ces entrées. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour créer une sauvegarde du journal des transactions**  
  
-   [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)  
  
 Pour planifier des travaux de sauvegarde, consultez [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).  
  
##  <a name="RelatedContent"></a> Contenu associé  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Journal des transactions &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [Sauvegarde et restauration des bases de données SQL Server](back-up-and-restore-of-sql-server-databases.md)   
 [Sauvegardes de la fin du journal &#40;SQL Server&#41;](tail-log-backups-sql-server.md)   
 [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)  
  
  
