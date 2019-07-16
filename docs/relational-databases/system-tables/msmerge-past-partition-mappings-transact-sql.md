---
title: MSmerge_past_partition_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_past_partition_mappings
- MSmerge_past_partition_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_past_partition_mappings system table
ms.assetid: 06d54ff5-4d29-4eeb-b8be-64d032e53134
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d56debf540de7b1e7f33f741fdd4c3f52d3f04a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984893"
---
# <a name="msmergepastpartitionmappings-transact-sql"></a>MSmerge_past_partition_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_past_partition_mappings** table stocke une ligne pour chaque id de partition une ligne modifiée donnée appartenait appartenir à, mais n’appartient plus. Cette table est stockée dans la base de données de publication.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Le numéro de publication, qui est stocké dans **sysmergepublications**.|  
|**tablenick**|**Int**|Surnom de la table publiée.|  
|**rowguid**|**uniqueidentifier**|Identificateur de ligne pour la ligne concernée.|  
|**partition_id**|**int**|ID de la partition à laquelle la ligne appartient. La valeur est -1 si la modification de ligne s’applique à tous les abonnés.|  
|**génération**|**bigint**|Valeur de la génération dans laquelle la modification de partition s'est produite.|  
|**reason**|**tinyint**|Interne-usage uniquement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
