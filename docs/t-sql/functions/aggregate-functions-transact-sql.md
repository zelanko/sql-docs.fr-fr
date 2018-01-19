---
title: "Fonctions d’agrégation (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/16/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 74cc3903f4d5e10718c2d4488e4c3b8da4448b80
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="aggregate-functions-transact-sql"></a>Fonctions d'agrégation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Les fonctions d'agrégation effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique. À l'exception de COUNT, les fonctions d'agrégation ignorent les valeurs NULL. Les fonctions d'agrégation sont souvent utilisées avec la clause GROUP BY de l'instruction SELECT.
  
Toutes les fonctions d'agrégation sont déterministes. Les fonctions sont déterministes lorsqu’elles retournent toujours le même résultat à chaque fois qu’elles sont appelées en utilisant un ensemble de valeurs d’entrée spécifique. Pour plus d’informations sur le déterminisme des fonctions, consultez [fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). Le [la clause OVER](../../t-sql/queries/select-over-clause-transact-sql.md) peut suivre toutes les fonctions d’agrégation sauf GROUPING et GROUPING_ID.
  
Les fonctions d'agrégation peuvent être utilisées comme expressions uniquement dans les cas suivants :
-   la liste de sélection d'une instruction SELECT (une sous-requête ou une requête externe) ;  
-   une clause HAVING.  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] fournit les fonctions d'agrégation suivantes :
  
|||  
|-|-|  
|[AVG](../../t-sql/functions/avg-transact-sql.md)|[MIN](../../t-sql/functions/min-transact-sql.md)|  
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[SUM](../../t-sql/functions/sum-transact-sql.md)|  
|[COUNT](../../t-sql/functions/count-transact-sql.md)|[STDEV](../../t-sql/functions/stdev-transact-sql.md)|  
|[COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|  
|[GROUPING](../../t-sql/functions/grouping-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|  
|[GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|  
|[MAX](../../t-sql/functions/max-transact-sql.md)|[VARP](../../t-sql/functions/varp-transact-sql.md)|  
  
## <a name="see-also"></a>Voir aussi
[Fonctions intégrées &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)  
[OVER Clause &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
