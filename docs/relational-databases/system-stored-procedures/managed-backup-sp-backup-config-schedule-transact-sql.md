---
title: managed_backup. sp_backup_config_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/20/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_schedule_TSQL
- managed_backup.sp_backup_config_schedule
- managed_backup.sp_backup_config_schedule_TSQL
- sp_backup_config_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- managed_backup.sp_backup_config_schedule
- sp_backup_config_schedule
ms.assetid: 82541160-d1df-4061-91a5-6868dd85743a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7bb477901dee22c70bb47cd0eaf7da5eb163b7f
ms.sourcegitcommit: 87b932dc4b603a35a19f16e2c681b6a8d4df1fec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77507531"
---
# <a name="managed_backupsp_backup_config_schedule-transact-sql"></a>managed_backup. sp_backup_config_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Configure les options de planification automatisées ou [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]personnalisées pour.  
    
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
EXEC managed_backup.sp_backup_config_schedule   
    [@database_name = ] 'database_name'
    ,[@scheduling_option = ] {'Custom' | 'System'}  
    ,[@full_backup_freq_type = ] {'Daily' | 'Weekly'}  
    ,[@days_of_week = ] 'days_of_the_week'  
    ,[@backup_begin_time = ] 'begin time of the backup window'  
    ,[@backup_duration = ] 'backup window length'  
    ,[@log_backup_freq = ] 'frequency of log backup'  
```  
  
##  <a name="Arguments"></a> Arguments  
 @database_name  
 Nom de la base de données pour activer la sauvegarde managée sur une base de données spécifique. Si la valeur est NULL ou *, cette sauvegarde managée s’applique à toutes les bases de données sur le serveur.  
  
 @scheduling_option  
 Spécifiez « système » pour la planification de sauvegarde contrôlée par le système. Spécifiez « Custom » pour une planification personnalisée définie par l’autre paramètres.  
  
 @full_backup_freq_type  
 Type de fréquence de l’opération de sauvegarde managée, qui peut être définie sur « quotidien » ou « hebdomadaire ».  
  
 @days_of_week  
 Les jours de la semaine pour les sauvegardes lorsque @full_backup_freq_type est défini sur hebdomadaire. Spécifiez des noms de chaîne complets comme « Monday ».  Vous pouvez également spécifier plus d’un nom de jour, séparé par un canal. Par exemple N’Monday | Mercredi | Vendredi».  
  
 @backup_begin_time  
 Heure de début de la fenêtre de sauvegarde. Les sauvegardes ne seront pas démarrées en dehors de la fenêtre de temps, qui est définie @backup_begin_time par @backup_durationune combinaison de et.  
  
 @backup_duration  
 Durée de la fenêtre de temps de sauvegarde. Notez qu’il n’y a aucune garantie que les sauvegardes seront effectuées pendant la fenêtre de @backup_begin_time temps @backup_durationdéfinie par et. Les opérations de sauvegarde démarrées dans cette fenêtre de temps mais qui dépassent la durée de la fenêtre ne sont pas annulées.  
  
 @log_backup_freq  
 Cela détermine la fréquence des sauvegardes du journal des transactions. Ces sauvegardes se produisent à intervalles réguliers plutôt qu’en fonction de la planification spécifiée pour les sauvegardes de base de données. @log_backup_freqpeut être en minutes ou en heures `0:00` et être valide, ce qui indique l’absence de sauvegardes du journal. La désactivation des sauvegardes de journaux ne conviendrait que pour les bases de données avec un mode de récupération simple.  
  
> [!NOTE]  
>  Si le mode de récupération passe de simple à Full, vous devez reconfigurer le log_backup_freq de `0:00` à une valeur différente de zéro.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle de base de données **db_backupoperator** , avec les autorisations **ALTER ANY CREDENTIAL** et **Execute** sur **sp_delete_backuphistory** procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [managed_backup. sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup. sp_backup_config_advanced &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)  
  
  
