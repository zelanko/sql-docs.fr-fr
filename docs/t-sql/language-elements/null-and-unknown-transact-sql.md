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
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: 5
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bdac1899707b3caa4f4c515324511a47830f2722
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="null-and-unknown-transact-sql"></a>NULL et UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL indique que la valeur est inconnue. Une valeur null est différente à partir d’un valeur vide ou nulle. Deux valeurs NULL ne sont pas égales. Comparaisons entre deux valeurs null, ou entre une valeur null et toute autre valeur de retour inconnus, car la valeur de chaque NULL est inconnue.  
  
 Les valeurs NULL indiquent généralement des données inconnues, non applicable, ou être ajoutées plus tard. Le montant moyen, par exemple, ne peut pas être connu à l'instant où le client effectue une commande.  
  
 Notez les éléments suivants concernant les valeurs null :  
  
-   Pour tester des valeurs NULL dans une requête, utilisez IS NULL ou IS NOT NULL dans la clause WHERE.  
  
-   Les valeurs null peuvent être insérées dans une colonne en spécifiant explicitement NULL dans une instruction INSERT ou UPDATE, ou en laissant une colonne dans une instruction INSERT.  
  
-   Les valeurs NULL ne doit pas servir des informations requises pour distinguer plusieurs lignes dans une table à partir d’une autre ligne d’une table, telles que des clés primaires, ou pour plus d’informations permet de distribuer les lignes, telles que les clés de la distribution.  
  
 Lorsque des valeurs NULL sont présentes dans les données, les opérateurs logiques et les opérateurs de comparaison peuvent renvoyer la valeur UNKNOWN au lieu de TRUE ou de FALSE. Cette logique tri-valuée nécessaire est source de nombreuses erreurs dans les applications. Ces tableaux présentent les effets dus à l'introduction de valeurs NULL dans les comparaisons.  
  
 Le tableau suivant présente les résultats de l’application d’un opérateur AND à deux opérandes booléens où un opérande renvoie la valeur NULL.  
  
|Opérande 1|Opérande de 2|Résultat|  
|---------------|---------------|------------|  
|TRUE|NULL|FALSE|  
|NULL|NULL|FALSE|  
|FALSE|NULL|FALSE|  
  
 Le tableau suivant présente les résultats de l’application d’un opérateur OR à deux opérandes booléens où un opérande renvoie la valeur NULL.  
  
|Opérande 1|Opérande de 2|Résultat|  
|---------------|---------------|------------|  
|TRUE|NULL|TRUE|  
|NULL|NULL|UNKNOWN|  
|FALSE|NULL|UNKNOWN|  
  
## <a name="see-also"></a>Voir aussi  
 [ET &#40; Transact-SQL &#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [OU &#40; Transact-SQL &#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [PAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [EST NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  

