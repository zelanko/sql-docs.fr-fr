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
ms.openlocfilehash: d0bd62fe3462441d4eab9d3d89bce20cf1144131
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909557"
---
# <a name="sp_change_log_shipping_secondary_database-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les paramètres de la base de données secondaire.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @restore_delay = ] 'restore_delay'` la durée, en minutes, pendant laquelle le serveur secondaire attend avant de restaurer un fichier de sauvegarde donné. *restore_delay* est de **type int** et ne peut pas avoir la valeur null. La valeur par défaut est 0 :  
  
`[ @restore_all = ] 'restore_all'` si la valeur est définie sur 1, le serveur secondaire restaure toutes les sauvegardes du journal des transactions disponibles lors de l’exécution du travail de restauration. Dans le cas contraire, le serveur s'arrête une fois qu'un fichier a été restauré. *restore_all* est de type **bit** et ne peut pas être null.  
  
`[ @restore_mode = ] 'restore_mode'` le mode de restauration de la base de données secondaire.  
  
 0 = restaurer le journal avec NORECOVERY.  
  
 1 = Restauration du journal avec l'option STANDBY.  
  
 *Restore* est de type **bit** et ne peut pas être null.  
  
`[ @disconnect_users = ] 'disconnect_users'` si la valeur 1 est définie, les utilisateurs sont déconnectés de la base de données secondaire lorsqu’une opération de restauration est effectuée. Valeur par défaut = 0. *disconnect_users* est de type **bit** et ne peut pas être null.  
  
`[ @block_size = ] 'block_size'` la taille, en octets, utilisée comme taille de bloc pour l’unité de sauvegarde. *block_size* est de **type int** avec la valeur par défaut-1.  
  
`[ @buffer_count = ] 'buffer_count'` le nombre total de mémoires tampons utilisées par l’opération de sauvegarde ou de restauration. *buffer_count* est de **type int** avec la valeur par défaut-1.  
  
`[ @max_transfer_size = ] 'max_transfer_size'` la taille, en octets, de la demande d’entrée ou de sortie maximale émise par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’unité de sauvegarde. *max_transfersize* est de **type int** et peut avoir la valeur null.  
  
`[ @restore_threshold = ] 'restore_threshold'` le nombre de minutes autorisées à s’écouler entre les opérations de restauration avant la génération d’une alerte. *restore_threshold* est de **type int** et ne peut pas avoir la valeur null.  
  
`[ @threshold_alert = ] 'threshold_alert'` est l’alerte à déclencher lorsque le seuil de restauration est dépassé. *threshold_alert* est de **type int**, avec 14420 comme valeur par défaut.  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` spécifie si une alerte est déclenchée lorsque *restore_threshold*est dépassé. 1 = activées ; 0 = désactivées. *threshold_alert_enabled* est de type **bit** et ne peut pas être null.  
  
`[ @history_retention_period = ] 'history_retention_period'` est la durée en minutes pendant laquelle l’historique est conservé. *history_retention_period* est de **type int**. La valeur 1440 est utilisée si aucun n’est spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 **sp_change_log_shipping_secondary_database** doit être exécuté à partir de la base de données **Master** sur le serveur secondaire. Elle effectue les actions suivantes :  
  
1.  Modifie les paramètres dans les enregistrements **log_shipping_secondary_database** en fonction des besoins.  
  
2.  Modifie l’enregistrement du moniteur local dans **log_shipping_monitor_secondary** sur le serveur secondaire à l’aide des arguments fournis, si nécessaire.  

## <a name="permissions"></a>Permissions  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure.  
  
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
  
  
