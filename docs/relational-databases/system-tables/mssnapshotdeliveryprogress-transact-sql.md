---
title: MSsnapshotdeliveryprogress (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
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
applies_to:
- SQL Server
f1_keywords:
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d7fbb80963679858339cc1df9206f101968f4f8e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsnapshotdeliveryprogress** table est utilisée pour effectuer le suivi des fichiers qui ont été remis avec succès à l’abonné lorsqu’un instantané est appliqué. Ces données permettent de reprendre la remise des fichiers si l'Agent de fusion ne parvient pas à fournir tous les fichiers pendant la session, de manière à ce que les mêmes fichiers ne soient pas de nouveau remis lors de la prochaine exécution de l'Agent. Cette table est stockée dans la base de données d'abonnement de l'Abonné.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar (260)**|Identifie le chemin d'accès du dossier d'instantané à partir duquel le fichier a été remis. Pour les publications qui utilisent des filtres paramétrés, la chaîne **dynsnap** sera ajouté à la valeur.|  
|**progress_token_hash**|**int**|Une valeur de hachage générée en fonction de la valeur de *progress_token* utilisé améliorer l’efficacité des recherches pour une donnée *progress_token* valeur.|  
|**progress_token**|**nvarchar (500)**|Identifie un fichier remis, sous la forme d'une combinaison du nom du fichier et de son chemin d'accès.|  
|**progress_timestamp**|**datetime**|Le **datetime** valeur qui indique quand un fichier d’instantané a été remis avec succès.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
