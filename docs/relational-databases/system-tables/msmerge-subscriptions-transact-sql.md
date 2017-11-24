---
title: MSmerge_subscriptions (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- MSmerge_subscriptions
- MSmerge_subscriptions_TSQL
dev_langs: TSQL
helpviewer_keywords: MSmerge_subscriptions system table
ms.assetid: cafd954a-92f8-44cb-a5d0-dce9aafa5ee1
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a58f591a2149080f86d8bc1b2dac57459b35a71a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msmergesubscriptions-transact-sql"></a>MSmerge_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_subscriptions** table contient une ligne pour chaque abonnement pris en charge par l’Agent de fusion sur l’abonné. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|L’ID du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**id_de_la_publication**|**int**|ID de la publication.|  
|**subscriber_id**|**smallint**|L’ID de l’abonné.|  
|**bd_abonné**|**sysname**|Le nom de la base de données d’abonnement.|  
|**subscription_type**|**int**|Le type d’abonnement :<br /><br /> 0 = Par envoi de données (push).<br /><br /> 1 = Par extraction de données (pull).<br /><br /> 2 = Anonyme.|  
|**sync_type**|**tinyint**|Type de synchronisation :<br /><br /> 1 = Automatique.<br /><br /> 2 = Pas de synchronisation.|  
|**status**|**tinyint**|L’état de l’abonnement.|  
|**subscription_time**|**datetime**|Heure de création de l'abonnement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
