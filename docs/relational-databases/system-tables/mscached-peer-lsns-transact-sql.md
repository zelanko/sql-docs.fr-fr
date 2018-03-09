---
title: MScached_peer_lsns (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MScached_peer_lsns_TSQL
- MScached_peer_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MScached_peer_lsns system table
ms.assetid: f8b6089a-0230-45f9-8c34-9fe0d2a3a74e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93c1c8600541f1f5710cc9dc2fe4675d1433fa92
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mscachedpeerlsns-transact-sql"></a>MScached_peer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MScached_peer_lsns** table est utilisée pour suivre les valeurs LSN dans le journal des transactions qui sont utilisées pour déterminer les commandes à renvoyer à un abonné donné dans la réplication d’égal à égal. Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**éléments agent_id**|**int**|ID de l'Agent de distribution.|  
|**donneur d’ordre**|**sysname**|Nom du serveur de publication d'origine.|  
|**originator_db**|**sysname**|Nom de la base de données de publication d'origine.|  
|**originator_publication_id**|**int**|Identifie la publication d'origine.|  
|**originator_db_version**|**int**|Identifie le numéro de version de la base de données d'origine.|  
|**originator_lsn**|**varbinary (16)**|Numéro de séquence d'enregistrement (LSN)  de la transaction d'origine.|  
  
## <a name="remarks"></a>Notes  
 Les valeurs LSN (numéros de séquence d'enregistrement) sont utilisées uniquement immédiatement après l'insertion. Elles n'ont pas de signification durable dans le système.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
