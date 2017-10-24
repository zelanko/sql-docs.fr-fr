---
title: Recherche (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- search
- Search Condition
- condition
dev_langs:
- TSQL
helpviewer_keywords:
- OR operator [Transact-SQL]
- CONTAINS predicate (Transact-SQL)
- ESCAPE keyword
- operators [Transact-SQL], search condition
- search conditions [SQL Server]
- WHERE clause, search conditions
- ALL keyword
- FREETEXT predicate (Transact-SQL)
- EXISTS keyword
- search conditions [SQL Server], about search conditions
- NOT operator [Transact-SQL]
- BETWEEN operator
- SOME | ANY keyword
- predicates [full-text search]
- AND, about search conditions
- logical operators [SQL Server], about search conditions
- precedence [SQL Server], logical operators
- logical operators [SQL Server], precedence
- LIKE comparisons
ms.assetid: 09974469-c5d2-4be8-bc5a-78e404660b2c
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: ad0a32f2f11c7b0ca781c7e01635204da38fcbdd
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="search-condition-transact-sql"></a>Condition de recherche (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combinaison d'un ou de plusieurs prédicats qui utilisent les opérateurs logiques AND, OR et NOT.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<search_condition> ::=   
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | ! > | < | < = | ! < } expression   
    | string_expression [ NOT ] LIKE string_expression   
  [ ESCAPE 'escape_character' ]   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | CONTAINS   
  ( { column | * } , '<contains_search_condition>' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery )     }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
< search_condition > ::=   
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | < | < = } expression   
    | string_expression [ NOT ] LIKE string_expression   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | expression [ NOT ] IN (subquery | expression [ ,...n ] )   
    | expression [ NOT ] EXISTS (subquery)     }   
