---
title: IN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IN_TSQL
- IN
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], matching
- NOT IN keyword
- 8623 (Database Engine error)
- matching values in subquery or list [SQL Server]
- IN keyword
- 8632 (Database Engine error)
ms.assetid: 4419de73-96b1-4dfe-8500-f4507915db04
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70b186107966791e29ccb76ea9c310724b76e3b6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="in-transact-sql"></a>IN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Détermine si une valeur donnée correspond à la valeur d'une liste ou d'une sous-requête.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
test_expression [ NOT ] IN   
    ( subquery | expression [ ,...n ]  
    )   
```  
  
## <a name="arguments"></a>Arguments  
 *test_expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *sous-requête*  
 Sous-requête avec un jeu de résultats d'une colonne. Cette colonne doit avoir les mêmes données de type en tant que *test_expression*.  
  
 *expression*[ **,**... *n* ]  
 Liste d'expressions utilisée pour vérifier une correspondance. Toutes les expressions doivent être du même type que *test_expression*.  
  
## <a name="result-types"></a>Types des résultats  
 **Booléen**  
  
## <a name="result-value"></a>Valeur des résultats  
 Si la valeur de *test_expression* est égale à toute valeur retournée par *sous-requête* ou est égale à *expression* dans la liste séparée par des virgules, la valeur de résultat a la valeur TRUE ; sinon, le résultat est FALSE.  
  
 L’utilisation de NOT IN inverse les *sous-requête* valeur ou *expression*.  
  
> [!CAUTION]  
>  Toute valeur null retournée par *sous-requête* ou *expression* qui sont comparés aux *test_expression* en utilisant IN ou NOT IN retourne UNKNOWN. L'utilisation de valeurs Null avec IN ou NOT IN peut produire des résultats inattendus.  
  
## <a name="remarks"></a>Notes  
 Explicitement, y compris un très grand nombre de valeurs (plusieurs milliers de valeurs séparées par des virgules) entre parenthèses, dans une clause IN peut consommer des ressources et retourner des erreurs 8623 ou 8632. Pour contourner ce problème, stockez les éléments dans la liste IN dans une table et utilisez une sous-requête SELECT dans une clause IN.  
  
 Erreur 8623 :  
  
 `The query processor ran out of internal resources and could not produce a query plan. This is a rare event and only expected for extremely complex queries or queries that reference a very large number of tables or partitions. Please simplify the query. If you believe you have received this message in error, contact Customer Support Services for more information.`  
  
 Erreur 8632 :  
  
 `Internal error: An expression services limit has been reached. Please look for potentially complex expressions in your query, and try to simplify them.`  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-comparing-or-and-in"></a>A. Comparaison des opérateurs OR et IN  
 L'exemple suivant sélectionne une liste des noms d'employés qui sont ingénieurs concepteurs, concepteurs d'outils ou assistants marketing.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle = 'Design Engineer'   
   OR e.JobTitle = 'Tool Designer'   
   OR e.JobTitle = 'Marketing Assistant';  
GO  
```  
  
 Vous obtenez toutefois les mêmes résultats en utilisant IN.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle IN ('Design Engineer', 'Tool Designer', 'Marketing Assistant');  
GO  
```  
  
 Voici le jeu de résultats obtenu pour l'une ou l'autre des requêtes.  
  
```  
FirstName   LastName      Title  
---------   ---------   ---------------------  
Sharon      Salavaria   Design Engineer                                     
Gail        Erickson    Design Engineer                                     
Jossef      Goldberg    Design Engineer                                     
Janice      Galvin      Tool Designer                                       
Thierry     D'Hers      Tool Designer                                       
Wanida      Benshoof    Marketing Assistant                                 
Kevin       Brown       Marketing Assistant                                 
Mary        Dempsey     Marketing Assistant                                 
  
(8 row(s) affected)  
```  
  
### <a name="b-using-in-with-a-subquery"></a>B. Utilisation de l'opérateur IN avec une sous-requête  
 L'exemple suivant recherche tous les ID des vendeurs dans la table `SalesPerson` pour les employés dont le quota de ventes annuel est supérieur à 250 000 $. Il sélectionne ensuite, dans la table `Employee`, les noms de tous les employés dont l'`EmployeeID` correspond aux résultats issus de la sous-requête `SELECT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FirstName   LastName                                             
---------   --------   
Tsvi         Reiter                                              
Michael      Blythe                                              
Tete         Mensa-Annan                                         
  
(3 row(s) affected)  
```  
  
### <a name="c-using-not-in-with-a-subquery"></a>C. Utilisation de l'opérateur NOT IN avec une sous-requête  
 L'exemple suivant recherche les vendeurs qui n'ont pas de quota supérieur à 250 000 $. `NOT IN` identifie les vendeurs qui ne correspondent pas aux éléments de la liste de valeurs.  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID NOT IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-in-and-not-in"></a>D. À l’aide d’en et pas dans  
 L’exemple suivant recherche toutes les entrées de la `FactInternetSales` qui correspondent à la table `SalesReasonKey` des valeurs dans le `DimSalesReason` table.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
IN (SELECT SalesReasonKey FROM DimSalesReason);   
```  
  
 L’exemple suivant recherche toutes les entrées de la `FactInternetSalesReason` table qui ne correspondent pas aux `SalesReasonKey` des valeurs dans le `DimSalesReason` table.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
NOT IN (SELECT SalesReasonKey FROM DimSalesReason);  
```  
  
### <a name="e-using-in-with-an-expression-list"></a>E. À l’aide avec une liste d’expressions  
 L’exemple suivant recherche tous les ID des vendeurs dans le `DimEmployee` de table pour les employés qui ont un premier nom qui est soit `Mike` ou `Michael`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM DimEmployee  
WHERE FirstName IN ('Mike', 'Michael');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [OÙ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [Tous les &#40; Transact-SQL &#41;](../../t-sql/language-elements/all-transact-sql.md)   
 [Certains &#124; &#40; Transact-SQL &#41;](../../t-sql/language-elements/some-any-transact-sql.md)  
  
  




