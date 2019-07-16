---
title: sp_replmonitorhelpsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpsubscription_TSQL
- sp_replmonitorhelpsubscription
helpviewer_keywords:
- sp_replmonitorhelpsubscription
ms.assetid: a681b2db-c82d-4624-a10c-396afb0ac42f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e8f76699e35c71e7bbf85b972cd76eb0cb3c289
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950546"
---
# <a name="spreplmonitorhelpsubscription-transact-sql"></a>sp_replmonitorhelpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur l'état actuel d'abonnements appartenant à une ou plusieurs publications du serveur de publication, et retourne une ligne pour chaque abonnement retourné. Cette procédure stockée, utilisée pour surveiller la réplication, est exécutée sur la base de données du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replmonitorhelpsubscription [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @mode = ] mode ]  
    [ , [ @topnum = ] topnum ]   
    [ , [ @exclude_anonymous = ] exclude_anonymous ]   
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication dont l’état est en cours d’analyse. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut. Si **null**, informations sont retournées pour tous les éditeurs qui utilisent le serveur de distribution.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données publiée. *publisher_db* est **sysname**, avec NULL comme valeur par défaut. Si la valeur est NULL, les informations retournées concernent toutes les bases de données publiées situées sur le serveur de publication.  
  
`[ @publication = ] 'publication'` Le nom de la publication en cours d’analyse. *publication* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @publication_type = ] publication_type` Si le type de publication. *publication_type* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|Publication transactionnelle.|  
|**1**|Publication d'instantané.|  
|**2**|Publication de fusion.|  
|NULL (par défaut)|La réplication tente de déterminer le type de publication.|  
  
`[ @mode = ] mode` Le mode de filtrage à utiliser lors du retour d’abonnement est la surveillance d’informations. *mode* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0** (valeur par défaut)|Retourne tous les abonnements.|  
|**1**|Retourne uniquement les abonnements qui ont des erreurs.|  
|**2**|Retourne uniquement les abonnements qui ont généré des avertissements de mesure de seuil.|  
|**3**|Retourne uniquement les abonnements qui ont des erreurs ou ayant généré des avertissements de mesure de seuil.|  
|**4**|Retourne les 25 abonnements les moins performants supérieurs.|  
|**5**|Retourne les 50 abonnements les moins performants.|  
|**6**|Retourne uniquement les abonnements en cours de synchronisation.|  
|**7**|Retourne uniquement les abonnements qui ne sont pas en cours de synchronisation.|  
  
`[ @topnum = ] topnum` Restreint le jeu de résultats à uniquement le nombre spécifié d’abonnements en haut des données retournées. *topnum* est **int**, sans valeur par défaut.  
  
`[ @exclude_anonymous = ] exclude_anonymous` Indique si les extractions d’abonnements anonymes sont exclues du jeu de résultats. *exclude_anonymous* est **bits**, avec une valeur par défaut **0**; la valeur **1** signifie que les abonnements anonymes sont exclus tandis que la valeur **0**  signifie qu’ils sont inclus.  
  
`[ @refreshpolicy = ] refreshpolicy` Usage interne uniquement.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**status**|**int**|Examine l'état de tous les agents de réplication associés à la publication, puis retourne l'état le plus élevé dans l'ordre suivant :<br /><br /> **6** = Échec<br /><br /> **5** = reprise<br /><br /> **2** = arrêté<br /><br /> **4** = inactif<br /><br /> **3** = en cours<br /><br /> **1** = démarré|  
|**avertissement**|**int**|Avertissement de seuil maximal généré par un abonnement appartenant à la publication, qui peut être le résultat OR logique d'au moins l'une des valeurs suivantes.<br /><br /> **1** = expiration - un abonnement à une publication transactionnelle n’a pas été synchronisé dans le seuil de période de rétention.<br /><br /> **2** = latency - le temps nécessaire pour répliquer des données à partir d’un serveur de publication transactionnelle à l’abonné dépasse le seuil, en secondes.<br /><br /> **4** = mergeexpiration – un abonnement à une publication de fusion n’a pas été synchronisé dans le seuil de période de rétention.<br /><br /> **8** = mergefastrunduration - le temps nécessaire pour effectuer la synchronisation d’un abonnement de fusion dépasse le seuil, en secondes, via une connexion réseau rapide.<br /><br /> **16** = mergeslowrunduration - le temps nécessaire pour effectuer la synchronisation d’un abonnement de fusion dépasse le seuil, en secondes, via une connexion réseau lente ou accès à distance.<br /><br /> **32** = mergefastrunspeed - la vitesse de transmission de lignes pendant la synchronisation d’un abonnement de fusion a échoué à maintenir le taux du seuil, en lignes par seconde, via une connexion réseau rapide.<br /><br /> **64** = mergeslowrunspeed - la vitesse de transmission de lignes pendant la synchronisation d’un abonnement de fusion a échoué à maintenir le taux du seuil, en lignes par seconde, via une connexion réseau lente ou accès à distance.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné.|  
|**bd_abonné**|**sysname**|Nom de la base de données utilisée pour l'abonnement.|  
|**publisher_db**|**sysname**|Nom de la base de données de publication.|  
|**publication**|**sysname**|Nom d'une publication.|  
|**publication_type**|**Int**|Est du type de publication, qui peut être une des valeurs suivantes :<br /><br /> **0** = publication transactionnelle<br /><br /> **1** = publication d’instantané<br /><br /> **2** = publication de fusion|  
|**subtype**|**int**|Type d'abonnement, qui peut prendre l'une des valeurs suivantes :<br /><br /> **0** = push<br /><br /> **1** = par extraction<br /><br /> **2** = anonyme|  
|**latence**|**Int**|Latence maximale, en secondes, des modifications de données propagées par l'Agent de lecture du journal ou l'Agent de distribution pour une publication transactionnelle.|  
|**latencythreshold**|**int**|Latence maximale de la publication transactionnelle au-delà de laquelle un avertissement est déclenché.|  
|**agentnotrunning**|**Int**|Durée, en heures, pendant laquelle l'Agent n'a pas été exécuté.|  
|**agentnotrunningthreshold**|**Int**|Durée, en heures, pendant laquelle l'Agent n'a pas été exécuté avant le déclenchement d'un avertissement.|  
|**timetoexpiration**|**Int**|Durée, en heures, au terme de laquelle l'abonnement expire s'il n'est pas synchronisé.|  
|**expirationthreshold**|**int**|Durée, en heures, au terme de laquelle l'expiration de l'abonnement déclenche un avertissement.|  
|**last_distsync**|**datetime**|Est la date/heure dernière exécution de l’Agent de Distribution.|  
|**distribution_agentname**|**sysname**|Nom du travail d'Agent de distribution pour l'abonnement à une publication transactionnelle.|  
|**mergeagentname**|**sysname**|Nom du travail d'Agent de fusion pour l'abonnement à une publication de fusion.|  
|**mergesubscriptionfriendlyname**|**sysname**|Nom convivial donné à l'abonnement.|  
|**mergeagentlocation**|**sysname**|Nom du serveur sur lequel l'Agent de fusion est exécuté.|  
|**mergeconnectiontype**|**int**|Connexion utilisée lors de la synchronisation d'un abonnement à une publication de fusion ; ce paramètre peut prendre l'une des valeurs suivantes :<br /><br /> **1** = réseau local (LAN)<br /><br /> **2** = connexion de réseau à distance<br /><br /> **3** = synchronisation web.|  
|**mergePerformance**|**Int**|Performances de la dernière synchronisation comparées à toutes les synchronisations de l'abonnement, calculées en divisant la vitesse de transmission de la dernière synchronisation par la moyenne de toutes les vitesses de transmission antérieures.|  
|**mergerunspeed**|**float**|Vitesse de transmission de la dernière synchronisation de l'abonnement.|  
|**mergerunduration**|**Int**|Durée qui a été nécessaire à la dernière synchronisation de l'abonnement.|  
|**monitorranking**|**int**|Valeur de classement des abonnements dans l'ensemble de résultats ; ce paramètre peut prendre l'une des valeurs suivantes :<br /><br /> Dans le cas d'une publication transactionnelle :<br /><br /> **60** = erreur<br /><br /> **56** = Avertissement : critique pour les performances<br /><br /> **52** = Avertissement : expire bientôt ou arrivé à expiration<br /><br /> **50** = Avertissement : abonnement non initialisé<br /><br /> **40** = nouvelle tentative de l’échec de la commande<br /><br /> **30** = non exécuté (succès)<br /><br /> **20** = en cours d’exécution (démarré, exécuté ou inactif)<br /><br /> Dans le cas d'une publication de fusion :<br /><br /> **60** = erreur<br /><br /> **56** = Avertissement : critique pour les performances<br /><br /> **54** = Avertissement : fusion longue<br /><br /> **52** = Avertissement : expire bientôt<br /><br /> **50** = Avertissement : abonnement non initialisé<br /><br /> **40** = nouvelle tentative de l’échec de la commande<br /><br /> **30** = en cours d’exécution (démarré, exécuté ou inactif)<br /><br /> **20** = non exécuté (succès)|  
|**distributionagentjobid**|**binary(16)**|ID du travail d'Agent de distribution pour les abonnements à une publication transactionnelle.|  
|**mergeagentjobid**|**binary(16)**|ID du travail d'Agent de fusion pour les abonnements à une publication de fusion.|  
|**distributionagentid**|**int**|ID du travail d'Agent de distribution pour l'abonnement.|  
|**distributionagentprofileid**|**int**|ID du profil d'Agent utilisé par l'Agent de distribution.|  
|**mergeagentid**|**int**|ID du travail d'Agent de fusion pour l'abonnement.|  
|**mergeagentprofileid**|**Int**|ID du profil d'Agent utilisé par l'Agent de fusion.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replmonitorhelpsubscription** est utilisé avec tous les types de réplication.  
  
 **sp_replmonitorhelpsubscription** trie les résultats selon la gravité de l’état de l’abonnement, ce qui est déterminé par la valeur de *monitorranking*. Par exemple, les lignes de tous les abonnements se trouvant dans un état d'erreur précèdent les lignes des abonnements se trouvant dans un état d'avertissement.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **db_owner** ou **replmonitor** rôle de base de données fixe sur la base de données de distribution peut exécuter **sp_replmonitorhelpsubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller la réplication par programmation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
