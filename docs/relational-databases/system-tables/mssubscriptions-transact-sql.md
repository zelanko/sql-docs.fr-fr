---
title: MSsubscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca4364709462eee9df62baa8193dec9f8ea36241
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74866034"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSsubscriptions** contient une ligne pour chaque article publié dans un abonnement desservi par le serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Identificateur de la base de données du serveur de publication.|  
|**publisher_id**|**smallint**|ID du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication_id**|**int**|ID de la publication.|  
|**article_id**|**int**|ID de l’article.|  
|**subscriber_id**|**smallint**|ID de l’abonné.|  
|**subscriber_db**|**sysname**|Nom de la base de données d’abonnement.|  
|**subscription_type**|**int**|Type d’abonnement :<br /><br /> **0** = push.<br /><br /> **1** = pull.<br /><br /> **2** = anonyme.|  
|**sync_type**|**tinyint**|Type de synchronisation :<br /><br /> **1** = automatique.<br /><br /> **2** = aucune synchronisation.|  
|**statu**|**tinyint**|État de l’abonnement :<br /><br /> **0** = inactif.<br /><br /> **1** = abonné.<br /><br /> **2** = actif.|  
|**subscription_seqno**|**varbinary(16)**|Numéro de séquence de la transaction d'instantané.|  
|**snapshot_seqno_flag**|**bit**|Indique la source du numéro de séquence de la transaction d’instantané, où la valeur **1** signifie que **subscription_seqno** est le numéro de séquence de l’instantané.|  
|**independent_agent**|**bit**|Indique s'il existe un Agent de distribution autonome pour cette publication.|  
|**subscription_time**|**DATETIME**|À usage interne uniquement|  
|**loopback_detection**|**bit**|S'applique aux abonnements qui font partie d'une topologie de réplication transactionnelle bidirectionnelle. La détection de boucle détermine si l'Agent de distribution renvoie à l'Abonné les transactions émanant de ce dernier :<br /><br /> **1** = n’est pas renvoyé.<br /><br /> **0** = renvoie.<br /><br />|  
|**agent_id**|**int**|ID de l'Agent.|  
|**update_mode**|**tinyint**|Type de mise à jour.|  
|**publisher_seqno**|**varbinary(16)**|Numéro de séquence de la transaction au niveau du serveur de publication pour cet abonnement.|  
|**ss_cplt_seqno**|**varbinary(16)**|Numéro de séquence utilisé pour indiquer la fin du traitement de l'instantané concurrent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
