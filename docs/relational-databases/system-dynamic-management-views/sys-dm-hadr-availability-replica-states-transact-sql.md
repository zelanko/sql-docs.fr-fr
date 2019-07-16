---
title: Sys.dm_hadr_availability_replica_states (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_availability_replica_states
- sys.dm_hadr_availability_replica_states_TSQL
- sys.dm_hadr_availability_replica_states
- dm_hadr_availability_replica_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_replica_states dynamic management view
ms.assetid: d2e678bb-51e8-4a61-b223-5c0b8d08b8b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 05964e0557cb08e874424af542b8fc8a57ce0835
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900625"
---
# <a name="sysdmhadravailabilityreplicastates-transact-sql"></a>sys.dm_hadr_availability_replica_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque réplica local et une ligne pour chaque réplica distant dans le même groupe de disponibilité Always On qu'un réplica local. Chaque ligne contient des informations sur l'état d'un réplica donné.  
  
> [!IMPORTANT]  
>  Pour obtenir des informations sur chaque réplica dans un groupe de disponibilité donné, interrogez **sys.dm_hadr_availability_replica_states** sur l’instance de serveur qui héberge le réplica principal. En cas d'interrogation sur une instance de serveur qui héberge un réplica secondaire d'un groupe de disponibilité, cette vue de gestion dynamique retourne uniquement les informations locales pour le groupe de disponibilité.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Identificateur unique du réplica.|  
|**group_id**|**uniqueidentifier**|Identificateur unique du groupe de disponibilité.|  
|**is_local**|**bit**|Si le réplica est local, une des :<br /><br /> 0 = Indique un réplica secondaire distant dans un groupe de disponibilité dont le réplica principal est hébergé par l'instance de serveur local. Cette valeur est présente uniquement sur l'emplacement de réplica principal.<br /><br /> 1 = indique un réplica local. Sur les réplicas secondaires, il s'agit de la seule valeur disponible pour le groupe de disponibilité auquel le réplica appartient.|  
|**role**|**tinyint**|Actuel [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] rôle d’un réplica local ou d’un réplica distant connecté, une des :<br /><br /> 0 = Résolution<br /><br /> 1 = Principal<br /><br /> 2 = Secondaire<br /><br /> Pour plus d’informations sur les rôles des [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], consultez [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).|  
|**role_desc**|**nvarchar(60)**|Description de **rôle**, l’un des :<br /><br /> RESOLVING<br /><br /> PRIMARY<br /><br /> SECONDARY|  
|**operational_state**|**tinyint**|État opérationnel actuel du réplica, une des :<br /><br /> 0 = Basculement en attente<br /><br /> 1 = en attente<br /><br /> 2 = en ligne<br /><br /> 3 = hors connexion<br /><br /> 4 = Échec<br /><br /> 5 = Échec, aucun quorum<br /><br /> NULL = Le réplica n'est pas local.<br /><br /> Pour plus d’informations, consultez [rôles et états opérationnels](#RolesAndOperationalStates), plus loin dans cette rubrique.|  
|**operational\_state\_desc**|**nvarchar(60)**|Description de **opérationnelle\_état**, l’un des :<br /><br /> PENDING_FAILOVER<br /><br /> PENDING<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> FAILED<br /><br /> FAILED_NO_QUORUM<br /><br /> NULL|  
|**récupération\_contrôle d’intégrité**|**tinyint**|Cumul de la **base de données\_état** colonne de la [sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) vue de gestion dynamique. Voici les valeurs possibles et leurs descriptions.<br /><br /> 0 : En cours d’exécution.  Au moins une base de données jointe présente un état de la base de données autre que ONLINE (**base de données\_état** est pas égal à 0).<br /><br /> 1 : En ligne. Toutes les bases de données jointes présentent un état de la base de données d’en ligne (**database_state** est 0).<br /><br /> NULL : **is_local** = 0|  
|**recovery_health_desc**|**nvarchar(60)**|Description de **recovery_health**, l’un des :<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**synchronisation\_contrôle d’intégrité**|**tinyint**|Reflète un cumul de l’état de synchronisation de base de données (**synchronization_state**) de tous les joint les bases de données de disponibilité (également appelé *réplicas*) et le mode de disponibilité de le (réplica mode de validation synchrone ou asynchrone). Le cumul reflète l’état accumulé moins intègre les bases de données sur le réplica. Voici les valeurs possibles et leurs descriptions.<br /><br /> 0 : Non sain.   Au moins une base de données jointe est dans un état NOT SYNCHRONIZING.<br /><br /> 1 : Partiellement sain. Certains réplicas ne sont pas dans l'état de synchronisation cible : les réplicas avec validation synchrone doivent être synchronisés, et les réplicas avec validation asynchrone doivent être en cours de synchronisation.<br /><br /> 2 : Sain. Tous les réplicas sont dans l'état de synchronisation cible : les réplicas avec validation synchrone sont synchronisés, et les réplicas avec validation asynchrone sont en cours de synchronisation.|  
|**synchronization_health_desc**|**nvarchar(60)**|Description de **synchronization_health**, l’un des :<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
|**connected_state**|**tinyint**|Si un réplica secondaire est actuellement connecté au réplica principal. Les valeurs possibles sont indiquées ci-dessous, avec leurs descriptions.<br /><br /> 0 : Déconnecté. La réponse d’un réplica de disponibilité à l’état DISCONNECTED dépend de son rôle : Sur le réplica principal, si un réplica secondaire est déconnecté, ses bases de données secondaires sont marquées comme NOT SYNCHRONIZED sur le réplica principal, qui attend que la base de données secondaire se reconnecter ; Sur un réplica secondaire, lors de la détection qu’il est déconnecté, le réplica secondaire tente de se reconnecter au réplica principal.<br /><br /> 1 : Connecté.<br /><br /> Chaque réplica principal suit l'état de la connexion pour chaque réplica secondaire dans le même groupe de disponibilité. Les réplicas secondaires suivent l'état de connexion du réplica principal uniquement.|  
|**connected_state_desc**|**nvarchar(60)**|Description de **connection_state**, l’un des :<br /><br /> DISCONNECTED<br /><br /> CONNECTED|  
|**last_connect_error_number**|**int**|Numéro de la dernière erreur de connexion.|  
|**last_connect_error_description**|**nvarchar(1024)**|Texte de la **last_connect_error_number** message.|  
|**last_connect_error_timestamp**|**datetime**|Horodatage de date et heure indiquant le moment le **last_connect_error_number** erreur s’est produite.|  
  
##  <a name="RolesAndOperationalStates"></a> Rôles et états opérationnels  
 Le rôle, **rôle**, reflète l’état d’un réplica de disponibilité donné et l’état opérationnel, **operational_state**, indique si le réplica est prêt à traiter les demandes de client pour tous les base de données du réplica de disponibilité. Voici un résumé des états opérationnels possibles pour chaque rôle : RESOLVING, principal et secondaire.  
  
 **RÉSOLUTION :** Lorsqu’un réplica de disponibilité est dans le rôle RESOLVING, les états opérationnels possibles sont comme indiqué dans le tableau suivant.  
  
|État opérationnel|Description|  
|-----------------------|-----------------|  
|PENDING_FAILOVER|Une commande de basculement est traitée pour le groupe de disponibilité.|  
|OFFLINE|Toutes les données de configuration du réplica de disponibilité ont été mises à jour sur le cluster WSFC, ainsi que dans les métadonnées locales, mais le groupe de disponibilité ne dispose pas actuellement de réplica principal.|  
|FAILED|Un échec de lecture s'est produit pendant une tentative de récupération des informations du cluster WSFC.|  
|FAILED_NO_QUORUM|Le nœud local WSFC n'a pas de quorum. Il s'agit d'un état déduit.|  
  
 **PRINCIPAL :** Lorsqu’un réplica de disponibilité a le rôle principal, il est actuellement le réplica principal. Les états opérationnels possibles sont comme indiqué dans le tableau suivant.  
  
|État opérationnel|Description|  
|-----------------------|-----------------|  
|PENDING|Il s'agit d'un état temporaire, mais un réplica principal peut être bloqué dans cet état si les processus de travail ne sont pas disponibles pour traiter les demandes.|  
|ONLINE|La ressource du groupe de disponibilité est en ligne, et tous les threads de travail de base de données ont été sélectionnés.|  
|FAILED|Le réplica de disponibilité ne peut pas lire sur le cluster WSFC et/ou écrire à partir de celui-ci.|  
  
 **BASE DE DONNÉES SECONDAIRE :** Lorsqu’un réplica de disponibilité a le rôle secondaire, il est actuellement un réplica secondaire. Les états opérationnels possibles sont comme indiqué dans le tableau ci-dessous.  
  
|État opérationnel|Description|  
|-----------------------|-----------------|  
|ONLINE|Le réplica secondaire local n'est pas connecté au réplica principal.|  
|FAILED|Le réplica secondaire local ne peut pas lire sur le cluster WSFC et/ou écrire à partir de celui-ci.|  
|NULL|Sur un réplica principal, cette valeur est retournée lorsque la ligne est liée à un réplica secondaire.|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
