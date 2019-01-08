---
title: Sys.dm_db_missing_index_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1fc72e290bf1aa495493eb09d5e0db8cf305202e
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52406656"
---
# <a name="sysdmdbmissingindexdetails-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations détaillées sur les index manquants, à l'exclusion des index spatiaux.  
  
 Dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d’exposer ces informations, chaque ligne qui contient les données qui n’appartient pas au locataire connecté est filtrée.  

  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**index_handle**|**Int**|Identifie un index manquant. L'identificateur est unique sur le serveur. **index_handle** est la clé de cette table.|  
|**database_id**|**smallint**|Identifie la base de données dans laquelle réside la table comportant les index manquants.|  
|**object_id**|**Int**|Identifie la table dans laquelle est situé l'index manquant.|  
|**equality_columns**|**nvarchar(4000)**|Liste de colonnes, séparées par des virgules, qui contribuent aux prédicats d'égalité au format :<br /><br /> *table.column* =*constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Liste de colonnes, séparées par des virgules, qui contribuent aux prédicats d'inégalité, par exemple, les prédicats au format :<br /><br /> *table.column* > *constant_value*<br /><br /> Tout opérateur de comparaison autre que "=" exprime l'inégalité.|  
|**included_columns**|**nvarchar(4000)**|Liste de colonnes, séparées par des virgules, requises comme colonnes de couverture pour la requête. Pour plus d’informations sur la couverture ou les colonnes incluses, consultez [créer des index avec colonnes incluses](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Pour les index optimisés en mémoire (hachage et optimisées en mémoire non cluster), ignorer **included_columns**. Toutes les commandes de la table sont incluses dans chaque index optimisé en mémoire.|  
|**instruction**|**nvarchar(4000)**|Nom de la table dans laquelle est situé l'index manquant.|  
  
## <a name="remarks"></a>Notes  
 Informations retournées par **sys.dm_db_missing_index_details** est mis à jour lorsqu’une requête est optimisée par l’optimiseur de requête et n’est pas persistant. Les informations sur les index manquants sont simplement conservées jusqu'au redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les administrateurs de base de données doivent effectuer régulièrement des copies de sauvegarde des informations sur les index manquants s'ils souhaitent les conserver après le recyclage du serveur.  
  
 Pour déterminer l’index manquant regroupe un index manquant donné fait partie de, vous pouvez interroger la **sys.dm_db_missing_index_groups** vue de gestion dynamique en établissant une équijointure avec **sys.dm_db_missing_index_details**  selon le **index_handle** colonne.  

  >[!NOTE]
  >Le jeu de résultats pour cette DMV sont limité à 600 lignes. Chaque ligne contient un index manquant. Si vous avez plus de 600 index manquants, vous devez traiter l’index manquants existants, donc vous pouvez ensuite afficher les plus récents. 
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Utilisation des informations sur les index manquants dans les instructions CREATE INDEX  
 Pour convertir les informations retournées par **sys.dm_db_missing_index_details** dans une instruction CREATE INDEX pour les index optimisés en mémoire et de basée sur disque, les colonnes d’égalité doivent être placées avant les colonnes d’inégalité et ensemble ils doivent constituer la clé de l’index. Les colonnes incluses doivent être ajoutées à l'instruction CREATE INDEX à l'aide de la clause INCLUDE. Pour déterminer un ordre efficace pour les colonnes d'égalité, vous devez les organiser en fonction de leur sélectivité : répertoriez les colonnes les plus sélectives (les colonnes de gauche dans la liste des colonnes).  
  
 Pour plus d’informations sur les index optimisés en mémoire, consultez [index des Tables mémoire optimisées](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Cohérence transactionnelle  
 Si une transaction crée ou supprime une table, les lignes qui contiennent les informations d'index manquants concernant les objets supprimés sont retirées de cet objet de gestion dynamique, ce qui permet de préserver la cohérence des transactions.  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   

## <a name="see-also"></a>Voir aussi  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
