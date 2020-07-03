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
ms.openlocfilehash: 7760b7893632f2171edc2b4823f8b87b8313000f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889818"
---
# <a name="msmerge_generation_partition_mappings-transact-sql"></a>MSmerge_generation_partition_mappings (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
  
