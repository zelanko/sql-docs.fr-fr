---
title: MSrepl_errors (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSrepl_errors
- MSrepl_errors_TSQL
dev_langs: TSQL
helpviewer_keywords: MSrepl_errors system table
ms.assetid: c6e023c1-2c32-4269-8d76-e442ea309e4b
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 66c276d57f2df480d1d3977304911c2826068cce
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msreplerrors-transact-sql"></a>MSrepl_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSrepl_errors** table contient des lignes avec des informations étendues d’échec de l’Agent de Distribution et l’Agent de fusion. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID de l'erreur.|  
|**time**|**datetime**|Heure de survenue de l'erreur.|  
|**error_type_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**source_type_id**|**int**|ID du type de source de l'erreur.|  
|**source_name**|**nvarchar (100)**|Nom de la source de l'erreur.|  
|**code_erreur**|**sysname**|Code d'erreur.|  
|**texte_erreur**|**ntext**|Message d’erreur.|  
|**xact_seqno**|**varbinary (16)**|Dans le journal des transactions, numéro séquentiel dans le journal de la première transaction du lot dont l'exécution a échoué. Uniquement utilisé par les Agents de distribution, c'est le numéro séquentiel dans le journal de la première transaction dans le lot dont l'exécution a échoué.|  
|**id_de_commande**|**int**|ID de la commande du lot dont l'exécution a échoué. Utilisé uniquement par les Agents de distribution, il s'agit de l'ID de commande de la première commande du lot en échec.|  
|**session_id**|**int**|ID de la session de l'Agent où l'erreur s'est produite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
