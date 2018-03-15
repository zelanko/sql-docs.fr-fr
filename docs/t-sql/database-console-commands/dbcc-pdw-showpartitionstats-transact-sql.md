---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/17/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|database-console-commands
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa9c4e335fddbe4851562f4aada8d55011d99b98
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Affiche la taille et le nombre de lignes pour chaque partition d’une table dans une base de données [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 [ *database_name* . [ *schema_name* ] . | *schema_name* . ] *table_name*  
 Nom en une, deux ou trois parties de la table à afficher.  Les noms de table en deux ou trois parties doivent être placés entre guillemets doubles (""). L’utilisation de guillemets autour d’un nom de table en une partie est facultative.  
  
## <a name="permissions"></a>Autorisations
Nécessite l’autorisation **VIEW SERVER STATE**.
  
## <a name="result-sets"></a>Jeux de résultats  
Voici les résultats de la commande DBCC PDW_SHOWPARTITIONSTATS.
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|partition_number|INT|Numéro de partition.|  
|used_page_count|BIGINT|Nombre de pages utilisées pour les données.|  
|reserved_page_count|BIGINT|Nombre de pages allouées à la partition.|  
|row_count|BIGINT|Nombre de lignes dans la partition.|  
|pdw_node_id|INT|Nœud de calcul pour les données.|  
|distribution_id|INT|ID de distribution pour les données.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. Exemples de syntaxe de base DBCC PDW_SHOWPARTITIONSTATS  
Les exemples suivants affichent l’espace utilisé et le nombre de lignes par partition pour la table FactInternetSales dans la base de données [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>Voir aussi
[DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)  
  
