---
title: sys.dm_db_page_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_page_info
- sys.dm_db_page_info_TSQL
- dm_db_page_info
- dm_db_page_info_TSQL
- dbcc page
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_page_info dynamic management view
author: bluefooted
ms.author: pamela
manager: amitban
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 71e32cbe889a6c8236bf536a83109b37e6845842
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833005"
---
# <a name="sysdmdbpageinfo-transact-sql"></a>sys.dm_db_page_info (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Retourne des informations sur une page dans une base de données.  La fonction retourne une ligne qui contient les informations d’en-tête à partir de la page, y compris le `object_id`, `index_id`, et `partition_id`.  Cette fonction rend superflue l’utilisation de `DBCC PAGE` dans la plupart des cas.

## <a name="syntax"></a>Syntaxe   
```  
sys.dm_db_page_info ( DatabaseId, FileId, PageId, Mode )  
``` 

## <a name="arguments"></a>Arguments  
*DatabaseId* | NULL | PAR DÉFAUT     
Est l’ID de la base de données. *DatabaseId* est **smallint**. Une entrée valide est le numéro d’ID d’une base de données. La valeur par défaut est NULL, toutefois envoyer qu'une valeur NULL pour ce paramètre entraîne une erreur.
 
*FileId* | NULL | DEFAULT   
Identificateur du fichier. *FileId* est **int**.  Une entrée valide est le numéro d’ID d’un fichier dans la base de données spécifiée par *DatabaseId*. La valeur par défaut est NULL, toutefois envoyer qu'une valeur NULL pour ce paramètre entraîne une erreur.

*PageId* | NULL | DEFAULT   
Est l’ID de la page.  *PageId* est **int**.  Une entrée valide est le numéro d’ID d’une page dans le fichier spécifié par *FileId*. La valeur par défaut est NULL, toutefois envoyer qu'une valeur NULL pour ce paramètre entraîne une erreur.

*mode* | NULL | PAR DÉFAUT   
Détermine le niveau de détail dans la sortie de la fonction. « LIMITÉ » retourne des valeurs NULL pour toutes les colonnes de description, « Détaillé » remplir les colonnes de description.  Valeur par défaut est « Limité ».

## <a name="table-returned"></a>Table retournée  

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|database_id |int |ID de la base de données |
|file_id |int |ID de fichier |
|page_id |int |ID de page |
|page_type |int |Type de page |
|page_type_desc |nvarchar(64) |Description du type de page |
|page_flag_bits |nvarchar(64) |Bits d’indicateur dans l’en-tête de page |
|page_flag_bits_desc |nvarchar (256) |Description du service bits indicateur dans l’en-tête de page |
|page_type_flag_bits |nvarchar(64) |Bits d’indicateur de type dans l’en-tête de page |
|page_type_flag_bits_desc |nvarchar(64) |Description du service bits indicateur type dans l’en-tête de page |
|object_id |int |ID de l’objet propriétaire de la page |
|index_id |int |ID de l’index (0 pour les pages de données de segment de mémoire) |
|partition_id |bigint |ID de la partition |
|alloc_unit_id |bigint |ID de l’unité d’allocation |
|page_level |int |Niveau de la page dans l’index (feuille = 0) |
|slot_count |smallint |Nombre total d’emplacements (utilisé et non utilisé) <br> Pour une page de données, ce nombre est équivalent au nombre de lignes. |
|ghost_rec_count |smallint |Nombre d’enregistrements marqués en tant que fantôme sur la page <br> Un enregistrement fantôme est celui qui a été marqué pour suppression mais n’a pas encore être supprimé. |
|torn_bits |int |bit 1 par secteur pour la détection des erreurs d’écriture. Également utilisé pour stocker la somme de contrôle <br> Cette valeur est utilisée pour détecter une altération des données |
|is_iam_pg |bit |Bits pour indiquer si la page est une page IAM  |
|is_mixed_ext |bit |Bit pour indiquer si alloué dans une extension mixte |
|pfs_file_id |smallint |ID de fichier de page PFS correspondante |
|pfs_page_id |int |ID de page de la page PFS correspondante |
|pfs_alloc_percent |int |Comme indiqué par l’octet PFS pour cent d’allocation |
|pfs_status |nvarchar(64) |Octet PFS |
|pfs_status_desc |nvarchar(64) |Description de l’octet PFS |
|gam_file_id |smallint |ID de fichier de la page GAM correspondante |
|gam_page_id |int |ID de page de la page GAM correspondante |
|gam_status |bit |Bit pour indiquer si allouée dans GAM |
|gam_status_desc |nvarchar(64) |Description de l’état le bit GAM |
|sgam_file_id |smallint |ID de fichier de la page SGAM correspondante |
|sgam_page_id |int |ID de page de la page SGAM correspondante |
|sgam_status |bit |Bit pour indiquer si allouée dans SGAM |
|sgam_status_desc |nvarchar(64) |Description du bit SGAM état |
|diff_map_file_id |smallint |ID de fichier de la page correspondante de la bitmap différentielle |
|diff_map_page_id |int |ID de page de la page correspondante de la bitmap différentielle |
|diff_status |bit |Bits pour indiquer si l’état de la comparaison est modifiée |
|diff_status_desc |nvarchar(64) |Description du bit état diff |
|ml_file_id |smallint |ID de fichier de la page de bitmap d’une journalisation minimale correspondante |
|ml_page_id |int |ID de page de la page de bitmap d’une journalisation minimale correspondante |
|ml_status |bit |Bits pour indiquer si la page est minimale |
|ml_status_desc |nvarchar(64) |Description de l’état de la journalisation minimale de bits |
|free_bytes |smallint |Nombre d’octets libres sur la page |
|free_data_offset |int |Décalage d’espace libre à la fin de la zone de données |
|reserved_bytes |smallint |Nombre d’octets libres réservées par toutes les transactions (si tas) <br> Nombre de lignes fantômes (si la feuille de l’index) |
|reserved_xdes_id |smallint |Espace fourni par m_xdesID à m_reservedCnt <br> Uniquement à des fins de débogage |
|xdes_id |nvarchar(64) |Transaction la plus récente par le m_reserved <br> Uniquement à des fins de débogage |
|prev_page_file_id |smallint |ID de fichier de page précédente |
|prev_page_page_id |int |ID de page de page précédente |
|next_page_file_id |smallint |ID de fichier de page suivante |
|next_page_page_id |int |ID de page de page suivante |
|LONG_MIN du fichier répertoire |smallint |Longueur de lignes de taille fixe |
|lsn |nvarchar(64) |Numéro de séquence de journal / horodatage |
|header_version |int |Version d’en-tête de page |

