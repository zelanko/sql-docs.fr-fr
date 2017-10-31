---
title: "Fonctions d’agrégation (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a97d68c641d2a3deb1d3fd3a674f65cafc3854c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="aggregate-functions-transact-sql"></a>Fonctions d'agrégation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Les fonctions d'agrégation effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique. À l'exception de COUNT, les fonctions d'agrégation ignorent les valeurs NULL. Les fonctions d'agrégation sont souvent utilisées avec la clause GROUP BY de l'instruction SELECT.
  
Toutes les fonctions d'agrégation sont déterministes. Les fonctions sont déterministes lorsqu’elles retournent toujours le même résultat à chaque fois qu’elles sont appelées en utilisant un ensemble de valeurs d’entrée spécifique. Pour plus d’informations sur le déterminisme des fonctions, consultez [fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). Le [la clause OVER](../../t-sql/queries/select-over-clause-transact-sql.md) peut suivre toutes les fonctions d’agrégation sauf GROUPING et GROUPING_ID.
  
Les fonctions d'agrégation peuvent être utilisées comme expressions uniquement dans les cas suivants :
-   la liste de sélection d'une instruction SELECT (une sous-requête ou une requête externe) ;  
-   une clause HAVING.  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] fournit les fonctions d'agrégation suivantes :
  
|||  
|-|-|  
|[AVG](../../t-sql/functions/avg-transact-sql.md)|[MIN](../../t-sql/functions/min-transact-sql.md)|  
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[SOMME](../../t-sql/functions/sum-transact-sql.md)|  
|[NOMBRE](../../t-sql/functions/count-transact-sql.md)|[FONCTION STDEV](../../t-sql/functions/stdev-transact-sql.md)|  
|[COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|  
|[REGROUPEMENT](../../t-sql/functions/grouping-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|  
|[GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[VARP](../../t-sql/functions/varp-transact-sql.md)|  
|[MAX](../../t-sql/functions/max-transact-sql.md)||  
  
## <a name="see-also"></a>Voir aussi
[Fonctions intégrées &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)  
[SUR la clause for &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  

