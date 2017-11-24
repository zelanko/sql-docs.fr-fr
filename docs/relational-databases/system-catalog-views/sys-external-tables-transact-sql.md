---
title: Sys.external_tables (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4f12fb4189752b8679d1648f2246ebfd1226c42
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysexternaltables-transact-sql"></a>Sys.external_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Contient une ligne pour chaque table externe dans la base de données actuelle.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|\<héritée de colonnes >||Pour obtenir la liste des colonnes qui hérite de cette vue, consultez [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).||  
|max_column_id_used|**int**|ID de colonne maximale jamais utilisé pour cette table.||  
|uses_ansi_nulls|**bit**|Lorsque la table a été créée, l'option de base de données SET ANSI_NULLS avait pour valeur ON.||  
|data_source_id|**int**|ID d’objet pour la source de données externe.||  
|file_format_id|**int**|Pour les tables externes sur une source de données externe HADOOP, il s’agit de l’ID d’objet pour le format de fichier externe.||  
|location|**nvarchar(4000)**|Pour les tables externes sur une source de données externe HADOOP, il s’agit du chemin d’accès des données externes dans HDFS.||  
|reject_type|**tinyint**|Pour les tables externes sur une source de données externe HADOOP, il s’agit de la façon de lignes rejetées sont comptées lors de l’interrogation des données externes.|VALEUR : le nombre de lignes rejetées.<br /><br /> POURCENTAGE – le pourcentage de lignes rejetées.|  
|reject_value|**float**|Pour les tables externes sur une source de données externe HADOOP :<br /><br /> Pour *reject_type =* valeur, il s’agit du nombre de rejets de ligne à autoriser avant l’échec de la requête.<br /><br /> Pour *reject_type* = pourcentage, il s’agit du pourcentage de rejets de ligne à autoriser avant l’échec de la requête.||  
|reject_sample_value|**int**|Pour *reject_type* = pourcentage, il s’agit du nombre de lignes à charger, soit avec succès, ou non, avant de calculer le pourcentage de lignes rejetées.|NULL si reject_type = valeur.|  
|distribution_type|**int**|Pour les tables externes sur une source de données externes SHARD_MAP_MANAGER, il s’agit des lignes de la distribution des données entre les tables de base sous-jacentes.|0 – partitionnée<br /><br /> 1 – répliquées<br /><br /> 2 – tourniquet (Round Robin)|  
|distribution_desc|**nvarchar(120)**|Pour les tables externes sur une source de données externes SHARD_MAP_MANAGER, il s’agit du type de distribution affiché sous forme de chaîne.||  
|sharding_column_id|**int**|Pour les tables externes sur une source de données externes SHARD_MAP_MANAGER et une distribution partitionnée, il s’agit de l’ID de colonne de la colonne qui contient les valeurs de clé de partitionnement.||  
|remote_schema_name|**sysname**|Pour les tables externes sur une source de données externes SHARD_MAP_MANAGER, il s’agit du schéma où se trouve la table de base sur les bases de données à distance (si différent de celui où la table externe est définie).||  
|remote_object_name|**sysname**|Pour les tables externes sur une source de données externes SHARD_MAP_MANAGER, ceci est le nom de la table de base sur les bases de données à distance (si différent du nom de la table externe).||  
  
## <a name="permissions"></a>Permissions  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.external_file_formats &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [Sys.external_data_sources &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
