---
title: COUNT_BIG (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT_BIG_TSQL
- COUNT_BIG
dev_langs: TSQL
helpviewer_keywords:
- totals [SQL Server], COUNT_BIG function
- counting items in group
- groups [SQL Server], number of items in
- number of group items
- COUNT_BIG function
ms.assetid: f2e3601f-487e-4917-bb01-47b1047908cd
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b0165fefcc715becfb9c59644ed0ddd96cca9c07
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="countbig-transact-sql"></a>COUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne le nombre d'éléments figurant dans un groupe. COUNT_BIG est similaire à la fonction COUNT. Elles diffèrent uniquement au niveau des valeurs renvoyées : COUNT_BIG retourne toujours un **bigint** valeur de type de données. COUNT renvoie toujours une **int** valeur de type de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Syntax for SQL Server and Azure SQL Database  
  
COUNT_BIG ( { [ ALL | DISTINCT ] expression } | * )  
   [ OVER ( [ partition_by_clause ] [ order_by_clause ] ) ]  
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Aggregation Function Syntax  
COUNT_BIG ( { [ [ ALL | DISTINCT ] expression ] | * } )  
  
-- Analytic Function Syntax  
COUNT_BIG ( { expression | * } ) OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Arguments  
ALL  
Applique la fonction d'agrégation à toutes les valeurs. ALL est l'argument par défaut.
  
DISTINCT  
Spécifie que la fonction COUNT_BIG doit renvoyer le nombre de valeurs non NULL uniques.
  
*expression*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type. Les fonctions d'agrégation et les sous-requêtes ne sont pas autorisées.
  
*\**  
Spécifie que toutes les lignes doivent être comptées pour renvoyer le nombre total de lignes de la table. COUNT_BIG (*\**) ne prend aucun paramètre et ne peut pas être utilisé avec DISTINCT. COUNT_BIG (*\**) ne nécessite pas une *expression* paramètre car, par définition, elle n’utilise pas d’informations sur une colonne particulière. COUNT_BIG (*\**) renvoie le nombre de lignes de la table spécifiée sans supprimer les doublons. Il compte chaque ligne séparément, y compris les lignes qui contiennent des valeurs NULL.
  
ALL  
Applique la fonction d'agrégation à toutes les valeurs. ALL est l'argument par défaut.
  
DISTINCT  
Spécifie que la fonction AVG doit uniquement être appliquée à chaque instance unique d'une valeur, quel que soit le nombre d'occurrences de la valeur.
  
*expression*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de la catégorie, de type de données numérique approximatives ou à l’exception de la **bits** type de données. Les fonctions d'agrégation et les sous-requêtes ne sont pas autorisées.
  
SUR **(** [ *partition_by_clause* ] [ *order_by_clause* ] **)**  
*partition_by_clause* divise le jeu de résultats généré par la clause FROM en partitions auxquelles la fonction est appliquée. S'il n'est pas spécifié, la fonction gère toutes les lignes du jeu de résultats de la requête en un seul groupe. *order_by_clause* détermine l’ordre logique dans lequel l’opération est effectuée. Pour plus d’informations, consultez [la Clause OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Types de retour
**bigint**
  
## <a name="remarks"></a>Notes  
COUNT_BIG(*) renvoie le nombre d'éléments figurant dans un groupe, y compris les valeurs NULL et les doublons.
  
COUNT_BIG (tous les *expression*) prend la valeur *expression* pour chaque ligne d’un groupe et renvoie le nombre de valeurs non null.
  
COUNT_BIG (DISTINCT *expression*) prend la valeur *expression* pour chaque ligne d’un groupe et renvoie le nombre de valeurs uniques, non nulles.
  
COUNT_BIG est une fonction déterministe lorsqu'elle est utilisée sans les clauses OVER et ORDER BY. Elle n'est pas déterministe avec les clauses OVER et ORDER BY. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Exemples  
Pour obtenir des exemples, consultez [COUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/count-transact-sql.md).
  
## <a name="see-also"></a>Voir aussi
[Fonctions d’agrégation &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[NOMBRE &#40; Transact-SQL &#41;](../../t-sql/functions/count-transact-sql.md)  
[int, bigint, smallint, tinyint et #40 ; Transact-SQL &#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
[SUR la clause for &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
