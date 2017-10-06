---
title: PERCENTILE_DISC (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/20/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PERCENTILE_DISC
- PERCENTILE_DISC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PERCENTILE_DISC function
- analytic functions,PERCENTILE_DISC
ms.assetid: b545413d-c4f7-4c8e-8617-607599a26680
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a70610ecc826cda363cc0eea25baf090b24acc08
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="percentiledisc-transact-sql"></a>PERCENTILE_DISC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Calcule un percentile spécifique pour des valeurs triées dans un ensemble de lignes entier ou dans des partitions distinctes d'un ensemble de lignes dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour une valeur de percentile donnée *P*, PERCENTILE_DISC trie les valeurs de l’expression dans la clause ORDER BY et retourne la valeur ayant la plus petite valeur CUME_DIST (en ce qui concerne la même spécification de classement) est supérieur ou égal à *P*. Par exemple, PERCENTILE_DISC (0,5) calcule le cinquantième percentile (autrement dit, la valeur médiane) d'une expression. PERCENTILE_DISC calcule le percentile selon une répartition discrète des valeurs de la colonne ; le résultat est égal à une valeur spécifique dans la colonne.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PERCENTILE_DISC ( numeric_literal ) WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *littéral*  
 Percentile à calculer. Il doit être compris entre 0.0 et 1.0.  
  
 DANS le groupe **(** ORDER BY *order_by_expression* [ **ASC** | DESC]**)**  
 Spécifie une liste de valeurs permet de trier et de calculer le centile. Seul *order_by_expression* est autorisée. L’ordre de tri par défaut est croissant. La liste de valeurs peut être d’un des types de données qui sont valides pour l’opération de tri.  
  
 SUR **(** \<partition_by_clause > **)**  
 Divise le jeu de résultats généré par la clause FROM en partitions auxquelles la fonction percentile est appliquée. Pour plus d’informations, consultez [la Clause OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md). Le \<clause ORDER BY > et \<lignes ou la clause range > ne peut pas être spécifié dans une fonction PERCENTILE_DISC.  
  
## <a name="return-types"></a>Types de retour  
 Le type de retour est déterminé par le *order_by_expression* type.  
  
## <a name="compatibility-support"></a>Prise en charge de la compatibilité  
 Lorsque le niveau de compatibilité est 110 et supérieur, WITHIN GROUP est un mot clé réservé. Pour plus d’informations, consultez [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Toutes les valeurs NULL dans le jeu de données sont ignorées.  
  
 PERCENTILE_DISC n'est pas déterministe. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-basic-syntax-example"></a>A. Exemple de syntaxe de base  
 L'exemple suivant utilise PERCENTILE_CONT et PERCENTILE_DISC pour rechercher le salaire moyen d'un employé dans chaque service. Notez que ces fonctions peuvent ne pas retourner la même valeur. Cela est dû au fait que PERCENTILE_CONT interpole la valeur appropriée, qu'elle existe ou non dans le jeu de données, alors que PERCENTILE_DISC retourne toujours une valeur réelle à partir du jeu.  
  
```  
USE AdventureWorks2012;  
  
SELECT DISTINCT Name AS DepartmentName  
      ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianCont  
      ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianDisc  
FROM HumanResources.Department AS d  
INNER JOIN HumanResources.EmployeeDepartmentHistory AS dh   
    ON dh.DepartmentID = d.DepartmentID  
INNER JOIN HumanResources.EmployeePayHistory AS ph  
    ON ph.BusinessEntityID = dh.BusinessEntityID  
WHERE dh.EndDate IS NULL;  
```  
  
 Voici un jeu de résultats partiel.  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.8269      16.8269
Engineering            34.375       32.6923
Executive              54.32695     48.5577
Human Resources        17.427850    16.5865
```
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-basic-syntax-example"></a>B. Exemple de syntaxe de base  
 L'exemple suivant utilise PERCENTILE_CONT et PERCENTILE_DISC pour rechercher le salaire moyen d'un employé dans chaque service. Notez que ces fonctions peuvent ne pas retourner la même valeur. Cela est dû au fait que PERCENTILE_CONT interpole la valeur appropriée, qu'elle existe ou non dans le jeu de données, alors que PERCENTILE_DISC retourne toujours une valeur réelle à partir du jeu.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT DepartmentName  
       ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianCont  
       ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianDisc  
FROM dbo.DimEmployee;  
  
```  
  
 Voici un jeu de résultats partiel.  
  
 ```
DepartmentName        MedianCont    MedianDisc  
--------------------   ----------   ----------  
Document Control       16.826900    16.8269  
Engineering            34.375000    32.6923  
Human Resources        17.427850    16.5865  
Shipping and Receiving  9.250000     9.0000
```  
  
## <a name="see-also"></a>Voir aussi  
 [PERCENTILE_CONT &#40; Transact-SQL &#41;](../../t-sql/functions/percentile-cont-transact-sql.md)  
  
  



