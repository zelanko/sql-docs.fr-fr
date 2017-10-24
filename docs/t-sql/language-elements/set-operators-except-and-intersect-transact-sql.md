---
title: EXCEPT et INTERSECT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INTERSECT_TSQL
- EXCEPT_TSQL
- INTERSECT
- EXCEPT
dev_langs:
- TSQL
helpviewer_keywords:
- EXCEPT operator [Transact-SQL]
- queries [SQL Server], comparing
- comparing queries
- INTERSECT operator
ms.assetid: b1019300-171a-4a1a-854f-e1e751de3565
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d8bff51308e9b8dbf02066d56b73829bc1658c2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-operators---except-and-intersect-transact-sql"></a>Jeu d’opérateurs - sauf et INTERSECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne des lignes distinctes en comparant les résultats de deux requêtes.  
  
 EXCEPT retourne les lignes distinctes de la requête d'entrée à gauche mais non trouvées par la requête d'entrée à droite.  
  
 INTERSECT retourne des lignes distinctes qui sont générées par les deux l’opérateur gauche et droit de requêtes d’entrée.  
  
 Voici deux règles essentielles pour combiner les ensembles de résultats de deux requêtes utilisant l'opérande EXCEPT ou l'opérande INTERSECT :  
  
-   Le nombre et l'ordre des colonnes doivent être identiques dans toutes les requêtes.  
  
-   Les types de données doivent être compatibles.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
{ <query_specification> | ( <query_expression> ) }   
{ EXCEPT | INTERSECT }  
{ <query_specification> | ( <query_expression> ) }  
```  
  
## <a name="arguments"></a>Arguments  
 \<*query_specification*> | ( \< *query_expression*>)  
 Spécification ou expression de requête qui retourne les données à comparer avec les données d'une autre spécification ou expression de requête. Les définitions des colonnes faisant partie d'une opération EXCEPT ou INTERSECT ne doivent pas forcément être identiques, mais doivent néanmoins être comparables par le biais d'une conversion implicite. Lorsque les types de données diffèrent, le type qui est utilisé pour effectuer la comparaison et de retourner des résultats est déterminé selon les règles de [priorité des types de données](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
 Si les types sont les mêmes mais diffèrent en terme de précision, d'échelle ou de longueur, le résultat se détermine d'après les mêmes règles de combinaison d'expressions. Pour plus d’informations, consultez [Précision, échelle et longueur &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 La spécification de la requête ou l’expression ne peut pas retourner **xml**, **texte**, **ntext**, **image**, ou les colonnes de type CLR non binaire défini par l’utilisateur, car ces types de données ne sont pas comparables.  
  
 EXCEPT  
 Retourne des valeurs distinctes à partir de la requête à gauche de l’opérateur EXCEPT qui ne sont pas retournées à partir de la requête à droite.  
  
 INTERSECT  
 Retourne toute valeur distincte trouvée par les requêtes à gauche et à droite de l'opérateur INTERSECT.  
  
## <a name="remarks"></a>Notes  
 Lorsque les types de données de colonnes comparables retournées par les requêtes à gauche et à droite de la EXCEPT ou opérateur INTERSECT sont de types de données de caractères avec des classements différents, la comparaison nécessaire s’effectue selon les règles de [la priorité de classement](../../t-sql/statements/collation-precedence-transact-sql.md). Si cette conversion est impossible, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] retourne une erreur.  
  
 Lors de la comparaison des valeurs de colonnes pour trouver les lignes DISTINCT, deux valeurs NULL sont considérées comme égales.  
  
 Les noms de colonnes du jeu de résultats retournés par EXCEPT ou INTERSECT sont identiques à ceux retournés par la requête se trouvant à gauche de l'opérateur.  
  
 Les noms ou les alias de colonnes placés dans des clauses ORDER BY doivent faire référence aux noms de colonnes retournés par la requête de gauche.  
  
 La propriété de toute colonne acceptant des valeurs NULL, lesquelles font partie du jeu de résultats retourné par EXCEPT ou INTERSECT, revient à la propriété à accepter des valeurs NULL par sa colonne correspondante retournée par la requête se trouvant à gauche de l'opérateur.  
  
 Si EXCEPT ou INTERSECT sont utilisés conjointement avec d'autres opérateurs au sein d'une expression, l'expression finale s'évalue d'après la règle de précédence suivante :  
  
1.  expressions entre parenthèses ;  
  
2.  opérateur INTERSECT ;  
  
3.  EXCEPT et UNION évaluée de gauche à droite d'après leur position dans l'expression.  
  
 Si EXCEPT ou INTERSECT est utilisé pour comparer plus de deux ensembles de requêtes, la conversion de type de données est déterminée en comparant deux requêtes à la fois et en suivant les règles précédemment mentionnées relatives à l'évaluation d'expressions.  
  
 EXCEPT et INTERSECT ne peuvent pas être utilisées dans une définition de vue partitionnée distribuée ou des notifications de requêtes.  
  
 Vous pouvez toujours les utiliser dans les requêtes distribuées à condition de ne les exécuter que sur un serveur local et de ne pas les envoyer à un serveur lié. Il se peut par conséquent que les performances soient affectées par l'utilisation d'EXCEPT et d'INTERSECT dans des requêtes distribuées.  
  
 Les curseurs avant uniquement statiques ou rapides sont entièrement pris en charge dans l'ensemble de résultats s'ils sont utilisés avec une opération EXCEPT ou INTERSECT. Si un curseur piloté par jeu de clés ou un curseur dynamique est utilisé avec une opération EXCEPT ou INTERSECT, le curseur de l'ensemble de résultats de l'opération est converti en curseur statique.  
  
 Lorsqu’une opération EXCEPT est affichée à l’aide de la fonctionnalité Graphical Showplan de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], l’opération apparaît comme un [semi jointure anti gauche](../../relational-databases/showplan-logical-and-physical-operators-reference.md), et une opération INTERSECT apparaît comme un [semi-jointure gauche](../../relational-databases/showplan-logical-and-physical-operators-reference.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent l’utilisation du `INTERSECT` et `EXCEPT` opérateurs. La première requête retourne toutes les valeurs de la table `Production.Product` pour qu'elles soient comparées aux résultats à l'aide de `INTERSECT` et de `EXCEPT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product ;  
