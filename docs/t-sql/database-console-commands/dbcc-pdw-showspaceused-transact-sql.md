---
title: DBCC PDW_SHOWSPACEUSED (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a16d4a7a10eb4f36d0ead2a19f8e37d251e417f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-pdwshowspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Affiche le nombre de lignes, espace disque réservé et espace disque utilisé pour une table spécifique ou pour toutes les tables dans un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] base de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Show the space used for all user tables and system tables in the current database  
DBCC PDW_SHOWSPACEUSED  
[;]  
  
-- Show the space used for a table  
DBCC PDW_SHOWSPACEUSED ( " [ database_name . [ schema_name ] . ] | [ schema_name .] table_name  " )  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 [ *nom_base_de_données* . [ *schema_name* ]. | *schema_name* . ] *nom_table*  
 L’une, de deux ou de nom en trois parties de la table à afficher. Pour deux ou les noms de table en trois parties, le nom doivent être mis entre guillemets doubles ( » »). L’utilisation des guillemets autour d’un nom de table d’une partie est facultative. Lorsque aucun nom de table n’est spécifié, les informations s’affichent pour la base de données actuelle.  
  
## <a name="permissions"></a>Permissions  
Requiert l'autorisation VIEW SERVER STATE.
  
## <a name="result-sets"></a>Jeux de résultats  
Il s’agit du jeu de résultats pour toutes les tables.
  
|Colonne|Type de données| Description|  
|------------|---------------|-----------------|  
|reserved_space|bigint|Espace total utilisé pour la base de données, en Ko.|  
|data_space|bigint|Espace utilisé pour les données, en Ko.|  
|index_space|bigint|Espace utilisé pour les index, en Ko.|  
|unused_space|bigint|Espace dans le cadre de l’espace réservé et non utilisé, en Ko.|  
|pdw_node_id|int|Nœud de calcul qui est utilisé pour les données.|  
  
Il s’agit du jeu de résultats pour une table.
  
|Colonne|Type de données| Description|Plage|  
|------------|---------------|-----------------|-----------|  
|lignes|bigint|Nombre de lignes.||  
|reserved_space|bigint|Espace total réservé pour l’objet, en Ko.||  
|data_space|bigint|Espace utilisé pour les données, en Ko.||  
|index_space|bigint|Espace utilisé pour les index, en Ko.||  
|unused_space|bigint|Espace dans le cadre de l’espace réservé et non utilisé, en Ko.||  
|pdw_node_id|int|Nœud de calcul qui est utilisé pour l’utilisation de l’espace de création de rapports.||  
|distribution_id|int|Distribution qui est utilisée pour l’utilisation de l’espace de création de rapports.|La valeur est -1 pour les tables répliquées.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowspaceused-basic-syntax"></a>A. Syntaxe de base DBCC PDW_SHOWSPACEUSED  
Les exemples suivants indiquent plusieurs façons d’afficher le nombre de lignes, l’espace réservé du disque et l’espace disque utilisé par la table FactInternetSales dans le [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] base de données.
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>B. Afficher l’espace disque utilisé par toutes les tables dans la base de données en cours  
 L’exemple suivant montre l’espace disque réservé et utilisé par toutes les tables utilisateur et système dans le [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] base de données.  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>Voir aussi
[DBCC PDW_SHOWEXECUTIONPLAN &#40; Transact-SQL &#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS &#40; Transact-SQL &#41;](dbcc-pdw-showpartitionstats-transact-sql.md)

  

