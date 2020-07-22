---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6d1a1a72fbe5ef1b8382901a62adfd95a907b765
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86484260"
---
# <a name="dbcc-pdw_showpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)

[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

Affiche la taille et le nombre de lignes pour chaque partition d’une table dans une base de données [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Icône du lien de l’article](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien d’article") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  

## <a name="arguments"></a>Arguments  
 `[ database_name . [ schema_name ] . | schema_name . ] table_name`  
 Nom en une, deux ou trois parties de la table à afficher.  Les noms de table en deux ou trois parties doivent être placés entre guillemets doubles (""). L’utilisation de guillemets autour d’un nom de table en une partie est facultative.  
  
## <a name="permissions"></a>Autorisations
Nécessite l’autorisation **VIEW SERVER STATE**.
  
## <a name="result-sets"></a>Jeux de résultats  
Voici les résultats de la commande DBCC PDW_SHOWPARTITIONSTATS.
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|partition_number|int|Numéro de partition.|  
|used_page_count|bigint|Nombre de pages utilisées pour les données.|  
|reserved_page_count|bigint|Nombre de pages réservées pour la partition.|  
|row_count|bigint|Nombre de lignes dans la partition.|  
|pdw_node_id|int|Nœud de calcul pour les données.|  
|distribution_id|int|Identificateur de distribution des données.|  
  
## <a name="examples-sssdw-and-sspdw"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdw_showpartitionstats-basic-syntax-examples"></a>R. Exemples de syntaxe de base DBCC PDW_SHOWPARTITIONSTATS  
Les exemples suivants affichent l’espace utilisé et le nombre de lignes par partition pour la table FactInternetSales dans la base de données [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  

## <a name="see-also"></a>Voir aussi

- [DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
- [DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)  