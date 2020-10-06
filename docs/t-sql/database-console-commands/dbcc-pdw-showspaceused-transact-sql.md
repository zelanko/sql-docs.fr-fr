---
description: DBCC PDW_SHOWSPACEUSED (Transact-SQL)
title: DBCC PDW_SHOWSPACEUSED (Transact-SQL)
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8c7ca98b19a801daa73367ee50df525ab43d1406
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722056"
---
# <a name="dbcc-pdw_showspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (Transact-SQL)

[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

Affiche le nombre de lignes, l’espace disque réservé et l’espace disque utilisé pour une table spécifique ou pour toutes les tables dans une base de données [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe
  
```syntaxsql
-- Show the space used for all user tables and system tables in the current database  
DBCC PDW_SHOWSPACEUSED  
[;]  
  
-- Show the space used for a table  
DBCC PDW_SHOWSPACEUSED ( " [ database_name . [ schema_name ] . ] | [ schema_name .] table_name  " )  
[;]  
```  

[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]

## <a name="arguments"></a>Arguments

 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
Nom en une, deux ou trois parties de la table à afficher. Les noms de table en deux ou trois parties doivent être placés entre guillemets doubles (""). L’utilisation de guillemets autour d’un nom de table en une partie est facultative. Quand aucun nom de table n’est spécifié, les informations s’affichent pour la base de données actuelle.  
  
## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW SERVER STATE.
  
## <a name="result-sets"></a>Jeux de résultats

Voici le jeu de résultats pour toutes les tables.  Avant de créer un cache pour une table Synapse répliquée, le résultat DBCC reflète la taille totale de la table de tourniquet (round robin) sous-jacente à partir de chaque distribution.  Une fois le cache créé, le résultat reflète la taille totale des tables de tourniquet (round robin) et du cache.   
  
|Colonne|Type de données|Description|  
|------------|---------------|-----------------|  
|reserved_space|bigint|Espace total utilisé pour la base de données, en Ko.|  
|data_space|bigint|Espace utilisé pour les données, en Ko.|  
|index_space|bigint|Espace utilisé pour les index, en Ko.|  
|unused_space|bigint|Espace qui fait partie de l’espace réservé et non utilisé, en Ko.|  
|pdw_node_id|int|Nœud de calcul qui est utilisé pour les données.|  
  
Voici le jeu de résultats pour une table.
  
|Colonne|Type de données|Description|Plage|  
|------------|---------------|-----------------|-----------|  
|rows|bigint|Nombre de lignes.||  
|reserved_space|bigint|Espace total réservé pour l’objet, en Ko.||  
|data_space|bigint|Espace utilisé pour les données, en Ko.||  
|index_space|bigint|Espace utilisé pour les index, en Ko.||  
|unused_space|bigint|Espace qui fait partie de l’espace réservé et non utilisé, en Ko.||  
|pdw_node_id|int|Nœud de calcul qui est utilisé pour signaler l’utilisation de l’espace.||  
|distribution_id|int|Distribution qui est utilisée pour signaler l’utilisation de l’espace.|Pour Parallel Data Warehouse, sa valeur est -1 pour les tables répliquées.|  
  
## <a name="examples-sssdw-and-sspdw"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdw_showspaceused-basic-syntax"></a>R. Syntaxe de base DBCC PDW_SHOWSPACEUSED  
Les exemples suivants indiquent plusieurs façons d’afficher le nombre de lignes, l’espace disque réservé et l’espace disque utilisé par la table FactInternetSales dans la base de données [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>B. Afficher l’espace disque utilisé par toutes les tables dans la base de données actuelle  

 L’exemple suivant montre l’espace disque réservé et utilisé par toutes les tables utilisateur et système dans la base de données [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  

## <a name="see-also"></a>Voir aussi

- [DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
- [DBCC PDW_SHOWPARTITIONSTATS &#40;Transact-SQL&#41;](dbcc-pdw-showpartitionstats-transact-sql.md)
