---
title: Sys.internal_partitions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0262df2b-5ba7-4715-b17b-3d9ce470a38e
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a86c559adeeca787ac0e278eed5fb832b8c00bfd
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52537904"
---
# <a name="sysinternalpartitions-transact-sql"></a>Sys.internal_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque ensemble de lignes qui assure le suivi des données internes pour les index columnstore sur les tables sur disque. Ces ensembles de lignes sont internes aux index columnstore et les lignes supprimé de suivi, les mappages de rowgroup et delta magasin rowgroups. Suivre les données pour chaque pour chaque partition de table ; chaque table possède au moins une partition. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recrée les ensembles de lignes chaque fois qu’il reconstruit l’index columnstore.   
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|ID de partition pour cette partition. Unique dans la base de données.|  
|object_id|**Int**|ID d’objet pour la table qui contient la partition.|  
|index_id|**Int**|ID d’index pour l’index columnstore défini sur la table.<br /><br /> 1 = index cluster columnstore<br /><br /> 2 = index non cluster columnstore|  
|partition_number|**Int**|Le numéro de partition.<br /><br /> 1 = la première partition d’une table partitionnée, ou la partition unique d’une table non partitionnée.<br /><br /> 2 = la deuxième partition et ainsi de suite.|  
|internal_object_type|**tinyint**|Objets d’ensemble de lignes qui effectuent le suivi des données internes pour l’index columnstore.<br /><br /> 2 = COLUMN_STORE_DELETE_BITMAP<br /><br /> 3 = COLUMN_STORE_DELTA_STORE<br /><br /> 4 = COLUMN_STORE_DELETE_BUFFER<br /><br /> 5 = COLUMN_STORE_MAPPING_INDEX|  
|internal_object_type_desc|**nvarchar(60)**|COLUMN_STORE_DELETE_BITMAP - cet index de bitmap effectue le suivi des lignes qui sont marquées comme supprimées de l’index columnstore. La bitmap est pour chaque groupe de lignes dans la mesure où les partitions peuvent avoir des lignes dans plusieurs groupes de lignes. Les lignes sont qui se trouvent toujours physiquement présent et permet de l’espace dans le columnstore.<br /><br /> COLUMN_STORE_DELTA_STORE - groupes de magasins de lignes, appelés rowgroups, qui n’ont pas été compressés dans un stockage en colonnes. Chaque partition de table peut avoir zéro ou plusieurs rowgroups deltastore.<br /><br /> COLUMN_STORE_DELETE_BUFFER - pour la maintenance des index columnstore non cluster actualisables des suppressions. Lorsqu’une requête supprime une ligne à partir de la table rowstore sous-jacente, la mémoire tampon de suppression effectue le suivi de la suppression de l’index columnstore. Lorsque le nombre de lignes supprimées dépasse 1048576, ils sont fusionnés dans la bitmap de suppression en arrière-plan des threads de moteur de Tuple ou par une commande Reorganize explicite.  À un moment donné dans le temps, l’union de la bitmap de suppression et de la mémoire tampon de suppression représente supprimés toutes les lignes.<br /><br /> COLUMN_STORE_MAPPING_INDEX - utilisé uniquement lors de l’index cluster columnstore a un index non cluster secondaire. Clés d’index non cluster correspond au rowgroup correct et l’ID de ligne dans le columnstore. Il stocke uniquement des clés pour les lignes qui déplacent vers un autre groupe de lignes ; Cela se produit quand un rowgroup delta est compressé dans le columnstore, et lorsqu’une opération de fusion fusionne les lignes à partir de deux groupes de lignes différentes.|  
|Row_group_id|**Int**|ID de rowgroup deltastore. Chaque partition de table peut avoir zéro ou plusieurs rowgroups deltastore.|  
|hobt_id|**bigint**|ID de l’objet d’ensemble de lignes interne. Il s’agit d’une bonne clé de jointure avec d’autres vues de gestion dynamique pour obtenir plus d’informations sur les caractéristiques physiques de l’ensemble de lignes interne.|  
|lignes|**bigint**|Nombre approximatif de lignes dans cette partition.|  
|data_compression|**tinyint**|L’état de compression pour l’ensemble de lignes :<br /><br /> 0 = AUCUN<br /><br /> 1 = LIGNE<br /><br /> 2 = PAGE|  
|data_compression_desc|**nvarchar(60)**|L’état de compression pour chaque partition. Les valeurs possibles pour les tables rowstore sont AUCUN, LIGNE et PAGE. Les valeurs possibles pour les tables columnstore sont COLUMNSTORE et COLUMNSTORE_ARCHIVE.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recrée les nouveaux index interne columnstore chaque fois qu’il crée ou reconstruit un index columnstore.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-view-all-of-the-internal-rowsets-for-a-table"></a>A. Afficher tous les ensembles de lignes interne pour une table  
 Cet exemple retourne tous les ensembles de lignes columnstore interne pour une table. Vous pouvez également utiliser hobt_id pour trouver plus d’informations sur l’ensemble de lignes spécifique.  
  
```  
SELECT i.object_id, i.index_id, i.name, p.hobt_id, p.internal_object_type_id, p.internal_object_type_desc  
FROM sys.internal_partitions AS p  
JOIN sys.indexes AS i  
on i.object_id = p.object_id  
WHERE p.object_id = OBJECT_ID ( '<table name' ) ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
