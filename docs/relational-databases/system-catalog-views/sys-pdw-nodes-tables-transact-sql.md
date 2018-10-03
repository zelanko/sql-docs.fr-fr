---
title: Sys.pdw_nodes_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 473b5d14-171b-4a16-9195-acf36d3f786c
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a8d89adf13e2e377122321fd8e385b96888e699e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47817477"
---
# <a name="syspdwnodestables-transact-sql"></a>Sys.pdw_nodes_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque objet de table qui détient un principal ou sur lequel le principal a accordé des autorisations.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|\<héritée de colonnes >||Pour obtenir la liste des colonnes qui hérite de cette vue, consultez [sys.objects](http://msdn.microsoft.com/c36fa71e-549a-4533-a6cd-1314d26f533f).||  
|lob_data_space_id|**Int**||Toujours 0.|  
|filestream_data_space_id|**Int**|ID de l’espace de données pour un groupe de fichiers FILESTREAM ou [!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**Int**|ID de colonne maximum utilisé par cette table.||  
|lock_on_bulk_load|**bit**|La table est verrouillée pour le chargement en masse.|TBD|  
|uses_ansi_nulls|**bit**|Lorsque la table a été créée, l'option de base de données SET ANSI_NULLS avait pour valeur ON.|1|  
|is_replicated|**bit**|1 = table est publiée à l’aide de la réplication.|0 ; la réplication n’est pas pris en charge.|  
|has_replication_filter|**bit**|1 = la table possède un filtre de réplication.|0|  
|is_merge_published|**bit**|1 = la table est publiée à l'aide de la réplication de fusion.|0 ; non pris en charge.|  
|is_sync_tran_subscribed|**bit**|1 = la table est abonnée à l'aide d'un abonnement avec mise à jour immédiate.|0 ; non pris en charge.|  
|has_unchecked_assembly_data|**bit**|1 = La table contient des données persistantes qui dépendent d'un assembly dont la définition a été modifiée lors de la dernière exécution de ALTER ASSEMBLY. Cette valeur est réinitialisée à 0 après exécution correcte de l'opération DBCC CHECKDB ou DBCC CHECKTABLE suivante.|0 ; Aucune prise en charge CLR.|  
|text_in_row_limit|**Int**|0 = l'option « text in row » n'est pas définie.|Toujours 0.|  
|large_value_types_out_of_row|**bit**|1 = les types de valeur élevée sont stockés en dehors de la ligne.|Toujours 0.|  
|is_tracked_by_cdc|**bit**|1 = table est activée pour la capture de données modifiées|Toujours 0 ; Aucune prise en charge de la capture de données modifiées.|  
|lock_escalation|**tinyint**|La valeur de l’option LOCK_ESCALATION pour la table : 2 = AUTO|Toujours 2.|  
|lock_escalation_desc|**nvarchar(60)**|Description textuelle de l’option lock_escalation.|Toujours ꞌAUTOꞌ.|  
|pdw_node_id|**Int**|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nœud.|NOT NULL|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
