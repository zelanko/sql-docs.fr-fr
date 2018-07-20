---
title: sysmergesubscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergesubscriptions_TSQL
- sysmergesubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubscriptions system table
ms.assetid: 6adc78da-991d-4c08-98c3-ecb4762e0e99
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcbe175a186b42c7bfb8e49290c7594e7b9e67d1
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102497"
---
# <a name="sysmergesubscriptions-transact-sql"></a>sysmergesubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque Abonné connu et constitue une table locale sur le serveur de publication. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|subscriber_server|**sysname**|L’ID du serveur. Permet de mapper le champ srvid avec la valeur propre au serveur lors de la migration d'une copie de la base de données d'abonnement vers un autre serveur.|  
|db_name|**sysname**|Le nom de la base de données à l’abonnement.|  
|pubid|**uniqueidentifier**|ID de la publication à partir de laquelle l'abonnement actuel a été créé.|  
|datasource_type|**Int**|Le type de source de données :<br /><br /> **0** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **2** = jet OLE DB.|  
|subid|**uniqueidentifier**|Numéro d'identification unique de l'abonnement.|  
|replnickname|**binaire**|Surnom compressé du réplica.|  
|replicastate|**uniqueidentifier**|Identificateur unique utilisé pour déterminer si la synchronisation précédente a réussi en comparant la valeur sur l'Éditeur à celle sur l'Abonné.|  
|status|**tinyint**|L’état de l’abonnement :<br /><br /> **0** = inactif.<br /><br /> **1** = actif.<br /><br /> **2** = supprimé.|  
|subscriber_type|**Int**|Le type d’abonné :<br /><br /> **1** = global.<br /><br /> **2** = local.<br /><br /> **3** = anonyme.|  
|subscription_type|**Int**|Le type d’abonnement :<br /><br /> **0** = push.<br /><br /> **1** = par extraction.<br /><br /> **2** = anonyme.|  
|sync_type|**tinyint**|Type de synchronisation :<br /><br /> **1** = automatique.<br /><br /> **2** = pas de synchronisation.|  
|description|**nvarchar(255)**|Brève description de l'abonnement.|  
|priority|**real**|Indique la priorité de l'abonnement et permet l'implémentation d'utilitaires de résolution de conflits basée sur les priorités. Est égal à **0,00** pour tous les abonnements locaux ou anonymes.|  
|recgen|**bigint**|Numéro de la dernière génération reçue.|  
|recguid|**uniqueidentifier**|ID unique de la dernière génération reçue.|  
|sentgen|**bigint**|Numéro de la dernière génération envoyée.|  
|sentguid|**uniqueidentifier**|ID unique de la dernière génération envoyée.|  
|schemaversion|**Int**|Numéro du dernier schéma reçu.|  
|schemaguid|**uniqueidentifier**|ID unique du dernier schéma reçu.|  
|last_validated|**datetime**|Le **datetime** de la dernière validation réussie des données de l’abonné.|  
|attempted_validate|**datetime**|La dernière **datetime** que la validation a été tentée sur l’abonnement.|  
|last_sync_date|**datetime**|Le **datetime** de la synchronisation.|  
|last_sync_status|**Int**|État de l'abonnement :<br /><br /> **0** = tous les travaux sont en attente de démarrage.<br /><br /> **1** = une ou plusieurs travaux commencent.<br /><br /> **2** = tous les travaux ont été correctement exécutées.<br /><br /> **3** = au moins un travail exécute.<br /><br /> **4** = tous les travaux sont planifiés et inactifs.<br /><br /> **5** = au moins un travail est relancée après un échec.<br /><br /> **6** = au moins un travail n’a pas pu s’exécuter avec succès.|  
|last_sync_summary|**sysname**|Description des résultats de la dernière synchronisation.|  
|metadatacleanuptime|**datetime**|La dernière **datetime** métadonnées arrivées à expiration a peut-être été retirée de tables de système de réplication de fusion.|  
|partition_id|**Int**|Identifie la partition précalculée à laquelle appartient l'abonnement.|  
|cleanedup_unsent_changes|**bit**|Indique que les métadonnées relatives aux modifications non envoyées ont été nettoyées sur l'Abonné.|  
|replica_version|**Int**|Identifie la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'abonné auquel appartient l'abonnement. Les valeurs possibles sont :<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|supportability_mode|**Int**|À usage interne uniquement|  
|application_name|**nvarchar(128)**|À usage interne uniquement|  
|subscriber_number|**Int**|À usage interne uniquement|  
|last_makegeneration_datetime|**datetime**|La dernière **datetime** que le processus de makegeneration s’est exécuté pour le serveur de publication. Pour plus d’informations, consultez le paramètre - MakeGenerationInterval dans [Agent de fusion de réplication](../../relational-databases/replication/agents/replication-merge-agent.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