## <a name="remarks"></a>Notes
Le `sys.dm_db_page_info` fonction de gestion dynamique retourne des informations de page comme `page_id`, `file_id`, `index_id`, `object_id` etc. qui sont présents dans un en-tête de page. Ces informations sont utiles pour le dépannage et débogage des différents problèmes de performances (contention de verrous et) et une altération.

`sys.dm_db_page_info` peut être utilisé à la place de la `DBCC PAGE` instruction dans nombreux cas, mais il retourne uniquement les page informations d’en-tête, pas le corps de la page. `DBCC PAGE` seront toujours utiles pour les cas d’usage où tout le contenu de la page est requis.

## <a name="using-in-conjunction-with-other-dmvs"></a>À utiliser avec d’autres vues de gestion dynamique
Un des cas d’usage importants de `sys.dm_db_page_info` consiste à joindre avec d’autres vues de gestion dynamique qui exposent des informations sur la page.  Pour faciliter ce cas d’utilisation, une nouvelle colonne appelée `page_resource` a été ajoutée qui expose des informations de page dans un format hexadécimal de 8 octets. Cette colonne a été ajoutée à `sys.dm_exec_requests` et `sys.sysprocesses` et seront ajoutés à d’autres vues de gestion dynamique à l’avenir en fonction des besoins.

Une nouvelle fonction, `sys.fn_PageResCracker`, prend la `page_resource` comme entrée et génère une seule ligne qui contienne `database_id`, `file_id` et `page_id`.  Cette fonction peut ensuite être utilisée pour faciliter les jointures entre `sys.dm_exec_requests` ou `sys.sysprocesses` et `sys.dm_db_page_info`.

## <a name="permissions"></a>Autorisations  
Nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-displaying-all-the-properties-of-a-page"></a>R. Affichage de toutes les propriétés d’une page
La requête suivante retourne une ligne avec toutes les informations de page pour une donnée `database_id`, `file_id`, `page_id` association avec le mode par défaut (« limité »)

```sql
SELECT *  
FROM sys.dm_db_page_info (5, 1, 15, DEFAULT)
```

### <a name="b-using-sysdmdbpageinfo-with-other-dmvs"></a>B. À l’aide de sys.dm_db_page_info avec d’autres vues de gestion dynamique 

La requête suivante renvoie une ligne par `wait_resource` exposées par `sys.dm_exec_requests` lorsque la ligne contient une valeur non null `page_resource`

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 'LIMITED') AS page_info
```

## <a name="see-also"></a>Voir aussi  
[Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)     
[sys.fn_PageResCracker](../../relational-databases/system-functions/sys-fn-pagerescracker-transact-sql.md)


