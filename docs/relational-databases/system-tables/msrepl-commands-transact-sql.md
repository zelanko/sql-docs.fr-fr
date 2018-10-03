---
title: MSrepl_commands (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSrepl_commands
- MSrepl_commands_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_commands system table
ms.assetid: 53b9f9cd-9429-47a0-aba2-908fc60e7036
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 44b9b1868959b744bf0d24300f828b351b521f54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834517"
---
# <a name="msreplcommands-transact-sql"></a>MSrepl_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSrepl_commands** table contient des lignes de commandes répliquées. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**Int**|Identificateur de la base de données du serveur de publication.|  
|**xact_seqno**|**varbinary(16)**|Numéro de séquence de transaction.|  
|**type**|**Int**|Type de commande.|  
|**article_id**|**Int**|L’ID de l’article.|  
|**originator_id**|**Int**|ID du point de départ.|  
|**command_id**|**Int**|L’ID de la commande.|  
|**commande_partielle**|**bit**|Indique s'il s'agit d'une commande partielle|  
|**commande**|**varbinary(1024)**|La valeur de commande.|  
|**hashkey**|**Int**|Interne-usage uniquement.|  
|**originator_lsn**|**varbinary(16)**|Identifie le LSN de la commande dans la publication d'origine. Utilisé dans la réplication transactionnelle d'égal à égal.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)  
  
  
