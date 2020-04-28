---
title: sys. external_data_sources (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1016db6e-9950-4ae2-a004-bd4171e27359
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 152265e072d9f21baae715692cada63ee4f7ab11
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68005180"
---
# <a name="sysexternal_data_sources-transact-sql"></a>sys.external_data_sources (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Contient une ligne pour chaque source de données externe de la base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]données [!INCLUDE[ssSDS](../../includes/sssds-md.md)]active pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], et.  
  
 Contient une ligne pour chaque source de données externe sur le serveur [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]pour.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|data_source_id|**int**|ID d’objet de la source de données externe.||  
|name|**sysname**|Nom de la source de données externe.||  
|location|**nvarchar(4000)**|Chaîne de connexion, qui comprend le protocole, l’adresse IP et le port de la source de données externe.||  
|type_desc|**nvarchar(255)**|Type de source de données affiché en tant que chaîne.|HADOOP, SGBDR, SHARD_MAP_MANAGER, RemoteDataArchiveTypeExtDataSource|  
|type|**tinyint**|Type de source de données affiché sous forme de nombre.|0-HADOOP<br /><br /> 1-SGBDR<br /><br /> 2-SHARD_MAP_MANAGER<br /><br /> 3-RemoteDataArchiveTypeExtDataSource|  
|resource_manager_location|**nvarchar(4000)**|Pour le type HADOOP, adresse IP et emplacement du port du gestionnaire de ressources Hadoop. Cela permet d’envoyer un travail sur une source de données Hadoop.<br /><br /> NULL pour les autres types de sources de données externes.||  
|credential_id|**int**|ID d’objet des informations d’identification délimitées à la base de données utilisées pour se connecter à la source de données externe.||  
|database_name|**sysname**|Pour le type SGBDR, nom de la base de données distante. Pour type, SHARD_MAP_MANAGER, nom de la base de données du gestionnaire de cartes de partition. NULL pour les autres types de sources de données externes.||  
|shard_map_name|**sysname**|Pour le type SHARD_MAP_MANAGER, nom de la carte de partition. NULL pour les autres types de sources de données externes.||  
  
## <a name="permissions"></a>Autorisations  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées.  Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sys. external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys. external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  
