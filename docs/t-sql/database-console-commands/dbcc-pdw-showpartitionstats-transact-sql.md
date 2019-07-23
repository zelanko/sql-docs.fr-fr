---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: ac6d3ac9128c8f27a898f4b903f74d1e9ab9bb1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116497"
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Affiche la taille et le nombre de lignes pour chaque partition d’une table dans une base de données [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Icône de lien d’article](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien de rubrique") [Conventions syntaxiques Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
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
|partition_number|INT|Numéro de partition.|  
|used_page_count|BIGINT|Nombre de pages utilisées pour les données.|  
|reserved_page_count|BIGINT|Nombre de pages réservées pour la partition.|  
|row_count|BIGINT|Nombre de lignes dans la partition.|  
|pdw_node_id|INT|Nœud de calcul pour les données.|  
|distribution_id|INT|Identificateur de distribution des données.|  
  
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
 
