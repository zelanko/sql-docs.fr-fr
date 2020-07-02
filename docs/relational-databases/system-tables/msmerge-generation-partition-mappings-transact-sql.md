---
title: MSmerge_generation_partition_mappings (T-SQL)
description: Décrit la procédure stockée MSmerge_generation_partition_mappings utilisée pour effectuer le suivi des modifications apportées aux partitions dans une publication de fusion.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_generation_partition_mappings_TSQL
- MSmerge_generation_partition_mappings
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_generation_partition_mappings system table
ms.assetid: 443a4024-ce48-4772-9ee5-95bd6fb6476b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 59adf719aa4647e8382b8c06fa838d7acf2b3feb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736756"
---
# <a name="msmerge_generation_partition_mappings-transact-sql"></a>MSmerge_generation_partition_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  La table **MSmerge_generation_partition_mappings** permet d’effectuer le suivi des modifications apportées aux partitions dans une publication de fusion. Cette table est stockée dans les bases de données de publication et scubscription.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Identifie la publication de fusion.|  
|**toute**|**bigint**|Valeur de génération.|  
|**partition_id**|**int**|Identifie la partition.|  
|**changecount**|**int**|Nombre de fois où la partition a été modifiée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
