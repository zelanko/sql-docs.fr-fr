---
title: NULL et UNKNOWN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: "5"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6a581045af3d5ed73e9cf9736c60588d87733369
ms.sourcegitcommit: 7673ad0e84a6de69420e19247a59e39ca751a8aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2018
---
# <a name="null-and-unknown-transact-sql"></a>NULL et UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL indique que la valeur est inconnue. Une valeur null est différente à partir d’un valeur vide ou nulle. Deux valeurs NULL ne sont pas égales. Comparaisons entre deux valeurs null, ou entre une valeur null et toute autre valeur de retour inconnus, car la valeur de chaque NULL est inconnue.  
  
 Les valeurs NULL indiquent généralement des données inconnues, non applicable, ou être ajoutées plus tard. Le montant moyen, par exemple, ne peut pas être connu à l'instant où le client effectue une commande.  
  
 Notez les éléments suivants concernant les valeurs null :  
  
-   Pour tester des valeurs NULL dans une requête, utilisez IS NULL ou IS NOT NULL dans la clause WHERE.  
  
-   Les valeurs null peuvent être insérées dans une colonne en spécifiant explicitement NULL dans une instruction INSERT ou UPDATE, ou en laissant une colonne dans une instruction INSERT.  
  
-   Les valeurs NULL ne doit pas servir des informations requises pour distinguer plusieurs lignes dans une table à partir d’une autre ligne d’une table, telles que des clés primaires, ou pour plus d’informations permet de distribuer les lignes, telles que les clés de la distribution.  
  
 Lorsque des valeurs NULL sont présentes dans les données, les opérateurs logiques et les opérateurs de comparaison peuvent renvoyer la valeur UNKNOWN au lieu de TRUE ou de FALSE. Cette logique tri-valuée nécessaire est source de nombreuses erreurs dans les applications. Les opérateurs logiques dans une expression booléenne qui inclut des inconnues retournera inconnu à moins que le résultat de l’opérateur ne dépend pas de l’expression inconnue. Ces tableaux fournissent des exemples de ce comportement.  
  
 Le tableau suivant présente les résultats de l’application d’un opérateur AND à deux expressions booléennes où une expression retourne UNKNOWN.  
  
|Expression 1|Expression 2|Résultats|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 Le tableau suivant présente les résultats de l’application d’un opérateur OR à deux expressions booléennes où une expression retourne UNKNOWN.  
  
|Expression 1|Expression 2|Résultats|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|TRUE|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a>Voir aussi  
 [ET &#40; Transact-SQL &#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [OU &#40; Transact-SQL &#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [PAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [EST NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
