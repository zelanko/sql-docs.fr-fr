---
title: sys.dm_db_column_store_row_group_physical_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_column_store_row_group_physical_stats_TSQL
- sys.dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_column_store_row_group_physical_stats
- sys.dm_db_column_store_row_group_physical_stats dynamic management view
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1460ef53098a9cdd7cf8bb1672c45cfd27adff57
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822733"
---
# <a name="sysdmdbcolumnstorerowgroupphysicalstats-transact-sql"></a>sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Fournit des informations au niveau du groupe de lignes actuelles sur tous les index columnstore dans la base de données actuelle.  
  
 Cela permet d’étendre l’affichage catalogue [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md).  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de la table sous-jacente.|  
|**index_id**|**Int**|ID de cet index columnstore sur *object_id* table.|  
|**partition_number**|**Int**|ID de la partition de table qui contient *row_group_id*. Utilisez partition_number pour joindre cette vue DMV à sys.partitions.|  
|**row_group_id**|**Int**|ID de ce groupe de lignes. Pour les tables partitionnées, il est unique au sein de la partition.<br /><br /> -1 pour une fin en mémoire.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id pour un groupe de lignes dans le magasin delta.<br /><br /> NULL si le groupe de lignes n’est pas dans le magasin delta.<br /><br /> NULL pour la fin d’une table en mémoire.|  
|**state**|**tinyint**|Numéro d’identification associé *state_description*.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = OBJET TOMBSTONE<br /><br /> COMPRESSED est le seul état qui s’applique aux tables en mémoire.|  
|**state_desc**|**nvarchar(60)**|Description de l’état de groupe de lignes :<br /><br /> INVISIBLE - un groupe de lignes en cours de construction. Exemple : <br />Un groupe de lignes dans le columnstore est INVISIBLE, tandis que les données sont compressées. Une fois que la compression est une modification des métadonnées commutateur l’état de la ligne de columnstore groupe de INVISIBLE compressés, et l’état du groupe de lignes deltastore de fermé à l’objet TOMBSTONE.<br /><br /> Ouvrez - un groupe de lignes du deltastore qui accepte les nouvelles lignes. Un groupe de lignes ouvert est toujours au format rowstore et n'a pas été compressé au format columnstore.<br /><br /> FERMÉ - un groupe de lignes dans le magasin delta qui contient le nombre maximal de lignes et est en attente pour le processus de moteur de tuple à compresser dans le columnstore.<br /><br /> COMPRESSÉ - un groupe de lignes qui est compressé avec la compression columnstore et stocké dans le columnstore.<br /><br /> Objet TOMBSTONE - un groupe de lignes qui se trouvait auparavant dans le deltastore et n’est plus utilisé.|  
|**total_rows**|**bigint**|Nombre de lignes physiques stocké dans le groupe de lignes. Pour les groupes de lignes compressé, cela inclut les lignes qui sont marquées à supprimer.|  
|**deleted_rows**|**bigint**|Nombre de lignes stockées physiquement dans un groupe de lignes compressés qui sont marqués pour suppression.<br /><br /> 0 pour les groupes de lignes qui se trouvent dans le magasin delta.|  
|**size_in_bytes**|**bigint**|Taille combinée, en octets, de toutes les pages dans ce groupe de lignes. Cette taille n’inclut pas la taille requise pour stocker les métadonnées ou les dictionnaires partagés.|  
|**trim_reason**|**tinyint**|Raison qui a déclenché le groupe de lignes compressés d’avoir inférieur le nombre maximal de lignes.<br /><br /> 0 - UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1 - NO_TRIM<br /><br /> 2 - CHARGEMENT EN MASSE<br /><br /> 3 - REORG<br /><br /> 4 - DICTIONARY_SIZE<br /><br /> 5 - MEMORY_LIMITATION<br /><br /> 6 - RESIDUAL_ROW_GROUP<br /><br /> 7  -  STATS_MISMATCH<br /><br /> 8 - DÉBORDEMENT|  
|**trim_reason_desc**|**nvarchar(60)**|Description de *trim_reason*.<br /><br /> 0 - UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION : S’est produite lors de la mise à niveau à partir de la version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 - NO_TRIM : Le groupe de lignes n’était pas tronqué. Le groupe de lignes a été compressé avec un maximum de 1,048,476 lignes.  Le nombre de lignes peut être inférieure si un subsset de lignes a été supprimé après la fermeture de rowgroup delta<br /><br /> 2 - LE CHARGEMENT EN BLOC : La taille de lot de chargement en masse limité le nombre de lignes.<br /><br /> 3 - REORG :  Forcé de la compression dans le cadre de la commande REORG.<br /><br /> 4 - DICTIONARY_SIZE : Taille du dictionnaire a augmenté de trop grande pour compresser toutes les lignes ensemble.<br /><br /> 5 - MEMORY_LIMITATION : Mémoire insuffisante pour compresser toutes les lignes ensemble.<br /><br /> 6 - RESIDUAL_ROW_GROUP :  Fermé dans le cadre du dernier groupe de lignes avec des millions de lignes < 1 pendant l’opération de génération d’index<br /><br /> STATS_MISMATCH : Uniquement pour columnstore sur la table en mémoire. Si les statistiques incorrectement indiqué > = 1 million de lignes complet dans la fin, mais nous avons trouvé moins, le rowgroup compressé a < 1 millions de lignes<br /><br /> DÉBORDEMENT : Uniquement pour columnstore sur la table en mémoire. Si la fin du a > 1 millions de lignes complet, les dernières lignes restantes de lot sont compressés si le nombre est compris entre 100k et 1 million|  
|**transition_to_compressed_state**|TINYINT|Montre comment ce groupe de lignes a été déplacé du deltastore à un état compressé dans le columnstore.<br /><br /> 1 - NOT_APPLICABLE<br /><br /> 2 - INDEX_BUILD<br /><br /> 3 - TUPLE_MOVER<br /><br /> 4 - REORG_NORMAL<br /><br /> 5 - REORG_FORCED<br /><br /> 6 - CHARGEMENT EN MASSE<br /><br /> 7 - FUSION|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE - l’opération ne s’applique pas dans le deltastore. Ou, le rowgroup a été compressé avant la mise à niveau vers [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] auquel cas l’historique n’est pas conservé.<br /><br /> INDEX_BUILD - création d’un index ou la reconstruction d’index compressés le groupe de lignes.<br /><br /> TUPLE_MOVER - le moteur de tuple en cours d’exécution en arrière-plan compressé le groupe de lignes. Cela se produit une fois que le groupe de lignes change d’état d’ouvert fermé.<br /><br /> REORG_NORMAL - l’opération de réorganisation, ALTER INDEX... RÉORGANISATION, déplacé le rowgroup fermé du deltastore dans le columnstore. Cela s’est produite avant que le moteur de tuple eu le temps de déplacer le groupe de lignes.<br /><br /> REORG_FORCED - ce groupe de lignes a été ouvert dans le deltastore et a été forcé dans le columnstore avant qu’elle avait un nombre total de lignes.<br /><br /> Chargement en bloc - une opération de chargement en bloc compressé le groupe de lignes directement sans utiliser le deltastore.<br /><br /> FUSION - une opération de fusion consolidées un ou plusieurs rowgroups dans ce groupe de lignes, puis effectué la compression columnstore.|  
|**has_vertipaq_optimization**|bit|L’optimisation Vertipaq améliore la compression columnstore en réorganisant l’ordre des lignes dans le groupe de lignes pour obtenir une compression plus élevée. Cette optimisation s’effectue automatiquement dans la plupart des cas. Il existe deux cas Vertipaq optimisation n’est pas utilisée :<br/>  A. Dans ce cas quand un rowgroup delta se déplace dans le columnstore et il existe un ou plusieurs index non cluster sur l’index columnstore - optimisation de Vertipaq est ignorée pour réduit les modifications apportées à l’index de mappage ;<br/> B. pour les index columnstore sur les tables optimisées en mémoire. <br /><br /> 0 = Non<br /><br /> 1 = Oui|  
|**generation**|BIGINT|Génération du groupe de lignes associée à ce groupe de lignes.|  
|**created_time**|datetime2|Heure de création de ce groupe de lignes.<br /><br /> NULL - pour un index columnstore sur une table en mémoire.|  
|**closed_time**|datetime2|Heure pour la fermeture de ce groupe de lignes.<br /><br /> NULL - pour un index columnstore sur une table en mémoire.|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="results"></a>Résultats  
 Retourne une ligne pour chaque groupe de lignes dans la base de données actuelle.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite ces autorisations :  
  
-   Autorisation CONTROL sur la table.  
  
-   Autorisation VIEW DATABASE STATE sur la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-calculate-fragmentaton-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. Calculer fragmentaton pour décider quand réorganiser ou reconstruire un index columnstore.  
 Pour les index columnstore, le pourcentage de lignes supprimées est une bonne mesure pour la fragmentation dans un groupe de lignes. Lorsque la fragmentation est de 20 % ou plus nous vous recommandons de supprimer les lignes supprimées.  Pour obtenir des exemples, consultez [défragmentation des index Columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md).  
  
 Cet exemple joint **sys.dm_db_column_store_row_group_physical_stats** avec un autre système des tables, puis calcule la `Fragmentation` colonne sous la forme d’une estimation de l’efficacité de chaque groupe de lignes dans la base de données actuelle.     Pour rechercher des informations sur une seule table, supprimez le commentaire des traits d’union devant le **où** clause et fournir un nom de table.  
  
```sql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/NULLIF(total_rows,0) AS 'Fragmentation'
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Interrogation des catalogues système SQL Server FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guide des index columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
