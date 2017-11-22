---
title: '| (OR au niveau du bit) (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '|'
- '|_TSQL'
- Bitwise OR
- bitwise
- OR
dev_langs: TSQL
helpviewer_keywords:
- OR operator
- bitwise OR (|)
- '| (bitwise OR operator)'
ms.assetid: 86a3b87f-9688-4eaf-a552-29f1b01d880a
caps.latest.revision: "43"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 47d4b177e93d028ccf0afffec6a9480928e11cb0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="-bitwise-or-transact-sql"></a>| (OR au niveau du bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Exécute une opération logique OR au niveau du bit entre deux valeurs entières spécifiées, traduites en expressions binaires dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```   
expression | expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de la catégorie de type de données entier, ou le **bits**, **binaire**, ou **varbinary** des types de données. *expression* est traité comme un nombre binaire pour l’opération au niveau du bit.  
  
> [!NOTE]  
>  Seul *expression* peut être du type **binaire** ou **varbinary** type de données dans une opération au niveau du bit.  
  
## <a name="result-types"></a>Types des résultats  
 Retourne un **int** si les valeurs d’entrée sont **int**, un **smallint** si les valeurs d’entrée sont **smallint**, ou un **tinyint** si les valeurs d’entrée sont **tinyint**.  
  
## <a name="remarks"></a>Notes  
 L'opérateur | au niveau du bit exécute un OR logique au niveau du bit entre les deux expressions, évaluant chaque bit se correspondant dans les deux expressions. Dans le résultat, les bits prennent la valeur 1 si l'un des bits ou les deux (pour la position en cours d'évaluation) des expressions d'entrées ont la valeur 1 ; si aucun des deux bits des deux expressions d'entrée ne vaut 1, le bit du résultat est mis à 0.  
  
 Si les expressions de gauche et droite ont des types de données entiers différents (par exemple, sur la gauche *expression* est **smallint** et du droit *expression* est **int**), l’argument du type de données plus petit est converti au type de données plus volumineux. Dans cet exemple, le **smallint***expression* est converti en un **int**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une table avec **int** types pour afficher les valeurs d’origine et place la table dans une ligne.  
  
```tsql  
CREATE TABLE bitwise  
(   
 a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 La requête suivante effectue l’opération de bits OR sur les **a_int_value** et **b_int_value** colonnes.  
  
```  
SELECT a_int_value | b_int_value  
FROM bitwise;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
235           
  
(1 row(s) affected)  
```  
  
 La représentation binaire de 170 (**a_int_value** ou `A`, ci-dessous) est `0000 0000 1010 1010`. La représentation binaire de 75 (**b_int_value** ou `B`, ci-dessous) est `0000 0000 0100 1011`. L'exécution de l'opération OR au niveau du bit entre ces deux valeurs produit le résultat binaire `0000 0000 1110 1011`, c'est-à-dire 235 en décimal.  
  
```  
(A | B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 1110 1011  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Opérateurs de bits &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [&#124; = &#40; Opérateur de bits OR affectation &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


