---
title: MSmerge_replinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_replinfo_TSQL
- MSmerge_replinfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_replinfo system table
ms.assetid: b0924094-c0cc-49c1-869a-65be0d0465a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 045f9ab13b701b8dbd5e0895531932c21767853f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67909056"
---
# <a name="msmerge_replinfo-transact-sql"></a>MSmerge_replinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSmerge_replinfo** contient une ligne pour chaque abonnement. Cette table effectue le suivi des informations relatives aux abonnements. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**repid**|**uniqueidentifier**|ID unique du réplica.|  
|**use_interactive_resolver**|**bit**|Indique si le résolveur interactif est utilisé au cours de la réconciliation.<br /><br /> **0** = ne pas utiliser le programme de résolution interactif.<br /><br /> **1** = utiliser le résolveur interactif.|  
|**validation_level**|**int**|Type de validation à réaliser sur l'abonnement. Le niveau de validation spécifié peut prendre l'une des valeurs suivantes :<br /><br /> **0** = aucune validation.<br /><br /> **1** = validation de RowCount uniquement.<br /><br /> **2** = RowCount et validation de la somme de contrôle.<br /><br /> **3** = RowCount et validation de somme de contrôle binaire.|  
|**resync_gen**|**bigint**|Numéro de génération utilisé pour la resynchronisation de l'abonnement. La valeur **-1** indique que l’abonnement n’est pas marqué pour la resynchronisation.|  
|**login_name**|**sysname**|Nom de l'utilisateur qui a créé l'abonnement.|  
|**nom d’hôte**|**sysname**|Valeur utilisée par le filtre de lignes paramétré lors de la génération de la partition de l'abonnement.|  
|**merge_jobid**|**Binary(16**|Identificateur du travail de fusion pour cet abonnement.|  
|**sync_info**|**int**|À usage interne uniquement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