--Result: 504 Rows  
```  
  
 La requête suivante retourne toute valeur distincte trouvée par les requêtes à gauche et à droite de l'opérateur `INTERSECT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
INTERSECT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 238 Rows (products that have work orders)  
```  
  
 La requête suivante retourne toute valeur distincte trouvée par la requête à gauche de l'opérateur `EXCEPT`, mais non trouvée par la requête à droite.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
EXCEPT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 266 Rows (products without work orders)  
```  
  
 La requête suivante retourne toute valeur distincte trouvée par la requête à gauche de l'opérateur `EXCEPT`, mais non trouvée par la requête à droite. Les tables sont inversées par rapport à l'exemple précédent.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.WorkOrder  
EXCEPT  
SELECT ProductID   
FROM Production.Product ;  
--Result: 0 Rows (work orders without products)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Les exemples suivants illustrent la manière d'utiliser les opérateurs `INTERSECT` et `EXCEPT`. La première requête retourne toutes les valeurs de la table `FactInternetSales` pour qu'elles soient comparées aux résultats à l'aide de `INTERSECT` et de `EXCEPT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales;  
--Result: 60398 Rows  
```  
  
 La requête suivante retourne toute valeur distincte trouvée par les requêtes à gauche et à droite de l'opérateur `INTERSECT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
INTERSECT   
SELECT CustomerKey   
FROM DimCustomer   
WHERE DimCustomer.Gender = 'F'  
ORDER BY CustomerKey;  
--Result: 9133 Rows (Sales to customers that are female.)  
```  
  
 La requête suivante retourne toute valeur distincte trouvée par la requête à gauche de l'opérateur `EXCEPT`, mais non trouvée par la requête à droite.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
EXCEPT   
SELECT CustomerKey   
FROM DimCustomer   
WHERE DimCustomer.Gender = 'F'  
ORDER BY CustomerKey;  
--Result: 9351 Rows (Sales to customers that are not female.)  
```  
  
  


