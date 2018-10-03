---
title: MSlogreader_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_history_TSQL
- MSlogreader_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_history system table
ms.assetid: 2e399fa1-3591-4c1c-96b7-7964fe82c7c4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ebf9155848d8acd515eea5dad10318c87f54a912
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645187"
---
# <a name="mslogreaderhistory-transact-sql"></a>MSlogreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSlogreader_history** table contient des lignes d’historique pour les Agents de lecture du journal associé à un serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**Int**|ID de l'Agent de lecture du journal.|  
|**runstatus**|**Int**|État d'exécution :<br /><br /> 1 = Démarrage.<br /><br /> 2 = Succès.<br /><br /> 3 = En cours.<br /><br /> 4 = Inactif.<br /><br /> 5 = Nouvel essai.<br /><br /> 6 = Échec.|  
|**start_time**|**datetime**|Heure de démarrage de l'exécution de la tâche|  
|**time**|**datetime**|Heure de consignation du message dans le journal|  
|**duration**|**Int**|Durée, en secondes, de la session de message.|  
|**Commentaires**|**nvarchar(255)**|Texte du message.|  
|**xact_seqno**|**varbinary(16)**|Numéro de séquence de la dernière transaction réalisée.|  
|**delivery_time**|**Int**|La première transaction de temps est remise.|  
|**delivered_transactions**|**Int**|Nombre total des transactions transmises dans la session.|  
|**delivered_commands**|**Int**|Nombre total des commandes transmises dans la session.|  
|**average_commands**|**Int**|Nombre moyen des commandes transmises dans la session.|  
|**delivery_rate**|**float**|Moyenne des commandes transmises par seconde.|  
|**delivery_latency**|**Int**|Temps de latence entre l'entrée de la commande dans la base de données publiée et son entrée dans la base de données de distribution. En millisecondes.|  
|**ID_erreur**|**Int**|L’ID de l’erreur dans le **MSrepl_error** (table système).|  
|**timestamp**|**timestamp**|Colonne timestamp de cette table|  
|**updateable_row**|**bit**|La valeur **1** si la ligne d’historique peut être remplacée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
