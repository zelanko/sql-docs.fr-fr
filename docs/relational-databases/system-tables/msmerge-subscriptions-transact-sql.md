---
title: MSmerge_subscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_subscriptions
- MSmerge_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_subscriptions system table
ms.assetid: cafd954a-92f8-44cb-a5d0-dce9aafa5ee1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b00a2e83839724c2b6e5193e2ca08d5c6d3eced9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106313"
---
# <a name="msmergesubscriptions-transact-sql"></a>MSmerge_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_subscriptions** table contient une ligne pour chaque abonnement pris en charge par l’Agent de fusion sur l’abonné. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|L’ID du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication_id**|**int**|ID de la publication.|  
|**subscriber_id**|**smallint**|L’ID de l’abonné.|  
|**bd_abonné**|**sysname**|Le nom de la base de données d’abonnement.|  
|**subscription_type**|**int**|Le type d’abonnement :<br /><br /> 0 = Par envoi de données (push).<br /><br /> 1 = Par extraction de données (pull).<br /><br /> 2 = Anonyme.|  
|**sync_type**|**tinyint**|Type de synchronisation :<br /><br /> 1 = Automatique.<br /><br /> 2 = Pas de synchronisation.|  
|**status**|**tinyint**|L’état de l’abonnement.|  
|**subscription_time**|**datetime**|Heure de création de l'abonnement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
