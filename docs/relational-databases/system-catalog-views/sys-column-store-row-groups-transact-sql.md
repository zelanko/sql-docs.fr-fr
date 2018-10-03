---
title: Sys.column_store_row_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_row_groups_TSQL
- column_store_row_groups
- sys.column_store_row_groups
- column_store_row_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_row_groups catalog view
ms.assetid: 76e7fef2-d1a4-4272-a2bb-5f5dcd84aedc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: bff4582f8bf46d094db2a1689ad8c9fd6de92185
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782897"
---
# <a name="syscolumnstorerowgroups-transact-sql"></a>sys.column_store_row_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les index cluster columnstore pour chaque segment afin d'aider l'administrateur à prendre des décisions de gestion du système. **Sys.column_store_row_groups** a une colonne pour le nombre total de lignes stockées physiquement (y compris celles marquées comme supprimées) et une colonne pour le nombre de lignes marquées comme supprimées. Utilisez **sys.column_store_row_groups** pour déterminer la ligne les groupes ont un pourcentage élevé de lignes supprimées et doivent être reconstruits.  
   
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de la table sur laquelle cet index est défini.|  
|**index_id**|**Int**|ID de l'index de la table qui contient cet index columnstore.|  
|**partition_number**|**Int**|ID de la partition de table qui contient le row_group_id de groupe de lignes. Utilisez partition_number pour joindre cette vue DMV à sys.partitions.|  
|**row_group_id**|**Int**|Numéro de groupe de lignes associé à ce groupe de lignes. Cet ID est unique dans la partition.<br /><br /> -1 = fin d’une table en mémoire.|  
|**delta_store_hobt_id**|**bigint**|Hobt_id des groupe de lignes ouvert dans le magasin delta.<br /><br /> NULL si le groupe de lignes n’est pas dans le magasin delta.<br /><br /> NULL pour la fin d’une table en mémoire.|  
|**state**|**tinyint**|Numéro d'ID associé à state_description.<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED <br /><br /> 4 = OBJET TOMBSTONE|  
|**state_description**|**nvarchar(60)**|Description de l'état permanent du groupe de lignes :<br /><br /> INVISIBLE – Un segment compressé masqué en cours de génération à partir des données dans une banque delta. Les actions de lecture utiliseront la banque delta jusqu'à ce que le segment compressé masqué soit terminé. Ensuite, le nouveau le segment est rendu visible, et la banque delta source est supprimée.<br /><br /> OPEN - Un groupe de lignes en lecture/écriture qui reçoit des enregistrements. Un groupe de lignes ouvert est toujours au format rowstore et n'a pas été compressé au format columnstore.<br /><br /> CLOSED – Un groupe de lignes qui a été renseigné, mais pas encore compressé par le processus du moteur de tuple.<br /><br /> COMPRESSED – Un groupe de lignes rempli et compressé.|  
|**total_rows**|**bigint**|Nombre total de lignes stockées physiquement dans le groupe de lignes. Certaines peuvent avoir été supprimées, mais elles sont toujours stockées. Le nombre maximal de lignes d'un groupe de lignes est 1 048 576 (hexadécimal FFFFF).|  
|**deleted_rows**|**bigint**|Nombre total de lignes marquées comme étant supprimées dans le groupe de lignes. Cette valeur est toujours 0 pour les groupes de lignes DELTA.|  
|**size_in_bytes**|**bigint**|Taille en octets de toutes les données dans ce groupe de lignes (sans les métadonnées ou les dictionnaires partagés), pour les rowgroups DELTA et COLUMNSTORE.|  
  
## <a name="remarks"></a>Notes  
 Retourne une ligne pour chaque groupe de lignes columnstore pour chaque table ayant un index columnstore cluster ou non cluster.  
  
 Utilisez **sys.column_store_row_groups** pour déterminer le nombre de lignes inclus dans le groupe de lignes et la taille du groupe de lignes.  
  
 Lorsque le nombre de lignes supprimées dans un groupe de lignes atteint un fort pourcentage du nombre total de lignes, la table est moins efficace. Reconstruisez l'index columnstore pour réduire la taille de la table, ce qui réduit les E/S disque nécessaires pour lire la table. Pour reconstruire l’index columnstore utilisez le **reconstruire** possibilité du **ALTER INDEX** instruction.  
  
 Le columnstore modifiable insère au préalable de nouvelles données dans un **OPEN** rowgroup, qui est au format rowstore et est également parfois appelé table delta.  Une fois qu’un rowgroup ouvert est saturé, son état passe à **fermé**. Un rowgroup fermé est compressé au format columnstore par le moteur de tuple et son état passe à **COMPRESSED**.  Le moteur de tuple est un processus en arrière-plan qui se réveille régulièrement et vérifie s'il existe des rowgroups fermés prêts à être compressés dans un rowgroup columnstore.  Le moteur de tuple libère également les rowgroups dans lesquels chaque ligne a été supprimée. Rowgroups libérés sont marqués en tant que **TOMBSTONE**. Pour exécuter le moteur de tuple immédiatement, utilisez le **RÉORGANISER** possibilité du **ALTER INDEX** instruction.  
  
 Lorsqu'un groupe de lignes columnstore est rempli, il est compressé, et cesse de recevoir de nouvelles lignes. Lorsque vous supprimez des lignes d'un groupe compressé, elles sont conservées mais sont marquées comme étant supprimées. Les mises à jour dans un groupe compressé sont implémentées comme une suppression du groupe compressé, et une insertion dans un groupe ouvert.  
  
## <a name="permissions"></a>Permissions  
 Retourne des informations pour une table si l’utilisateur a **VIEW DEFINITION** autorisation sur la table.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant joint le **sys.column_store_row_groups** table à d’autres tables système pour retourner des informations sur des tables spécifiques. La colonne calculée `PercentFull` est une estimation de l'efficacité du groupe de lignes. Pour rechercher des informations sur une seule table, supprimez le commentaire des traits d’union devant le **où** clause et fournir un nom de table.  
  
```  
SELECT i.object_id, object_name(i.object_id) AS TableName,   
i.name AS IndexName, i.index_id, i.type_desc,   
CSRowGroups.*,   
100*(total_rows - ISNULL(deleted_rows,0))/total_rows AS PercentFull    
FROM sys.indexes AS i  
JOIN sys.column_store_row_groups AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id  
AND i.index_id = CSRowGroups.index_id   
--WHERE object_name(i.object_id) = '<table_name>'   
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
  
  

