---
title: MSdynamicsnapshotjobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotjobs_TSQL
- MSdynamicsnapshotjobs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotjobs system table
ms.assetid: 4f36a325-0e3c-46c4-aeeb-416346cce0bc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8b7934d914af50d61df554c2a82ae221a1d5490f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52817281"
---
# <a name="msdynamicsnapshotjobs-transact-sql"></a>MSdynamicsnapshotjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdynamicsnapshotjobs** table effectue le suivi des informations sur les filtres de lignes paramétrable appliquées pour générer un instantané de données filtrées. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|ID de la tâche d'instantané des données filtrées.|  
|**nom**|**sysname**|Nom de la tâche d'instantané des données filtrées.|  
|**pubid**|**uniqueidentifier**|Numéro d'identification unique de cette publication.|  
|**job_id**|**uniqueidentifier**|L’ID du travail de l’Agent SQL Server sur le serveur de distribution.|  
|**agent_id**|**Int**|ID de l’Agent SQL Server.|  
|**dynamic_filter_login**|**sysname**|La valeur utilisée pour évaluer la [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) fonction dans le filtre de lignes paramétrable défini pour la publication.|  
|**dynamic_filter_hostname**|**sysname**|La valeur utilisée pour évaluer la [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) fonction dans le filtre de lignes paramétrable défini pour la publication.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Chemin d'accès au dossier à partir duquel les fichiers d'instantané sont lus en cas d'utilisation d'un instantané de données filtrées.|  
|**partition_id**|**Int**|ID de la partition de données à laquelle la tâche appartient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
