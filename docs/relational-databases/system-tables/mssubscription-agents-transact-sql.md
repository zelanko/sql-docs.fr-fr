---
title: MSsubscription_agents (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b1b8680343f233c35b704f3805b06ea9dc47c12
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808501"
---
# <a name="mssubscriptionagents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsubscription_agents** table est utilisée par l’Agent de Distribution et des déclencheurs d’abonnements modifiables pour effectuer le suivi des propriétés de l’abonnement. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|L’ID de la ligne.|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**publisher_db**|**sysname**|Le nom de la base de données de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**subscription_type**|**Int**|Type d'abonnement :<br /><br /> 0 = Par envoi de données (push).<br /><br /> 1 = par extraction de données (pull)<br /><br /> 2 = par extraction de données anonyme|  
|**queue_id**|**sysname**|L’ID de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message de file d’attente sur le serveur de publication. *queue_id* a la valeur **SQL** pour SQL en attente basée sur la mise à jour.|  
|**update_mode**|**tinyint**|Type de mise à jour :<br /><br /> **0** = lecture seule.<br /><br /> **1** = mise à jour immédiate.<br /><br /> **2** = mise à jour en file d’attente à l’aide de Message Queuing.<br /><br /> **3** = immédiat mettre à jour avec la mise à jour en file d’attente sous forme de basculement à l’aide de Message Queuing.<br /><br /> **4** = mise à jour en file d’attente à l’aide de la file d’attente de SQL Server.<br /><br /> **5** = mise à jour immédiate avec basculement de mise à jour en file d’attente, à l’aide de la file d’attente de SQL Server.|  
|**failover_mode**|**bit**|Si un type de basculement de mise à jour a été sélectionné, ce paramètre représente le type de basculement choisi :<br /><br /> **0** = exécution mise à jour est utilisé. Le basculement n'est pas activé.<br /><br /> **1** = en file d’attente mise à jour est utilisé. Le basculement est activé. La file d’attente utilisée pour le basculement est spécifié dans le *update_mode* valeur.|  
|**spid**|**Int**|ID de processus système de la connexion utilisée par l'Agent de distribution en cours d'exécution ou récemment exécuté.|  
|**login_time**|**datetime**|Date et heure de la connexion de l'Agent de distribution en cours d'exécution ou récemment exécutée.|  
|**allow_subscription_copy**|**bit**|Indique si la possibilité de copier la base de données d'abonnement est autorisée.|  
|**attach_state**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**binary (16)**|Identificateur unique représentant la version d'un abonnement attaché.|  
|**last_sync_status**|**Int**|État de la dernière exécution de l'Agent de distribution en cours d'exécution ou récemment exécuté. L'état peut prendre l'une des valeurs suivantes :<br /><br /> **1** = démarré.<br /><br /> **2** = a réussi.<br /><br /> **3** = en cours d’exécution.<br /><br /> **4** = inactif.<br /><br /> **5** = nouvelle tentative.<br /><br /> **6** = échec.|  
|**last_sync_summary**|**sysname**|Dernier message de l'Agent de distribution en cours d'exécution ou récemment exécuté. L'état peut prendre l'une des valeurs suivantes :<br /><br /> **Démarré.**<br /><br /> **A réussi.**<br /><br /> **En cours d’exécution.**<br /><br /> **Temps d’inactivité.**<br /><br /> **Nouvelle tentative.**<br /><br /> **Échouer.**|  
|**last_sync_time**|**datetime**|La date et l’heure auxquelles le *last_sync_summary* et *last_sync_status* colonnes ont été mises à jour. Les Agents de distribution anonyme ou par extraction de données exécutés en tant que travaux du service SqlServer Agent ne mettent pas à jour ces colonnes. Dans ce cas, les informations d'historique sont consignées dans la table de l'historique des travaux.|  
|**queue_server**|**sysname**|À usage interne uniquement|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
