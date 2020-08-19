---
description: MSmerge_current_partition_mappings
title: MSmerge_current_partition_mappings | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_current_partition_mappings
- MSmerge_current_partition_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_current_partition_mappings system table
ms.assetid: a3088840-5a30-40f5-8e8a-aa03afc4905f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d854b7a913ad181f744592c42fdb08861de7e0ca
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469058"
---
# <a name="msmerge_current_partition_mappings"></a>MSmerge_current_partition_mappings
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La table **MSmerge_current_partition_mappings** stocke une ligne pour chaque ID de partition auquel appartient une ligne modifiée donnée. Cette table est stockée dans la base de données de publication.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publication_number**|**smallint**|Numéro de publication, qui est stocké dans **sysmergepublications**.|  
|**tablenick**|**int**|Surnom de la table publiée.|  
|**rowguid**|**uniqueidentifier**|Identificateur de ligne pour la ligne concernée.|  
|**partition_id**|**int**|Identificateur de la partition à laquelle appartient la ligne. La valeur est-1 si la modification de ligne s’applique à tous les abonnés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
