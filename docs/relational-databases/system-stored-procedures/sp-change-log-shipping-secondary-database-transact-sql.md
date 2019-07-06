---
title: sp_change_log_shipping_secondary_database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_database
- sp_change_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_database
ms.assetid: 3ebcf2f1-980f-4543-a84b-fbaeea54eeac
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5af98bd479738785c341b2618561eaab3f43b5d1
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586016"
---
# <a name="spchangelogshippingsecondarydatabase-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les paramètres de la base de données secondaire.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_change_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
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
`[ @restore_delay = ] 'restore_delay'` La durée, en minutes, pendant laquelle le serveur secondaire attend avant de restaurer un fichier de sauvegarde donné. *restore_delay* est **int** et ne peut pas être NULL. La valeur par défaut est 0.  
  
`[ @restore_all = ] 'restore_all'` Si défini sur 1, le serveur secondaire restaure toutes les sauvegardes de journaux de transactions disponibles lors de l’exécution de la tâche de restauration. Dans le cas contraire, le serveur s'arrête une fois qu'un fichier a été restauré. *restore_all* est **bits** et ne peut pas être NULL.  
  
`[ @restore_mode = ] 'restore_mode'` Le mode de restauration pour la base de données secondaire.  
  
 0 = restaurer le journal avec NORECOVERY.  
  
 1 = Restauration du journal avec l'option STANDBY.  
  
 *restaurer* est **bits** et ne peut pas être NULL.  
  
`[ @disconnect_users = ] 'disconnect_users'` Si la valeur 1, les utilisateurs est déconnectée de la base de données secondaire lorsqu’une opération de restauration est effectuée. Par défaut = 0. *disconnect_users* est **bits** et ne peut pas être NULL.  
  
`[ @block_size = ] 'block_size'` La taille, en octets, qui est utilisée comme la taille de bloc pour l’unité de sauvegarde. *block_size* est **int** avec une valeur par défaut de -1.  
  
`[ @buffer_count = ] 'buffer_count'` Le nombre total de mémoires tampons utilisées par l’opération de sauvegarde ou de restauration. *buffer_count* est **int** avec une valeur par défaut de -1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'` La taille, en octets, de l’entrée maximale ou de la demande de sortie qui est émise par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’unité de sauvegarde. *max_transfersize* est **int** et peut être NULL.  
  
`[ @restore_threshold = ] 'restore_threshold'` Le nombre de minutes pouvant s’écouler entre les opérations de restauration avant qu’une alerte est générée. *restore_threshold* est **int** et ne peut pas être NULL.  
  
`[ @threshold_alert = ] 'threshold_alert'` Est l’alerte à déclencher lorsque le seuil de restauration est dépassé. *threshold_alert ne* est **int**, avec une valeur par défaut 14420.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` Spécifie si une alerte est déclenchée quand *restore_threshold*est dépassé. 1 = activées ; 0 = désactivées. *threshold_alert_enabled* est **bits** et ne peut pas être NULL.  
  
`[ @history_retention_period = ] 'history_retention_period'` Est la durée en minutes pendant laquelle l’historique doit être conservé. *history_retention_period* est **int**. Une valeur de 1440 sera utilisée si aucun n’est spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **sp_change_log_shipping_secondary_database** doit être exécuté à partir de la **master** base de données sur le serveur secondaire. Elle effectue les actions suivantes :  
  
1.  Modifie les paramètres de la **log_shipping_secondary_database** enregistre en fonction des besoins.  
  
2.  Modifie l’enregistrement du moniteur local dans **log_shipping_monitor_secondary** sur le serveur secondaire à l’aide des arguments fournis, si nécessaire.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 Cet exemple illustre l’utilisation de **sp_change_log_shipping_secondary_database** pour mettre à jour les paramètres de base de données secondaire pour la base de données **LogShipAdventureWorks**.  
  
```  
EXEC master.dbo.sp_change_log_shipping_secondary_database   
 @secondary_database =  'LogShipAdventureWorks'  
,  @restore_delay = 0  
,  @restore_all = 1  
,  @restore_mode = 0  
,  @disconnect_users = 0  
,  @threshold_alert = 14420  
,  @threshold_alert_enabled = 1  
,  @history_retention_period = 14420;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
