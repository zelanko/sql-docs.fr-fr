---
title: CHARINDEX (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHARINDEX
- CHARINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], pattern searching
- CHARINDEX function
- pattern searching [SQL Server]
- starting point of expression in character string
ms.assetid: 78c10341-8373-4b30-b404-3db20e1a3ac4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: ed2f5334c0c76288ca31cf07857a87f2d1c72033
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="charindex-transact-sql"></a>CHARINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Recherche une autre expression dans une expression et retourne sa position de départ, le cas échéant.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CHARINDEX ( expressionToFind , expressionToSearch [ , start_location ] )   
```  
  
## <a name="arguments"></a>Arguments  
*expressionToFind*  
Est un caractère [expression](../../t-sql/language-elements/expressions-transact-sql.md) qui contient la séquence à rechercher. *expressionToFind* est limité à 8 000 caractères.
  
*expressionToSearch*  
Expression de caractères à rechercher.
  
*start_location*  
Est un **entier** ou **bigint** expression à laquelle la recherche commence. Si *start_location* n’est pas spécifié, est un nombre négatif ou est égal à 0, la recherche commence au début de *expressionToSearch*.
  
## <a name="return-types"></a>Types de retour
**bigint** si *expressionToSearch* est de le **varchar (max)**, **nvarchar (max)**, ou **varbinary (max)** des types de données ; sinon, **int**.
  
## <a name="remarks"></a>Notes  
Si le paramètre *expressionToFind* ou *expressionToSearch* est d’un type de données Unicode (**nvarchar** ou **nchar**) et l’autre ne l’est pas, l’autre est converti en un type de données Unicode. Fonction CHARINDEX ne peut pas être utilisée avec **texte**, **ntext**, et **image** des types de données.
  
Si le paramètre *expressionToFind* ou *expressionToSearch* est NULL, CHARINDEX retourne NULL.
  
Si *expressionToFind* n’est trouvé dans *expressionToSearch*, CHARINDEX retourne 0.
  
CHARINDEX effectue des comparaisons basées sur le classement de l'entrée. Pour exécuter une comparaison selon un classement spécifié, vous pouvez utiliser COLLATE pour appliquer à l'entrée un classement explicite.
  
La position de départ retournée est basée sur la valeur 1, et non sur la valeur 0.
  
0 x 0000 (**char(0)**) est un caractère indéfini dans les classements Windows et ne peut pas être inclus dans CHARINDEX.
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caractères supplémentaires (paires de substitution)  
Lors de l’utilisation de classements SC, les deux *start_location* et la valeur de retour comptent les paires substitution comme un caractère, pas les deux. Pour plus d’informations, consultez [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-starting-position-of-an-expression"></a>A. Retour de la position de départ d'une expression  
L'exemple suivant retourne la position initiale de la séquence de caractères `bicycle` dans la colonne `DocumentSummary` de la table `Document` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
DECLARE @document varchar(64);  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bicycle', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
48            
```  
  
### <a name="b-searching-from-a-specific-position"></a>B. Recherche à partir d'une position spécifique  
L’exemple suivant utilise le paramètre facultatif *start_location* paramètre pour commencer la recherche de `vital` au cinquième caractère de la `DocumentSummary` colonne dans la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('vital', @document, 5);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
16            
  
(1 row(s) affected)  
```  
  
### <a name="c-searching-for-a-nonexistent-expression"></a>C. Recherche d'une expression inexistante  
L’exemple suivant montre le jeu de résultats lorsque *expressionToFind* n’est trouvé dans *expressionToSearch*.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bike', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
  
(1 row(s) affected)
```
  
### <a name="d-performing-a-case-sensitive-search"></a>D. Recherche respectant la casse  
L’exemple suivant effectue une recherche qui respecte la casse de la chaîne `'TEST'` dans `'This is a Test``'`.
  
```sql
USE tempdb;  
GO  
--perform a case sensitive search  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
```  
  
L’exemple suivant effectue une recherche qui respecte la casse de la chaîne `'Test'` dans `'This is a Test'`.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'Test',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
13
```  
  
### <a name="e-performing-a-case-insensitive-search"></a>E. Recherche ne respectant pas la casse  
L'exemple suivant effectue une recherche qui ne respecte pas la casse de la chaîne `'TEST'` dans `'This is a Test'`.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CI_AS);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
13
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="f-searching-from-the-start-of-a-string-expression"></a>F. Recherche à partir du début d’une expression de chaîne  
L’exemple suivant retourne le premier emplacement de la `is` de chaîne dans `This is a string`, en commençant à partir de la position 1 (le premier caractère) dans la chaîne.
  
```sql
SELECT CHARINDEX('is', 'This is a string');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
3
```  
  
### <a name="g-searching-from-a-position-other-than-the-first-position"></a>G. Recherche à partir d’une position autre que la première position  
L’exemple suivant retourne le premier emplacement de la `is` de chaîne dans `This is a string`, en commençant par la quatrième position.
  
```sql
SELECT CHARINDEX('is', 'This is a string', 4);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
 6
 ```  
  
### <a name="h-results-when-the-string-is-not-found"></a>H. Résultats de la chaîne est introuvable.  
L’exemple suivant montre la valeur de retour lorsque la *string_pattern* est introuvable dans la chaîne recherchée.
  
```sql
SELECT TOP(1) CHARINDEX('at', 'This is a string') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
0
```  
  
## <a name="see-also"></a>Voir aussi
 [LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)  
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
 [+ &#40;String Concatenation&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
 [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  