```  
  
## <a name="arguments"></a>Arguments  
 \<search_condition >  
 Pour une instruction SELECT, une expression de requête ou une sous-requête, spécifie les conditions des lignes retournées dans le jeu de résultats. Pour une instruction UPDATE, spécifie les lignes à mettre à jour. Pour une instruction DELETE, spécifie les lignes à supprimer. Le nombre de prédicats pouvant être inclus dans une condition de recherche d'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] est illimité.  
  
 NOT  
 Inverse l'expression booléenne spécifiée par le prédicat. Pour plus d’informations, consultez [pas &#40; Transact-SQL &#41; ](../../t-sql/language-elements/not-transact-sql.md).  
  
 AND  
 Combine deux conditions et a la valeur TRUE lorsque les deux conditions ont l'une et l'autre la valeur TRUE. Pour plus d’informations, consultez [et &#40; Transact-SQL &#41; ](../../t-sql/language-elements/and-transact-sql.md).  
  
 ou  
 Combine deux conditions et a la valeur TRUE lorsque l'une des deux conditions a la valeur TRUE. Pour plus d’informations, consultez [ou &#40; Transact-SQL &#41; ](../../t-sql/language-elements/or-transact-sql.md).  
  
 \<prédicat >  
 Expression qui retourne la valeur TRUE, FALSE ou UNKNOWN.  
  
 *expression*  
 Nom de colonne, constante, fonction, variable, sous-requête scalaire ou toute combinaison de noms de colonnes, de constantes et de fonctions reliées par un ou plusieurs opérateurs ou par une sous-requête. L'expression peut également contenir l'expression CASE.  
  
> [!NOTE]  
>  Lors du référencement de types de données caractères Unicode **nchar**, **nvarchar**, et **ntext**, 'expression' doit comporter la majuscule n '. Si vous ne spécifiez pas « N », [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit la chaîne dans la page de codes qui correspond au classement par défaut de la base de données ou de la colonne. Tous les caractères absents de cette page de codes sont alors perdus.  
  
 =  
 Opérateur utilisé pour tester l'égalité de deux expressions.  
  
 <>  
 Opérateur utilisé pour tester l'inégalité de deux expressions.  
  
 !=  
 Opérateur utilisé pour tester l'inégalité de deux expressions.  
  
 \>  
 Opérateur utilisé pour tester la supériorité d'une expression par rapport à une autre.  
  
 \>=  
 Opérateur utilisé pour tester la supériorité ou l'égalité d'une expression par rapport à une autre.  
  
 !>  
 Opérateur utilisé pour tester la non-supériorité d'une expression par rapport à une autre.  
  
 <  
 Opérateur utilisé pour tester l'infériorité d'une expression par rapport à une autre.  
  
 <=  
 Opérateur utilisé pour tester l'infériorité ou l'égalité d'une expression par rapport à une autre.  
  
 !<  
 Opérateur utilisé pour tester la non-infériorité d'une expression par rapport à une autre.  
  
 *string_expression*  
 Chaîne de caractères et de caractères génériques.  
  
 [ NOT ] LIKE  
 Indique que la chaîne de caractères suivante sera utilisée avec une syntaxe de correspondance au modèle. Pour plus d’informations, consultez [comme &#40; Transact-SQL &#41; ](../../t-sql/language-elements/like-transact-sql.md).  
  
 Séquence d’échappement **'***escape_ caractère***'**  
 Permet la recherche d'un caractère générique dans une chaîne de caractères et non en tant que caractère générique. *escape_character* est le caractère placé devant le caractère générique pour indiquer cette utilisation spéciale.  
  
 [ NOT ] BETWEEN  
 Définit une plage inclusive (ou exclusive) de valeurs. Utilisez AND pour séparer les valeurs de début et de fin. Pour plus d’informations, consultez [BETWEEN &#40; Transact-SQL &#41; ](../../t-sql/language-elements/between-transact-sql.md).  
  
 IS [NOT] NULL  
 Définit une recherche des valeurs NULL ou non NULL suivant les mots clé utilisés. Une expression avec un opérateur au niveau du bit ou un opérateur arithmétique retourne la valeur NULL si l'un des opérandes a la valeur NULL.  
  
 CONTAINS  
 Recherche dans des colonnes qui contiennent des données caractères de plus ou moins précises (*floue*) correspond à des mots ou d’expressions, la proximité de mots à une certaine distance de, ainsi que des correspondances pondérées. Cette option ne peut être utilisée qu'avec les instructions SELECT. Pour plus d’informations, consultez [CONTAINS &#40; Transact-SQL &#41; ](../../t-sql/queries/contains-transact-sql.md).  
  
 FREETEXT  
 Fournit une forme simple de requête en langage naturel qui recherche dans des colonnes de caractères les synonymes et non les termes exacts du prédicat. Cette option ne peut être utilisée qu'avec les instructions SELECT. Pour plus d’informations, consultez [FREETEXT &#40; Transact-SQL &#41; ](../../t-sql/queries/freetext-transact-sql.md).  
  
 [ NOT ] IN  
 Définit la recherche d'une expression, selon que cette dernière est incluse ou non dans une liste. L'expression de recherche peut être une constante ou un nom de colonne ; par ailleurs, la liste peut être un ensemble de constantes ou, plus généralement, une sous-requête. Mettez la liste des valeurs entre parenthèses. Pour plus d’informations, consultez [IN &#40; Transact-SQL &#41; ](../../t-sql/language-elements/in-transact-sql.md).  
  
 *sous-requête*  
 Peut être considéré comme une instruction SELECT restreinte et ressemble à \<query_expresssion > dans l’instruction SELECT. La clause ORDER BY et le mot clé INTO ne sont pas autorisés. Pour plus d’informations, consultez [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
 ALL  
 Utilisé avec un opérateur de comparaison et une sous-requête. Retourne la valeur TRUE pour \<prédicat > lorsque toutes les valeurs extraites pour la sous-requête satisfont l’opération de comparaison, ou False (faux) pas toutes les valeurs de la comparaison ou quand la sous-requête ne retourne aucune ligne à l’instruction externe. Pour plus d’informations, consultez [tous les &#40; Transact-SQL &#41; ](../../t-sql/language-elements/all-transact-sql.md).  
  
 { SOME | ANY }  
 Utilisé avec un opérateur de comparaison et une sous-requête. Retourne la valeur TRUE pour \<prédicat > lorsque n’importe quelle valeur extraite pour la sous-requête satisfait l’opération de comparaison, ou la valeur FALSE lorsque aucune valeur dans la sous-requête satisfait la comparaison ou quand la sous-requête ne retourne aucune ligne à l’instruction externe. Dans les autres cas, l'expression est inconnue (UNKNOWN). Pour plus d’informations, consultez [certaines &#124; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 EXISTS  
 Utilisée avec une sous-requête pour vérifier l’existence de lignes renvoyées par la sous-requête. Pour plus d’informations, consultez [EXISTS &#40; Transact-SQL &#41; ](../../t-sql/language-elements/exists-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 L'ordre de priorité des opérateurs logiques est NOT (la plus élevée), puis AND, puis OR. Les parenthèses peuvent être utilisées pour remplacer cette priorité dans un critère de recherche. L'ordre d'évaluation des opérateurs logiques peut varier en fonction des choix effectués par l'optimiseur de requête. Pour plus d’informations sur le fonctionnement des opérateurs logiques sur des valeurs logiques, consultez [et &#40; Transact-SQL &#41; ](../../t-sql/language-elements/and-transact-sql.md), [Ou &#40; Transact-SQL &#41; ](../../t-sql/language-elements/or-transact-sql.md), et [pas &#40; Transact-SQL &#41; ](../../t-sql/language-elements/not-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-where-with-like-and-escape-syntax"></a>A. Utilisation de WHERE avec la syntaxe LIKE et ESCAPE  
 L’exemple suivant recherche les lignes dans lesquelles la `LargePhotoFileName` colonne comprend les caractères `green_`et utilise le `ESCAPE` option _ étant un caractère générique. Sans spécifier le `ESCAPE` option, la requête rechercherait toutes les valeurs de description contenant le mot `green` suivie de n’importe quel caractère unique autre que le caractère _.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT *   
FROM Production.ProductPhoto  
WHERE LargePhotoFileName LIKE '%greena_%' ESCAPE 'a' ;  
```  
  
### <a name="b-using-where-and-like-syntax-with-unicode-data"></a>B. Utilisation de la syntaxe WHERE et LIKE avec des données Unicode  
 Cet exemple utilise la clause `WHERE` pour récupérer l'adresse postale de toutes les sociétés qui se trouvent hors des États-Unis (`US`) et dans une ville dont le nom commence par `Pa`.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT AddressLine1, AddressLine2, City, PostalCode, CountryRegionCode    
FROM Person.Address AS a  
JOIN Person.StateProvince AS s ON a.StateProvinceID = s.StateProvinceID  
WHERE CountryRegionCode NOT IN ('US')  
AND City LIKE N'Pa%' ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-where-with-like"></a>C. Utilisation de WHERE avec LIKE  
 L’exemple suivant recherche les lignes dans lesquelles la `LastName` colonne comprend les caractères `and`.  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE '%and%';  
```  
  
### <a name="d-using-where-and-like-syntax-with-unicode-data"></a>D. Utilisation de la syntaxe WHERE et LIKE avec des données Unicode  
 L’exemple suivant utilise le `WHERE` clause pour effectuer une recherche Unicode sur le `LastName` colonne.  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE N'%and%';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’agrégation &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [CAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [Curseurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  


