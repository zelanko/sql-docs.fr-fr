---
title: Recherche (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 01/15/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- search
- Search Condition
- condition
dev_langs: TSQL
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
caps.latest.revision: "43"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aff1f4010182b601111ed2ba892bb06b6e82b71d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="search-condition-transact-sql"></a>Condition de recherche (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

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
 \<search_condition>  
 Pour une instruction SELECT, une expression de requête ou une sous-requête, spécifie les conditions des lignes retournées dans le jeu de résultats. Pour une instruction UPDATE, spécifie les lignes à mettre à jour. Pour une instruction DELETE, spécifie les lignes à supprimer. Le nombre de prédicats pouvant être inclus dans une condition de recherche d'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] est illimité.  
  
 NOT  
 Inverse l'expression booléenne spécifiée par le prédicat. Pour plus d’informations, consultez [pas &#40; Transact-SQL &#41; ](../../t-sql/language-elements/not-transact-sql.md).  
  
 AND  
 Combine deux conditions et a la valeur TRUE lorsque les deux conditions ont l'une et l'autre la valeur TRUE. Pour plus d’informations, consultez [et &#40; Transact-SQL &#41; ](../../t-sql/language-elements/and-transact-sql.md).  
  
 OU  
 Combine deux conditions et a la valeur TRUE lorsque l'une des deux conditions a la valeur TRUE. Pour plus d’informations, consultez [ou &#40; Transact-SQL &#41; ](../../t-sql/language-elements/or-transact-sql.md).  
  
 \<prédicat >  
 Expression qui retourne la valeur TRUE, FALSE ou UNKNOWN.  
  
 *expression*  
 Nom de colonne, constante, fonction, variable, sous-requête scalaire ou toute combinaison de noms de colonnes, de constantes et de fonctions reliées par un ou plusieurs opérateurs ou par une sous-requête. L'expression peut également contenir l'expression CASE.  
  
> [!NOTE]  
>  Variables et les constantes de chaîne Non-Unicode. utilisent la page de codes qui correspond au classement par défaut de la base de données. Peut se produire les conversions de page de code lorsque vous travaillez avec uniquement les données de caractères non-Unicode et faisant référence à des types de données caractères non-Unicode **char**, **varchar**, et **texte**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Convertit des variables et constantes de chaîne non-Unicode à la page de codes qui correspond au classement de la colonne référencée ou spécifié à l’aide de COLLATE, si cette page de codes est différente de celui de la page de codes qui correspond au classement par défaut de la base de données. Tous les caractères introuvables dans la nouvelle page de codes seront convertis en un caractère similaire, si un [mappage ajusté](http://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) peut être trouvée, sinon sera convertie en caractère de remplacement par défaut de « ? ».  
>  
> Lorsque vous travaillez avec plusieurs pages de codes, les constantes de caractère peuvent être préfixés par la lettre majuscule n ', Unicode et variables peuvent être utilisées afin d’éviter des conversions de page de codes.  
  
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
 Définit la recherche d'une expression, selon que cette dernière est incluse ou non dans une liste. L'expression de recherche peut être une constante ou un nom de colonne ; par ailleurs, la liste peut être un ensemble de constantes ou, plus généralement, une sous-requête. Mettez la liste des valeurs entre parenthèses. Pour plus d’informations, consultez [IN &#40;Transact-SQL&#41;](../../t-sql/language-elements/in-transact-sql.md).  
  
 *subquery*  
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
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [Curseurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  

