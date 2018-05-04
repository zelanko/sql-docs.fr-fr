---
title: MSmerge_current_partition_mappings | Documents Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSmerge_current_partition_mappings
- MSmerge_current_partition_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_current_partition_mappings system table
ms.assetid: a3088840-5a30-40f5-8e8a-aa03afc4905f
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e5e6b8c70196b6f6473f8bd9ef1203e64a61ad9d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="msmergecurrentpartitionmappings"></a>MSmerge_current_partition_mappings
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_current_partition_mappings** table stocke une ligne pour chaque id de partition appartient une ligne modifiée donnée. Cette table est stockée dans la base de données de publication.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Le numéro de publication, qui est stocké dans **sysmergepublications**.|  
|**tablenick**|**int**|Surnom de la table publiée.|  
|**ROWGUID**|**uniqueidentifier**|Identificateur de ligne pour la ligne concernée.|  
|**partition_id**|**int**|Identificateur de la partition à laquelle appartient la ligne. La valeur est –1 si la modification de ligne concerne tous les abonnés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
