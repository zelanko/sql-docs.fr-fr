---
title: MSdistribution_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_history
- MSdistribution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_history system table
ms.assetid: 55665bd2-9e1d-4efc-8f60-c63a24f66b28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 305223fca45bb1916598f02c16cc4e38981e861d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903668"
---
# <a name="msdistributionhistory-transact-sql"></a>MSdistribution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdistribution_history** table contient des lignes d’historique pour les Agents de Distribution associés à un serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**Int**|ID de l'Agent de distribution.|  
|**runstatus**|**Int**|L’état en cours d’exécution :<br /><br /> **1** = démarrage.<br /><br /> **2** = réussisse.<br /><br /> **3** = en cours d’exécution.<br /><br /> **4** = inactif.<br /><br /> **5** = nouvelle tentative.<br /><br /> **6** = échec.|  
|**start_time**|**datetime**|Heure de démarrage de l'exécution de la tâche|  
|**time**|**datetime**|Heure de consignation du message dans le journal|  
|**duration**|**Int**|Durée, en secondes, de la session de message.|  
|**comments**|**nvarchar(4000)**|Texte du message.|  
|**xact_seqno**|**varbinary(16)**|Numéro de séquence de la dernière transaction réalisée.|  
|**current_delivery_rate**|**float**|Nombre moyen de commandes transmises par seconde depuis la dernière entrée de commande dans l'historique.|  
|**current_delivery_latency**|**Int**|Temps de latence entre l'entrée de la commande dans la base de données de distribution et son application à l'abonné depuis la dernière entrée dans l'historique. En millisecondes.|  
|**delivered_transactions**|**Int**|Nombre total des transactions transmises dans la session.|  
|**delivered_commands**|**Int**|Nombre total des commandes transmises dans la session.|  
|**average_commands**|**Int**|Nombre moyen des commandes transmises dans la session.|  
|**delivery_rate**|**float**|Moyenne des commandes transmises par seconde.|  
|**delivery_latency**|**Int**|Temps de latence entre l'entrée de la commande dans la base de données de distribution et son application à l'abonné. En millisecondes.|  
|**total_delivered_commands**|**bigint**|Nombre total de commandes transmises depuis la création de l'abonnement.|  
|**error_id**|**Int**|L’ID de l’erreur dans le **MSrepl_error** (table système).|  
|**updateable_row**|**bit**|La valeur **1** si la ligne d’historique peut être remplacée.|  
|**timestamp**|**timestamp**|Colonne timestamp de cette table|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
