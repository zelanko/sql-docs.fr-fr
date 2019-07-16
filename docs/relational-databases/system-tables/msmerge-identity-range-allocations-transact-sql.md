---
title: MSmerge_identity_range_allocations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
author: stevestein
ms.author: sstein
ms.openlocfilehash: de0325925bb1ad1626987361435056ff21a26be6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072650"
---
# <a name="msmergeidentityrangeallocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_identity_range_allocations** table est utilisée pour suivre l’historique de l’identité affectations de plage, à des éditeurs et les abonnés, pour les articles publiés. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|L’ID du serveur de publication.|  
|**publisher_db**|**nvarchar(128)**|Le nom de la base de données de publication.|  
|**publication**|**nvarchar(128)**|Nom de la publication.|  
|**article**|**nvarchar(128)**|Le nom de l’article.|  
|**subscriber** (Abonné)|**nvarchar(128)**|Nom de l'Abonné.|  
|**bd_abonné**|**nvarchar(128)**|Le nom de la base de données d’abonnement.|  
|**is_pub_range**|**bit**|Indique si la plage d'identité est affectée à un serveur de publication.|  
|**ranges_allocated**|**tinyint**|Nombre de plages d'identité affectées.|  
|**range_begin**|**numeric(38)**|Valeur de départ de la plage.|  
|**range_end**|**numeric(38)**|La dernière valeur dans la plage.|  
|**next_range_begin**|**numeric(38)**|Valeur de début de la plage suivante à affecter.|  
|**next_range_end**|**numeric(38)**|Valeur de fin de la plage suivante à affecter.|  
|**max_used**|**numeric(38)**|Valeur d'identité la plus élevée utilisée.|  
|**time_of_allocation**|**datetime**|Heure à laquelle l'affectation a été faite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
