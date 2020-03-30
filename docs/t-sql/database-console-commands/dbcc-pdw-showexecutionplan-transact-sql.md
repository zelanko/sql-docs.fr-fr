---
title: DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.technology: data-warehouse
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7fd267efe05da089cf72b1b9d1e4a04e6c18b83b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68809839"
---
# <a name="dbcc-pdw_showexecutionplan-transact-sql"></a>DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Affiche le plan d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour une requête exécutée sur un nœud de contrôle ou un nœud de calcul [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] spécifique. Cela permet de résoudre les problèmes de performances des requêtes pendant leur exécution sur les nœuds de calcul et le nœud de contrôle.
  
Une fois les problèmes de performances des requêtes compris pour les requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMP exécutées sur les nœuds de calcul, il existe plusieurs façons d’améliorer les performances. Les méthodes possibles pour améliorer les performances des requêtes sur les nœuds de calcul incluent la création de statistiques multicolonnes, la création d’index non-cluster et l’utilisation d’indicateurs de requête.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
Syntaxe pour Azure SQL Data Warehouse :

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Syntaxe Azure Parallel Data Warehouse :
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *distribution_id*  
 Identificateur de la distribution qui exécute le plan de requête. Il s’agit d’un entier différent de Null. Utilisé quand la cible est [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 *pdw_node_id*  
 Identificateur du nœud qui exécute le plan de requête. Il s’agit d’un entier différent de Null. Utilisé quand la cible est une appliance.  
  
 *spid*  
 Identificateur de la session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécute le plan de requête. Il s’agit d’un entier différent de Null.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation CONTROL sur [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
Nécessite l’autorisation VIEW-SERVER-STATE sur l’appliance.
  
## <a name="examples-sssdw"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdw_showexecutionplan-basic-syntax"></a>R. Syntaxe de base DBCC PDW_SHOWEXECUTIONPLAN  
 Lors de l’exécution sur une instance de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], modifiez la requête ci-dessus pour sélectionner aussi l’argument distribution_id.  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
Vous retournez ainsi l’identificateur spid pour chaque distribution activement exécutée. Si vous aviez la curiosité de savoir ce que la distribution 1 exécutait dans la session 375, vous exécuteriez la commande suivante.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-sspdw"></a>Exemples : [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdw_showexecutionplan-basic-syntax"></a>B. Syntaxe de base DBCC PDW_SHOWEXECUTIONPLAN  
 La requête dont l’exécution est trop longue exécute une opération de plan de requête DMS ou SQL.  
  
Si la requête exécute une opération de plan de requête DMS, vous pouvez utiliser la requête suivante pour récupérer une liste des ID de nœud et ID de session pour les étapes qui ne sont pas terminées.
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
D’après les résultats de la requête précédente, il est recommandé d’utiliser sql_spid et pdw_node_id comme paramètres pour DBCC PDW_SHOWEXECUTIONPLAN. Par exemple, la commande suivante indique le plan d’exécution pour pdw_node_id 201001 et sql_spid 375.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>Voir aussi
[DBCC PDW_SHOWPARTITIONSTATS &#40;Transact-SQL&#41;](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)
