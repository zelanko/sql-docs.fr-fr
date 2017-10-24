---
title: STRING_AGG (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STRING_AGG
- STRING_AGG_TSQL
helpviewer_keywords:
- STRING_AGG function
ms.assetid: 8860ef3f-142f-4cca-aa64-87a123e91206
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bf74698e9e61f456726b1e6a62126a8d78a09777
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stringagg-transact-sql"></a>STRING_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

Concatène les valeurs des expressions de chaîne et place les valeurs de séparation entre eux. Le séparateur n’est pas ajouté à la fin de chaîne.
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STRING_AGG ( expression, separator ) [ <order_clause> ]

<order_clause> ::=   
    WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )   
```

## <a name="arguments"></a>Arguments 

*séparateur*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de `NVARCHAR` ou `VARCHAR` type qui est utilisé comme séparateur pour concaténer des chaînes. Il peut être littéral ou une variable. 

*expression*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type. Expressions sont converties en `NVARCHAR` ou `VARCHAR` types lors de la concaténation. Les autres types sont convertis en `NVARCHAR` type.


< order_clause >   
Si vous le souhaitez spécifier l’ordre des résultats concaténés à l’aide de `WITHIN GROUP` clause :
```
WITHIN GROUP ( ORDER BY <order_by_expression_list> [ ASC | DESC ] )
```   
< order_by_expression_list >   
 
  Une liste de constante non [expressions](../../t-sql/language-elements/expressions-transact-sql.md) qui peut être utilisé pour le tri des résultats. Seul `order_by_expression` est autorisé par la requête. L’ordre de tri par défaut est croissant.   
  

## <a name="return-types"></a>Types de retour 

Type de retour est varie selon le premier argument (expression). Si un argument d’entrée est de type chaîne (`NVARCHAR`, `VARCHAR`), le type de résultat sera identique au type d’entrée. Le tableau suivant répertorie les conversions automatiques :  

|Type de l’expression d’entrée |Résultat | 
|-------|-------|
|NVARCHAR(MAX) |NVARCHAR(MAX) |
|VARCHAR(MAX) |VARCHAR(MAX) |
|NVARCHAR (1... 4000) |NVARCHAR (4000) |
|VARCHAR (1... 8000) |VARCHAR(8000) |
|int, bigint, smallint, tinyint, numeric, float, real, bit, decimal, smallmoney, money, datetime, datetime2, |NVARCHAR (4000) |


## <a name="remarks"></a>Notes  
 
`STRING_AGG`agrégat accepte toutes les expressions à partir des lignes et les concatène en une seule chaîne. Valeurs d’expression sont implicitement convertis en types chaîne et ensuite concaténés. La conversion implicite en chaînes respecte les règles existantes de conversion de type de données. Pour plus d’informations sur les conversions de type de données, consultez [CAST et CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md). 

Si l’expression d’entrée est de type `VARCHAR`, le séparateur ne peut pas être de type `NVARCHAR`. 

Les valeurs NULL sont ignorées et le séparateur correspondant n’est pas ajouté. Pour retourner un espace réservé pour les valeurs null, utilisez la `ISNULL` de fonction comme illustré dans l’exemple B.

`STRING_AGG`dans n’importe quel niveau de compatibilité n’est disponible.


## <a name="examples"></a>Exemples 

### <a name="a-generate-list-of-names-separated-in-new-lines"></a>A. Générer la liste de noms séparés dans les nouvelles lignes 
L’exemple suivant génère une liste de noms dans une cellule de résultat unique, séparées par des retours chariot.
```tsql
SELECT STRING_AGG (FirstName, CHAR(13)) AS csv 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|csv | 
|--- |
|Syed <br />Catherine <br />Kim <br />Kim <br />Kim <br />Hazem <br />... | 

`NULL`valeurs trouvées dans `name` cellules ne sont pas retournés dans les résultats.   
> [!NOTE]  
>  Si vous utilisez l’éditeur de requête de Management Studio, le **résultats dans des grilles** option ne peut pas implémenter le retour chariot. Basculez vers **résultats dans du texte** pour voir le résultat correctement défini.   


