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
manager: craigg
ms.openlocfilehash: 4b0c5d53519b09c9f30ccdf7e973e25e5a06a6a3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823593"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsubscriptions** table contient une ligne pour chaque article publié dans un abonnement pris en charge par le serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**Int**|Identificateur de la base de données du serveur de publication.|  
|**publisher_id**|**smallint**|L’ID du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication_id**|**Int**|ID de la publication.|  
|**article_id**|**Int**|L’ID de l’article.|  
|**subscriber_id**|**smallint**|L’ID de l’abonné.|  
|**bd_abonné**|**sysname**|Le nom de la base de données d’abonnement.|  
|**subscription_type**|**Int**|Le type d’abonnement :<br /><br /> **0** = push.<br /><br /> **1** = par extraction.<br /><br /> **2** = anonyme.|  
|**sync_type**|**tinyint**|Type de synchronisation :<br /><br /> **1** = automatique.<br /><br /> **2** = pas de synchronisation.|  
|**status**|**tinyint**|L’état de l’abonnement :<br /><br /> **0** = inactif.<br /><br /> **1** = abonné.<br /><br /> **2** = actif.|  
|**subscription_seqno**|**varbinary(16)**|Numéro de séquence de la transaction d'instantané.|  
|**snapshot_seqno_flag**|**bit**|Indique la source du numéro de séquence de transaction de capture instantanée, où la valeur **1** signifie que **subscription_seqno** est le numéro de séquence de capture instantanée.|  
|**independent_agent**|**bit**|Indique s'il existe un Agent de distribution autonome pour cette publication.|  
|**subscription_time**|**datetime**|À usage interne uniquement|  
|**loopback_detection**|**bit**|S'applique aux abonnements qui font partie d'une topologie de réplication transactionnelle bidirectionnelle. La détection de boucle détermine si l'Agent de distribution renvoie à l'Abonné les transactions émanant de ce dernier :<br /><br /> **1** = ne pas renvoyer.<br /><br /> **0** = renvoie les transactions.<br /><br /> Remarque : Cette colonne n'est prise en charge que dans un but de compatibilité ascendante avec la fonctionnalité de réplication bidirectionnelle de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Pour les versions ultérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez plutôt la fonctionnalité de réplication d'égal à égal. Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
|**agent_id**|**Int**|ID de l'Agent.|  
|**update_mode**|**tinyint**|Type de mise à jour.|  
|**publisher_seqno**|**varbinary(16)**|Numéro de séquence de la transaction au niveau du serveur de publication pour cet abonnement.|  
|**ss_cplt_seqno**|**varbinary(16)**|Numéro de séquence utilisé pour indiquer la fin du traitement de l'instantané concurrent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
