---
title: sp_add_log_shipping_secondary_database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_database
- sp_add_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_database
ms.assetid: d29e1c24-3a3c-47a4-a726-4584afa6038a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5c7dab148af9d8c3db8a9b1503ad33975c790120
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493221"
---
# <a name="spaddlogshippingsecondarydatabase-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit une base de données secondaire pour la copie des journaux de transaction.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>Arguments  
`[ @secondary_database = ] 'secondary_database'` Est le nom de la base de données secondaire. *secondary_database* est **sysname**, sans valeur par défaut.  
  
`[ @primary_server = ] 'primary_server'` Le nom de l’instance principale de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dans la configuration d’envoi de journaux. *primary_server* est **sysname** et ne peut pas être NULL.  
  
`[ @primary_database = ] 'primary_database'` Est le nom de la base de données sur le serveur principal. *primary_database* est **sysname**, sans valeur par défaut.  
  
`[ @restore_delay = ] 'restore_delay'` La durée, en minutes, pendant laquelle le serveur secondaire attend avant de restaurer un fichier de sauvegarde donné. *restore_delay* est **int** et ne peut pas être NULL. La valeur par défaut est 0.  
  
`[ @restore_all = ] 'restore_all'` Si défini sur 1, le serveur secondaire restaure toutes les sauvegardes de journaux de transactions disponibles lors de l’exécution de la tâche de restauration. Dans le cas contraire, le serveur s'arrête une fois qu'un fichier est restauré. *restore_all* est **bits** et ne peut pas être NULL.  
  
`[ @restore_mode = ] 'restore_mode'` Le mode de restauration pour la base de données secondaire.  
  
 0 = Restauration du journal avec l'option NORECOVERY.  
  
 1 = Restauration du journal avec l'option STANDBY.  
  
 *restaurer* est **bits** et ne peut pas être NULL.  
  
`[ @disconnect_users = ] 'disconnect_users'` Si défini sur 1, les utilisateurs sont déconnectés de la base de données secondaire lorsqu’une opération de restauration est effectuée. Par défaut = 0. *Déconnecter* utilisateurs est **bits** et ne peut pas être NULL.  
  
`[ @block_size = ] 'block_size'` La taille, en octets, qui est utilisée comme la taille de bloc pour l’unité de sauvegarde. *block_size* est **int** avec une valeur par défaut de -1.  
  
`[ @buffer_count = ] 'buffer_count'` Le nombre total de mémoires tampons utilisées par l’opération de sauvegarde ou de restauration. *buffer_count* est **int** avec une valeur par défaut de -1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'` La taille, en octets, de l’entrée maximale ou de la demande de sortie qui est émise par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’unité de sauvegarde. *max_transfersize* est **int** et peut être NULL.  
  
`[ @restore_threshold = ] 'restore_threshold'` Le nombre de minutes pouvant s’écouler entre les opérations de restauration avant qu’une alerte est générée. *restore_threshold* est **int** et ne peut pas être NULL.  
  
`[ @threshold_alert = ] 'threshold_alert'` Est l’alerte à déclencher lorsque le seuil de sauvegarde est dépassé. *threshold_alert ne* est **int**, avec 14 420 comme valeur par défaut.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` Indique si une alerte est générée lorsque *backup_threshold* est dépassé. La valeur 1 par défaut indique que l'alerte sera générée. *threshold_alert_enabled* est **bits**.  
  
`[ @history_retention_period = ] 'history_retention_period'` Est la durée en minutes pendant laquelle l’historique est conservé. *history_retention_period* est **int**, avec NULL comme valeur par défaut. La valeur 14 420 est utilisée si aucune autre valeur n'est spécifiée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **sp_add_log_shipping_secondary_database** doit être exécuté à partir de la **master** base de données sur le serveur secondaire. Elle effectue les actions suivantes :  
  
1.  **sp_add_log_shipping_secondary_primary** doit être appelée avant cette procédure stockée pour initialiser le journal principal les informations de base de données sur le serveur secondaire d’expédition.  
  
2.  Ajoute une entrée pour la base de données secondaire dans **log_shipping_secondary_databases** à l’aide des arguments fournis.  
  
3.  Ajoute un enregistrement moniteur local dans **log_shipping_monitor_secondary** sur le serveur secondaire à l’aide des arguments fournis.  
  
4.  Si le serveur moniteur est différent du serveur secondaire, ajoute un enregistrement moniteur dans **log_shipping_monitor_secondary** sur le moniteur de serveur à l’aide des arguments fournis.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 Cet exemple illustre l’utilisation de la **sp_add_log_shipping_secondary_database** procédure pour ajouter la base de données stockée **LogShipAdventureWorks** en tant que base de données secondaire dans une configuration d’envoi de journaux avec la base de données primaire [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] résidant sur le serveur principal TRIBECA.  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_database   
@secondary_database = N'LogShipAdventureWorks'   
,@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks2012'   
,@restore_delay = 0   
,@restore_mode = 1   
,@disconnect_users = 0   
,@restore_threshold = 45     
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