### <a name="b-generate-list-of-names-separated-with-comma-without-null-values"></a>B. Générer la liste de noms séparés par des virgules sans les valeurs NULL   
L’exemple suivant remplace les valeurs null avec le « N/a » et retourne les noms séparés par des virgules dans une cellule de résultat unique.  
```tsql
SELECT STRING_AGG ( ISNULL(FirstName,'N/A'), ',') AS csv 
FROM Person.Person; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
 

|Volumes partagés de cluster | 
|--- |
|John, n/a, Mike, Peter, n/a, n/a, Alice, Bob |  


### <a name="c-generate-comma-separated-values"></a>C. Générer des valeurs séparées par des virgules 

```tsql   
SELECT 
STRING_AGG(CONCAT(FirstName, ' ', LastName, ' (', ModifiedDate, ')'), CHAR(13)) 
  AS names 
FROM Person.Person; 
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|noms | 
|--- |
|Ken Sánchez (8 février 2003 12:00 AM) <br />Terri Duffyen (24 février 2002 12:00 AM) <br />Roberto Tamburello (5 décembre 2001 12:00 AM) <br />Famille de Rob (29 décembre 2001 12:00 AM) <br />... |

> [!NOTE]  
>  Si vous utilisez l’éditeur de requête de Management Studio, le **résultats dans des grilles** option ne peut pas implémenter le retour chariot. Basculez vers **résultats dans du texte** pour voir le résultat correctement défini.   
 

### <a name="d-return-news-articles-with-related-tags"></a>D. Retourner des articles d’actualité avec les balises associées 

L’article et leurs balises sont séparés dans différentes tables. Développeur souhaite retourner une ligne par chaque article avec toutes les balises associées. Utilisation de la requête suivante : 
```tsql
SELECT a.articleId, title, STRING_AGG (tag, ',') as tags 
FROM dbo.Article AS a       
LEFT JOIN dbo.ArticleTag AS t 
    ON a.ArticleId = t.ArticleId 
GROUP BY a.articleId, title;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|ID article |title |tags |
|--- |--- |--- |
|172 |Interroge indique des résultats d’élection fermer |politique, sondages, ville Conseil | 
|176 |Nouveau bus attendu pour la réduction de la congestion |NULL |
|177 |Dogs continuent d’être plus répandue que chats |sondages, animaux| 

### <a name="e-generate-list-of-emails-per-towns"></a>E. Générer la liste des messages électroniques par villes

La requête suivante recherche les adresses de messagerie d’employés et les regroupe par villes : 
```tsql
SELECT town, STRING_AGG (email, ';') AS emails 
FROM dbo.Employee 
GROUP BY town; 
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Ville |messages électroniques |
|--- |--- |
|Seattle |syed0@adventure-works.com;catherine0@adventure-works.com;kim2@adventure-works.com |
|LA |sam1@adventure-works.com;hazem0@adventure-works.com |

Des messages électroniques retourné dans les colonne peut être utilisée directement à envoyer des e-mails à un groupe de personnes travaillant dans certaines villes particuliers les e-mails. 

### <a name="f-generate-a-sorted-list-of-emails-per-towns"></a>F. Générer une liste triée de messages électroniques par villes   
   
Similaire à l’exemple précédent, la requête suivante recherche les adresses de messagerie d’employés, les regroupe par ville puis trie les e-mails par ordre alphabétique :   
```tsql
SELECT town, 
    STRING_AGG (email, ';') WITHIN GROUP (ORDER BY email ASC) AS emails 
FROM dbo.Employee 
GROUP BY town; 
```
   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|Ville |messages électroniques |
|--- |--- |
|Seattle |catherine0@adventure-works.com;kim2@adventure-works.com;syed0@adventure-works.com |
|LA |hazem0@adventure-works.com;sam1@adventure-works.com |


## <a name="see-also"></a>Voir aussi  

[Fonctions de chaîne (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  


