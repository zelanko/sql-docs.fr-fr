---
title: MSpeer_topologyresponse (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpeer_topologyresponse
- MSpeer_topologyresponse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_topologyresponse
ms.assetid: 1bc5c0c6-c432-405c-89fd-e953d173a247
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 059fa8cb441bde356e2020a7bf6ffa11e3417ad3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mspeertopologyresponse-transact-sql"></a>MSpeer_topologyresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Permet de stocker la réponse de chaque nœud à une requête de statut de topologie dans le cadre d'une réplication d'égal à égal. Cette table est stockée dans la base de données de publication.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|request_id|**int**|Identifie une entrée de demande de statut de topologie dans le [MSpeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md) table.|  
|peer|**sysname**|Nom de l'instance serveur qui a généré la réponse.|  
|peer_version|**int**|Spécifie le numéro de version du serveur de publication.|  
|peer_db|**sysname**|Base de données abonnement sur l’homologue qui a généré la réponse.|  
|originator_id|**int**|Identifie chaque nœud dans la topologie pour les besoins de la détection de conflit. Pour plus d'informations, consultez [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|peer_conflict_retention|**int**|Durée, en jours, du stockage des métadonnées dans les tables en conflit.|  
|received_date|**datetime**|Heure de réception de la demande de topologie.|  
|connection_info|**xml**|Informations relatives au nœud ayant répondu à la demande.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
