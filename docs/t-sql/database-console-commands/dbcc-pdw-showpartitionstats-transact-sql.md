---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|database-console-commands
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
caps.latest.revision: "10"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fb41140783d4c334e7ee701f44d523ec68e41435
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Affiche la taille et le nombre de lignes pour chaque partition d’une table dans un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] base de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 [ *nom_base_de_données* . [ *schema_name* ]. | *schema_name* . ] *nom_table*  
 L’une, de deux ou de nom en trois parties de la table à afficher.  Pour deux ou les noms de table en trois parties, le nom doivent être mis entre guillemets doubles ( » »). L’utilisation des guillemets autour d’un nom de table d’une partie est facultative.  
  
## <a name="permissions"></a>Permissions
Requiert **VIEW SERVER STATE** autorisation.
  
## <a name="result-sets"></a>Jeux de résultats  
Voici les résultats de la commande DBCC PDW_SHOWPARTITIONSTATS.
  
|Nom de la colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|partition_number|int|Numéro de partition.|  
|used_page_count|bigint|Nombre de pages utilisées pour les données.|  
|reserved_page_count|bigint|Nombre de pages allouées à la partition.|  
|row_count|bigint|Nombre de lignes dans la partition.|  
|pdw_node_id|int|Nœud pour les données de calcul.|  
|distribution_id|int|Id de distribution pour les données.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. Exemples de syntaxe de base DBCC PDW_SHOWPARTITIONSTATS  
Les exemples suivants affichent l’espace utilisé et le nombre de lignes par partition pour la table FactInternetSales dans le [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] base de données.
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>Voir aussi
[DBCC PDW_SHOWEXECUTIONPLAN &#40; Transact-SQL &#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40; Transact-SQL &#41;](dbcc-pdw-showspaceused-transact-sql.md)  
  
