---
title: DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/16/2017
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
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 461ee87f41692172b31125e36553c0eab0b09772
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Affiche la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] plan d’exécution pour une requête en cours d’exécution sur un spécifique [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nœud de contrôle ou un nœud de calcul. Cela permet de résoudre les problèmes de performances de requête pendant l’exécutant de requêtes sur les nœuds de calcul et le nœud de contrôle.
  
Une fois les problèmes de performances de requête sont compris de SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requêtes s’exécutant sur les nœuds de calcul, il existe plusieurs façons d’améliorer les performances. Méthodes possibles pour améliorer les performances des requêtes sur les nœuds de calcul incluent la création des statistiques de colonnes multiples, création d’index non cluster ou à l’aide des indicateurs de requête.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
Syntaxe pour SQL Server :

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Syntaxe Azure Parallel Data Warehouse :
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *distribution_id*  
 Identificateur de la distribution qui est en cours d’exécution du plan de requête. Ceci est un entier et ne peut pas être NULL. Utilisé lorsque vous ciblez [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 *pdw_node_id*  
 Identificateur du nœud qui exécute le plan de requête. Ceci est un entier et ne peut pas être NULL. Utilisé lorsque vous ciblez un appareil.  
  
 *SPID*  
 Identificateur de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session qui est en cours d’exécution du plan de requête. Ceci est un entier et ne peut pas être NULL.  
  
## <a name="permissions"></a>Permissions  
 Requiert l’autorisation CONTROL sur [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
Requiert l’autorisation de serveur-état d’affichage sur l’appareil.
  
## <a name="examples-includesssdwincludessssdw-mdmd"></a>Exemples :[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdwshowexecutionplan-basic-syntax"></a>A. Syntaxe de base DBCC PDW_SHOWEXECUTIONPLAN  
 Lors de l’exécution un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] d’une instance, modifiez la requête ci-dessus pour sélectionner le distribution_id.  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
Cette méthode retourne le spid pour la distribution chaque activement en cours d’exécution. Si vous étiez obtenir des informations concernant la distribution 1 était exécuté dans la session 375, vous exécutez la commande suivante.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-includesspdwincludessspdw-mdmd"></a>Exemples :[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdwshowexecutionplan-basic-syntax"></a>B. Syntaxe de base DBCC PDW_SHOWEXECUTIONPLAN  
 La requête est trop longue est soit en cours d’exécution un DMS interroger l’opération de plan ou d’une opération de plan de requête SQL.  
  
Si la requête s’exécute une opération de plan de requête DMS, vous pouvez utiliser la requête suivante pour récupérer une liste des ID de nœud et les ID de session pour obtenir des instructions qui ne sont pas terminées.
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
Selon les résultats de la requête précédente, utilisez le sql_spid et pdw_node_id en tant que paramètres à DBCC PDW_SHOWEXEUCTIONPLAN. Par exemple, la commande suivante affiche le plan d’exécution pour pdw_node_id 201001 et sql_spid 375.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>Voir aussi
[DBCC PDW_SHOWPARTITIONSTATS &#40; Transact-SQL &#41;](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40; Transact-SQL &#41;](dbcc-pdw-showspaceused-transact-sql.md)
