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
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: "4"
author: savjani
ms.author: pariks
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: b7250943f4e92d60888a75d9e577388f3cc6b1ed
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbloginfo-transact-sql"></a>Sys.dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne `VLF` informations des fichiers journaux des transactions. (Tous les fichiers journaux sont combinés dans la sortie de la table). Chaque ligne dans la sortie représente un `VLF` dans le journal des transactions et fournit des informations relatives à ce fichier journal virtuel dans le journal.

## <a name="syntax"></a>Syntaxe  
  
```  
sys.dm_db_log_info ( database_id )  
```  
## <a name="arguments"></a>Arguments  
 *database_id* | NULL | PAR DÉFAUT  
 Est l’ID de la base de données. *database_id* est **int**. Les entrées valides sont l’ID de base de données, NULL ou par défaut. La valeur par défaut est NULL. NULL et par défaut sont des valeurs équivalentes dans le contexte de base de données actuelle.
 
 Spécifiez la valeur NULL pour retourner `VLF` plus d’informations de la base de données actuelle.

 La fonction intégrée [DB_ID](../../t-sql/functions/db-id-transact-sql.md) peut être spécifié. Si vous utilisez DB_ID sans spécifier de nom de base de données, le niveau de compatibilité de la base de données active doit être égal à 90 ou plus.  

## <a name="table-returned"></a>Table retournée  

|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID de la base de données.|
|file_id|**smallint**|Id de fichier du journal des transactions.|  
|vlf_begin_offset|**bigint** |Offset de l’emplacement de la `VLF` à partir du début du fichier journal des transactions.|
|vlf_size_mb |**float** |`VLF`taille en Mo, arrondi à 2 décimales.|     
|vlf_sequence_number|**bigint** |`VLF`numéro de séquence dans l’ordre créé. Utilisé pour identifier de manière unique `VLFs` dans le fichier journal.|
|vlf_active|**bit** |Indique si le fichier journal virtuel est en cours d’utilisation ou non. <br />0 - fichier journal virtuel n’est pas en cours d’utilisation.<br />1 - `VLF` est actif.|
|vlf_status|**int** |État de la `VLF`. Les valeurs possibles sont <br />0 - `VLF` est inactif <br />1 - fichier journal virtuel est initialisé, mais inutilisé <br /> 2 - `VLF` est actif.|
|vlf_parity|**tinyint** |Parité de `VLF`. Utilisé en interne pour déterminer la fin du journal dans un `VLF`.|
|vlf_first_lsn|**nvarchar(48)** |NSE du premier enregistrement de journal dans le `VLF`.|
|vlf_create_lsn|**nvarchar(48)** |LSN du journal enregistrement qui a créé le `VLF`.|

## <a name="remarks"></a>Notes
 Le `sys.dm_db_log_info` fonction de gestion dynamique remplace la `DBCC LOGINFO` instruction. 
 
## <a name="permissions"></a>Permissions  
 Nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Définir bases de données dans une instance de SQL Server avec un nombre élevé de`VLFs`
La requête suivante détermine les bases de données avec plus de 100 `VLFs` dans les fichiers journaux, ce qui peut affecter le temps de démarrage, de restauration et de récupération de base de données.

```sql
SELECT name,count(l.database_id) as 'vlf_count' from sys.databases s
cross apply sys.dm_db_log_info(s.database_id) l
group by name
having count(l.database_id)> 100
```

### <a name="b-determing-the-status-of-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. Détermination de l’état de la dernière `VLF` dans le journal des transactions avant la réduction du fichier journal

La requête suivante peut être utilisée pour déterminer l’état de la dernière `VLF` avant d’exécuter shrinkfile sur le journal des transactions pour déterminer si le journal des transactions peut réduire.

```sql
USE <database name>
GO

SELECT top 1 DB_NAME(database_id) as "Database Name",file_id,vlf_size_mb,vlf_sequence_number, vlf_active, vlf_status
from sys.dm_db_log_info(DEFAULT)
order by vlf_sequence_number desc
```


## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_log_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)    
  



