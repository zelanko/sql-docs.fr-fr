---
title: sys. column_store_segments (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8d476e2f21693254eac5fc4712d53ac854e74ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68140003"
---
# <a name="syscolumn_store_segments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Retourne une ligne pour chaque segment de colonne dans un index ColumnStore. Il y a un segment de colonne par colonne par rowgroup. Par exemple, une table contenant 10 colonnes RowGroups et 34 renvoie 340 lignes. 
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Indique l'ID de partition. Unique dans une base de données.|  
|**hobt_id**|**bigint**|ID du segment ou de l'index d'arbre B (B-tree) pour la table ayant cet index columnstore.|  
|**column_id**|**int**|ID de la colonne columnstore.|  
|**segment_id**|**int**|ID du rowgroup. Pour la compatibilité descendante, le nom de colonne continue d’être appelé segment_id même s’il s’agit de l’ID rowgroup. Vous pouvez identifier un segment de manière unique \<à l’aide de hobt_id, partition_id, column_id>, <segment_id>.|  
|**Version**|**int**|Version du format de segment de colonne.|  
|**encoding_type**|**int**|Type d’encodage utilisé pour ce segment :<br /><br /> 1 = VALUE_BASED non chaîne/binaire sans dictionnaire (très similaire à 4 avec certaines variations internes)<br /><br /> 2 = VALUE_HASH_BASED-colonne non chaîne/binaire avec des valeurs communes dans le dictionnaire<br /><br /> 3 = STRING_HASH_BASED-chaîne/colonne binaire avec des valeurs communes dans le dictionnaire<br /><br /> 4 = STORE_BY_VALUE_BASED-non-chaîne/binaire sans dictionnaire<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED chaîne/binaire sans dictionnaire<br /><br /> Tous les encodages tirent parti de l’encodage de bits et de la longueur d’exécution lorsque cela est possible.|  
|**row_count**|**int**|Nombre de lignes dans le groupe de lignes.|  
|**has_nulls**|**int**|1 si le segment de colonne a des valeurs NULL.|  
|**base_id**|**bigint**|ID de la valeur de base si le type d’encodage 1 est utilisé.  Si le type d’encodage 1 n’est pas utilisé, base_id a la valeur-1.|  
|**magnitude**|**float**|Magnitude si le type d’encodage 1 est utilisé.  Si le type d’encodage 1 n’est pas utilisé, l’argument magnitude a la valeur-1.|  
|**primary_dictionary_id**|**int**|La valeur 0 représente le dictionnaire global. La valeur-1 indique qu’il n’existe aucun dictionnaire global créé pour cette colonne.|  
|**secondary_dictionary_id**|**int**|Une valeur différente de zéro pointe vers le dictionnaire local de cette colonne dans le segment actuel (c’est-à-dire, rowgroup). La valeur-1 indique qu’il n’existe aucun dictionnaire local pour ce segment.|  
|**min_data_id**|**bigint**|ID de données minimum dans le segment de colonne.|  
|**max_data_id**|**bigint**|ID de données maximum dans le segment de colonne.|  
|**null_value**|**bigint**|Valeur utilisée pour représenter les valeurs NULL.|  
|**on_disk_size**|**bigint**|Taille de segment en octets.|  
  
## <a name="remarks"></a>Notes  
 La requête suivante retourne des informations sur les segments d'un index columnstore.  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>Autorisations  
 Toutes les colonnes requièrent au moins l’autorisation **View definition** sur la table. Les colonnes suivantes retournent la valeur null, sauf si l’utilisateur a également l’autorisation **Select** : has_nulls, base_id, magnitude, min_data_id, max_data_id et null_value.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Interrogation du SQL Server FAQ du catalogue système](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys. Columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys. computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guide des index ColumnStore](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys. column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

