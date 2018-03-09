---
title: Sys.dm_db_log_info (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: 
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: 661647715d2fcff3a4821250dfaa65e0fea07d6e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="sysdmdbloginfo-transact-sql"></a>Sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne [le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) les informations du journal des transactions. Notez que tous les fichiers journaux des transactions sont combinés dans la sortie de la table. Chaque ligne dans la sortie représente un fichier journal virtuel dans le journal des transactions et fournit des informations relatives à ce fichier journal virtuel dans le journal.

## <a name="syntax"></a>Syntaxe  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>Arguments  
 *database_id* | NULL | PAR DÉFAUT  
 Est l’ID de la base de données. *database_id* est **int**. Les entrées valides sont l’ID de base de données, NULL ou par défaut. La valeur par défaut est NULL. NULL et par défaut sont des valeurs équivalentes dans le contexte de base de données actuelle.
 
 Spécifiez NULL pour retourner des informations de fichier journal virtuel de la base de données actuelle.

 La fonction intégrée [DB_ID](../../t-sql/functions/db-id-transact-sql.md) peut être spécifié. Lorsque vous utilisez `DB_ID` sans spécifier un nom de base de données, le niveau de compatibilité de la base de données en cours doit être supérieur ou égal à 90.  

## <a name="table-returned"></a>Table retournée  

|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|database_id|**Int**|ID de la base de données.|
|file_id|**smallint**|Id de fichier du journal des transactions.|  
|vlf_begin_offset|**bigint** |Offset de l’emplacement de la [le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) à partir du début du fichier journal des transactions.|
|vlf_size_mb |**float** |[le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) taille en Mo, arrondi à 2 décimales.|     
|vlf_sequence_number|**bigint** |[le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) numéro dans l’ordre créé. Utilisé pour identifier les fichiers journaux virtuels dans le fichier journal.|
|vlf_active|**bit** |Indique si [le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) est en cours d’utilisation ou non. <br />0 - fichier journal virtuel n’est pas en cours d’utilisation.<br />1 - fichier journal virtuel est actif.|
|vlf_status|**Int** |État de la [le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Les valeurs possibles sont <br />0 - fichier journal virtuel est inactif <br />1 - fichier journal virtuel est initialisé, mais inutilisé <br /> 2 - fichier journal virtuel est actif.|
|vlf_parity|**tinyint** |Parité de [le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Utilisé en interne pour déterminer la fin du journal dans un fichier journal virtuel.|
|vlf_first_lsn|**nvarchar(48)** |[Numéro de séquence journal (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) du premier enregistrement de journal dans le [le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_create_lsn|**nvarchar(48)** |[Numéro de séquence journal (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) du journal enregistrement créé le [le fichier journal virtuel (fichier journal virtuel)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|

## <a name="remarks"></a>Notes 
 Le `sys.dm_db_log_info` fonction de gestion dynamique remplace la `DBCC LOGINFO` instruction. 
 
## <a name="permissions"></a>Autorisations  
 Nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Définir bases de données dans une instance de SQL Server avec un grand nombre de fichiers journaux virtuels
La requête suivante détermine les bases de données avec plus de 100 fichiers journaux virtuels dans les fichiers journaux, ce qui peuvent affecter le temps de démarrage, de restauration et de récupération de base de données.

```sql
SELECT [name], COUNT(l.database_id) AS 'vlf_count' 
FROM sys.databases s
CROSS APPLY sys.dm_db_log_info(s.database_id) l
GROUP BY [name]
HAVING COUNT(l.database_id) > 100
```

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. Détermination de l’état de la dernière `VLF` dans le journal des transactions avant la réduction du fichier journal

La requête suivante peut être utilisée pour déterminer l’état du dernier fichier journal virtuel avant d’exécuter shrinkfile sur le journal des transactions pour déterminer si le journal des transactions peut réduire.

```sql
USE AdventureWorks2016
GO

SELECT TOP 1 DB_NAME(database_id) AS "Database Name", file_id, vlf_size_mb, vlf_sequence_number, vlf_active, vlf_status
FROM sys.dm_db_log_info(DEFAULT)
ORDER BY vlf_sequence_number DESC
```


## <a name="see-also"></a>Voir aussi  
[Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[Sys.dm_db_log_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

