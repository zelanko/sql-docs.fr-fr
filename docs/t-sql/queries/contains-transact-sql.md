---
title: CONTIENT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTAINS_TSQL
- CONTAINS
dev_langs: TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- CONTAINS predicate (Transact-SQL)
- conditions [SQL Server], CONTAINS
- fuzzy (less precise) word or phrase search [full-text search]
- word weighting values [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- LANGUAGE option
- word inflectionally generated from another [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- word near another word search [full-text search]
- full-text search [SQL Server], searching on a property
- proximity searches [full-text search]
- less precise (fuzzy) searches [full-text search]
- property searching [SQL Server], searching on a property
- inflectional forms [full-text search]
- prefix searches [full-text search]
ms.assetid: 996c72fc-b1ab-4c96-bd12-946be9c18f84
caps.latest.revision: "117"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 81b231ce95ae1b87bbda2f2fd786d12cb709e9fe
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="contains-transact-sql"></a>CONTAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Recherche des concordances précises ou approximatives (moins précises) avec des mots isolés ou des expressions, des termes situés à une certaine distance les uns des autres ou des concordances pondérées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. CONTAINS est un prédicat utilisé dans le [clause WHERE](../../t-sql/queries/where-transact-sql.md) d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] une instruction SELECT pour effectuer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche en texte intégral sur la recherche en texte intégral indexées colonnes contenant des types de données de type caractère.  
  
 CONTAINS peut rechercher :  
  
-   un mot ou une expression ;  
  
-   le préfixe d'un mot ou d'une expression ;  
  
-   un mot proche d'un autre mot ;  
  
-   un mot dérivant d'un autre mot par inflexion (par exemple, le radical « part » a généré par inflexion les formes dérivées partir, départ, partant ou partie) ;  
  
-   un mot synonyme d'un autre mot d'après un dictionnaire des synonymes (par exemple, le mot « métal » peut avoir des synonymes comme « aluminium » et « acier »).  
  
 Pour plus d’informations sur les formes de recherches en texte intégral qui sont prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [requête avec la recherche en texte intégral](../../relational-databases/search/query-with-full-text-search.md).  
 
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CONTAINS (   
     {   
        column_name | ( column_list )   
      | *   
      | PROPERTY ( { column_name }, 'property_name' )    
     }   
     , '<contains_search_condition>'  
     [ , LANGUAGE language_term ]  
   )   
  
<contains_search_condition> ::=   
  {   
      <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    | <weighted_term>   
    }   
  |   
    { ( <contains_search_condition> )   
        [ { <AND> | <AND NOT> | <OR> } ]   
        <contains_search_condition> [ ...n ]   
  }   
<simple_term> ::=   
     { word | "phrase" }  
  
<prefix term> ::=   
  { "word*" | "phrase*" }  
  
<generation_term> ::=   
  FORMSOF ( { INFLECTIONAL | THESAURUS } , <simple_term> [ ,...n ] )   
  
<generic_proximity_term> ::=   
  { <simple_term> | <prefix_term> } { { { NEAR | ~ }   
     { <simple_term> | <prefix_term> } } [ ...n ] }  
  
<custom_proximity_term> ::=   
  NEAR (   
     {  
        { <simple_term> | <prefix_term> } [ ,…n ]  
     |  
        ( { <simple_term> | <prefix_term> } [ ,…n ] )   
      [, <maximum_distance> [, <match_order> ] ]  
     }  
       )   
  
      <maximum_distance> ::= { integer | MAX }  
      <match_order> ::= { TRUE | FALSE }   
  
<weighted_term> ::=   
  ISABOUT   
   ( {   
        {   
          <simple_term>   
        | <prefix_term>   
        | <generation_term>   
        | <proximity_term>   
        }   
      [ WEIGHT ( weight_value ) ]   
      } [ ,...n ]   
   )   
  
<AND> ::=   
  { AND | & }  
  
<AND NOT> ::=   
  { AND NOT | &! }  
  
<OR> ::=   
  { OR | | }  
  
```  
  
## <a name="arguments"></a>Arguments  
 *column_name*  
 Nom d'une colonne d'index de recherche en texte intégral de la table spécifiée dans la clause FROM. Les colonnes peuvent être de type **char**, **varchar**, **nchar**, **nvarchar**, **texte**, **ntext**, **image**, **xml**, **varbinary**, ou **varbinary (max)**.  
  
 *column_list*  
 Spécifie deux colonnes ou plus, séparées par des virgules. *column_list* doit être mis entre parenthèses. À moins que *language_term* est spécifié, la langue de toutes les colonnes de *column_list* doivent être identiques.  
  
 \*  
 Indique que la requête recherche toutes les colonnes indexées en texte intégral dans la table spécifiée dans la clause FROM de la condition de recherche donnée. Les colonnes de la clause CONTAINS doivent provenir d'une table unique qui possède un index de recherche en texte intégral. À moins que *language_term* est spécifié, la langue de toutes les colonnes de la table doit être le même.  
  
 PROPRIÉTÉ ( *column_name* , '*property_name*')  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Spécifie une propriété du document sur laquelle rechercher la condition de recherche spécifiée.  
  
> [!IMPORTANT]  
>  Pour la requête retourne des lignes, *property_name* doit être spécifié dans la propriété de recherche liste de l’index de recherche en texte intégral et de l’index de recherche en texte intégral doit contenir des entrées spécifiques à la propriété pour *property_name*. Pour plus d’informations, consultez [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 LANGUAGE *language_term*  
 Est la langue à utiliser pour l’analyse lexicale, recherche de radical, les expansions du dictionnaire des synonymes et remplacements et parasites (ou [mot vide](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) dans le cadre de la requête. Ce paramètre est facultatif.  
  
 Si des documents de langues différentes sont stockés ensemble en tant qu'objets blob dans une colonne unique, l'identificateur de paramètres régionaux (LCID) d'un document donné détermine la langue à utiliser pour l'indexation de son contenu. Lorsque vous interrogez une telle colonne, spécification de langage *language_term* permet d’augmenter la probabilité d’une correspondance correcte.  
  
 *language_term* peut être spécifié comme une chaîne, entier ou valeur hexadécimale correspondant à l’identificateur LCID d’une langue. Si *language_term* est spécifié, la langue représentée est appliquée à tous les éléments de la condition de recherche. Si aucune valeur n'est définie, la langue du texte intégral de la colonne est utilisée.  
  
 Lorsque spécifié sous forme de chaîne, *language_term* correspond à la **alias** valeur de colonne dans le [sys.syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) affichage de compatibilité. La chaîne doit être entourée de guillemets simples, comme dans «*language_term*'. Lorsque spécifié en tant qu’entier, *language_term* est l’identificateur LCID réel qui identifie la langue. Lorsque spécifié en tant que valeur hexadécimale *language_term* est 0 x suivi de la valeur hexadécimale du LCID. La valeur hexadécimale ne doit pas dépasser huit caractères, y compris les zéros non significatifs.  
  
 Si la valeur est dans un format de caractères de deux octets (DBCS), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit en Unicode.  
  
 Si la langue spécifiée n'est pas valide ou si aucune ressource correspondant à cette langue n'est installée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une erreur. Pour utiliser les ressources de langue neutre, spécifiez 0 x 0 *language_term*.  
  
 \<*contains_search_condition*>  
 Spécifie le texte à rechercher dans *column_name* et les conditions pour une correspondance.  
  
*\<contains_search_condition >* est **nvarchar**. Une conversion implicite se produit lorsqu'un autre type de données character est utilisé comme entrée. Varchar (max) et nvarchar (max) types de données chaîne de grande taille ne peut pas être utilisés. Dans l'exemple suivant, la variable `@SearchWord`, à laquelle est attribuée la valeur `varchar(30)`, provoque une conversion implicite dans le prédicat `CONTAINS`.
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 Étant donné que « détection des paramètres » ne fonctionne pas lors de la conversion, utilisez **nvarchar** pour de meilleures performances. Dans l’exemple, déclarer `@SearchWord` comme `nvarchar(30)`.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 Vous pouvez également utiliser l'indicateur de requête OPTIMIZE FOR lorsqu'un plan non optimal est généré.  
  
 *word*  
 Chaîne de caractères sans espaces ni ponctuation.  
  
 *phrase*  
 Un ou plusieurs mots séparés par des espaces.  
  
> [!NOTE]  
>  Certaines langues, notamment certaines langues asiatiques, peuvent contenir des expressions composées d'un ou de plusieurs mots non séparés par des espaces.  
  
\<simple_term>  
Spécifie une correspondance pour un mot ou une expression exacts. Exemples de termes simples autorisés : « lieu dit », « lieudit » et « Microsoft SQL Server ». Les expressions doivent être mises entre des guillemets doubles (""). Mots d’une expression doivent apparaître dans l’ordre spécifié dans  *\<contains_search_condition >* telles qu’elles apparaissent dans la colonne de base de données. La recherche de caractères dans un mot ou une expression ne respecte pas la casse. Les mots parasites (ou [mots vides](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) (tels qu’un et, ou) dans les colonnes indexées en texte intégral ne sont pas stockées dans l’index de recherche en texte intégral. Si un mot parasite est utilisé dans la recherche d'un mot unique, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un message d'erreur indiquant que la requête contient uniquement des mots parasites. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient une liste standard des mots parasites dans le répertoire \Mssql\Binn\FTERef de chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La ponctuation est ignorée. Par conséquent, `CONTAINS(testing, "computer failure")` retourne la ligne ayant la valeur « Où est mon ordinateur (computer) ? Il est en panne (Failure). » Pour plus d’informations sur le comportement de séparateur de mots, consultez [configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
 \<prefix_term>  
 Précise une correspondance de mots ou d'expressions commençant par le texte spécifié. Placez un terme préfixe entre guillemets doubles (" ») et ajoutez un astérisque (\*) avant les guillemets doubles fermants afin que tout le texte commençant par le terme simple spécifié avant l’astérisque est mis en correspondance. La clause doit être définie de la manière suivante : `CONTAINS (column, '"text*"')`. L'astérisque correspond à aucun, à un ou à plusieurs caractères (du ou des mots racine dans le mot ou l'expression). Si le texte et l'astérisque ne sont pas délimités par des guillemets doubles, comme dans `CONTAINS (column, 'text*')`, la recherche en texte intégral considère l'astérisque comme un caractère et recherche les correspondances exactes avec `text*`. Le moteur de recherche en texte intégral ne trouvera pas de mots avec l’astérisque (\*) caractère car les analyseurs lexicaux ignorent en général ces caractères.  
  
 Lorsque  *\<prefix_term >* est une expression, chaque mot de l’expression est considéré comme un préfixe séparé. Ainsi, une recherche spécifiant le préfixe « contrôle des mots* » trouvera les lignes contenant le texte « contrôle des mots clés », « contrôleur des mots », etc.  
  
 \<generation_term>  
 Précise une correspondance de mots lorsque les termes simples qui s'y trouvent contiennent des variantes du mot initial à rechercher.  
  
 INFLECTIONAL  
 Spécifie que le générateur de formes dérivées dépendant de la langue doit être utilisé sur le terme simple spécifié. Le comportement du générateur de formes dérivées est défini en fonction des règles de racine de chaque langue spécifique. La langue neutre ne possède pas de générateur de formes dérivées associé. La langue des colonnes interrogées est utilisée pour se reporter au générateur de formes dérivées souhaité. Si *language_term* est spécifié, le Générateur de formes dérivées correspondant à cette langue est utilisé.  
  
 Une fonction  *\<simple_term >* au sein d’un  *\<generation_term >* ne correspondra pas à des noms et des verbes.  
  
 THESAURUS  
 Spécifie l'utilisation du dictionnaire des synonymes correspondant à la langue de texte intégral de la colonne ou à la langue spécifiée dans la requête. Le modèle ou les modèles à partir de la plus longue du  *\<simple_term >* sont mis en correspondance avec le dictionnaire des synonymes et conditions supplémentaires sont créées pour étendre ou remplacer le modèle d’origine. Si une correspondance est introuvable pour la totalité ou une partie de la  *\<simple_term >*, la partie de la mise en correspondance est traitée comme un *simple_term*. Pour plus d’informations sur le dictionnaire des synonymes de recherche en texte intégral, consultez [configurer et gérer les fichiers de dictionnaire des synonymes pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).  
  
 \<generic_proximity_term>  
 Spécifie une correspondance de mots ou d'expressions qui doit figurer dans le document faisant l'objet d'une recherche.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Nous vous recommandons d’utiliser \<custom_proximity_term >.  
  
 NEAR | ~  
 Indique que le mot ou l'expression qui se trouve de chaque côté de l'opérateur NEAR ou ~ doit figurer dans un document pour qu'une correspondance soit retournée. Vous devez spécifier deux termes de recherche. Un terme de recherche donné peut être un mot ou une expression qui est délimitée par des guillemets doubles («*expression*»).  
  
 Plusieurs termes de proximité peuvent être enchaînés, par exemple `a NEAR b NEAR c` ou `a ~ b ~ c`. Les termes de proximité enchaînés doivent tous figurer dans le document pour qu'une correspondance soit retournée.  
  
 Par exemple, `CONTAINS(*column_name*, 'fox NEAR chicken')` et `CONTAINSTABLE(*table_name*, *column_name*, 'fox ~ chicken')` retournent tous les documents de la colonne spécifiée qui contiennent à la fois « renard » et « poulet ». De plus, CONTAINSTABLE retourne un classement pour chaque document en fonction de la proximité de « renard » et de « poulet ». Par exemple, si un document contient la phrase, « Le renard a mangé le poulet », son classement serait élevé car les termes sont plus proches l'un de l'autre que dans d'autres documents.  
  
 Pour plus d’informations sur les termes de proximité générique, consultez [recherche de mots dans le voisinage d’autres mots avec NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<custom_proximity_term>  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
 Spécifie une correspondance de mots ou d'expressions, et la distance maximale éventuellement autorisée entre des termes de recherche. Vous pouvez également spécifier que les termes de recherche doivent être trouvés dans l’ordre exact dans lequel vous les spécifiez (\<match_order >).  
  
 Un terme de recherche donné peut être un mot ou une expression qui est délimitée par des guillemets doubles («*expression*»). Chaque terme spécifié doit figurer dans le document pour qu'une correspondance soit retournée. Vous devez spécifier au moins deux termes de recherche. Le nombre maximal de termes de recherche est de 64.  
  
 Par défaut, le terme de proximité personnalisée retourne toutes les lignes qui contiennent les termes spécifiés indépendamment de la distance qui les sépare et indépendamment de leur ordre. Par exemple, pour correspondre à la requête suivante, un document devrait simplement contenir `term1` et « `term3 term4` », peu importe leur place et leur ordre dans le document :  
  
```  
CONTAINS(column_name, 'NEAR(term1,"term3 term4")')  
```  
  
 Les paramètres facultatifs sont les suivants :  
  
 \<maximum_distance>  
 Spécifie la distance maximale autorisée entre les termes de recherche au début et à la fin d'une chaîne afin que cette chaîne soit considérée comme une correspondance.  
  
 *entier*  
 Spécifie un entier positif compris 0 et 4 294 967 295. Cette valeur contrôle le nombre de termes n'appartenant pas à la recherche pouvant se situer entre les premier et dernier termes de la recherche, à l'exclusion de tout autre terme de recherche spécifié supplémentaire.  
  
 Par exemple, la requête suivante recherche `AA` et `BB`, dans n’importe quel ordre, dans une distance maximale de cinq.  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB),5)')  
```  
  
 La chaîne `AA one two three four five BB` serait une correspondance. Dans l’exemple suivant, la requête spécifie trois termes de recherche, `AA`, `BB`, et `CC` dans une distance maximale de cinq :  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB,CC),5)')  
```  
  
 Cette requête correspondrait à la chaîne suivante, dans laquelle la distance totale est de cinq :  
  
 `BB   one two   CC   three four five A  A`  
  
 Notez que le terme, de recherche interne `CC`, n’est pas compté.  
  
 **MAX**  
 Retourne toutes les lignes qui contiennent les termes spécifiés indépendamment de la distance qui les sépare. Il s'agit du paramètre par défaut.  
  
 \<match_order>  
 Spécifie si les termes doivent apparaître dans l'ordre spécifié pour être retournés par une requête de recherche. Pour spécifier \<match_order >, vous devez également spécifier \<maximum_distance >.  
  
 \<match_order > prend l’une des valeurs suivantes :  
  
 **TRUE**  
 Impose l'ordre spécifié parmi les termes. Par exemple, `NEAR(A,B)` correspondrait uniquement à `A … B`.  
  
 **FALSE**  
 Ignore l'ordre spécifié. Par exemple, `NEAR(A,B)` correspondrait à la fois à `A … B` et à `B … A`.  
  
 Il s'agit du paramètre par défaut.  
  
 Par exemple, le terme de proximité suivant recherche les mots « `Monday` », « `Tuesday` » et « `Wednesday` » dans l'ordre spécifié, indépendamment de la distance qui les sépare :  
  
```  
CONTAINS(column_name, 'NEAR ((Monday, Tuesday, Wednesday), MAX, TRUE)')  
```  
  
 Pour plus d’informations sur l’utilisation de termes de proximité personnalisé, consultez [recherche de mots dans le voisinage d’autres mots avec NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<weighted_term>  
 Précise que les lignes retournées par la requête correspondent à une liste de mots ou d'expressions auxquels une valeur de pondération peut être affectée.  
  
 ISABOUT  
 Spécifie le  *\<weighted_term >* (mot clé).  
  
 WEIGHT(*weight_value*)  
 Définit une valeur de pondération qui est un nombre compris entre 0,0 et 1,0. Chaque composant de  *\<weighted_term >* peut inclure un *valeur_de_pondération*. *valeur_de_pondération* consiste à modifier les différentes parties d’une requête affectent la valeur de classement affectée à chaque ligne correspondant à la requête. POIDS n’affecte pas les résultats de requêtes CONTAINS, mais influe sur le classement dans [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) requêtes.  
  
> [!NOTE]  
>  Le séparateur de décimale est toujours un point, quels que soient les paramètres régionaux du système d'exploitation.  
  
 { AND | & } | { AND NOT | &! } | { OR | | }   
 Spécifie une opération logique entre deux conditions de recherche de contenu.  
  
 {ET | &}  
 Indique que les deux conditions de recherche de contenu doivent être satisfaites pour obtenir une correspondance. Le symbole et commercial (&) peut être utilisé à la place du mot clé AND pour représenter l'opérateur AND.  
  
 {ET NON | & ! }  
 Indique que la deuxième condition de recherche ne doit pas être satisfaite pour obtenir une correspondance. Le symbole et commercial suivi d'un point d'exclamation (&!) peut être utilisé à la place du mot clé AND NOT pour représenter l'opérateur AND NOT.  
  
 {OU ||}  
 Indique que l'une des deux conditions de recherche de contenu doit être satisfaite pour obtenir une correspondance. Le symbole de barre verticale (|) peut être utilisé à la place du mot clé OR pour représenter l'opérateur OR.  
  
 Lorsque  *\<contains_search_condition >* contient des groupes entre parenthèses, ces groupes sont évalués tout d’abord. Une fois ces groupes évalués, les règles suivantes sont appliquées lorsque ces opérateurs logiques sont utilisés dans les conditions de recherche de contenu :  
  
-   NOT est appliqué avant AND.  
  
-   NOT peut uniquement être utilisé après AND, comme dans AND NOT. L'opérateur OR NOT n'est pas autorisé. NOT ne peut pas être spécifié avant le premier terme. Par exemple, `CONTAINS (mycolumn, 'NOT "phrase_to_search_for" ' )` est incorrect.  
  
-   AND est appliqué avant OR.  
  
-   Les opérateurs booléens de même type (AND, OR) sont associatifs et peuvent donc être utilisés dans un ordre quelconque.  
  
 *n*  
 Espace réservé indiquant que plusieurs conditions de recherche CONTAINS peuvent être spécifiées, de même que plusieurs termes dans celles-ci.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Les prédicats et les fonctions de texte intégral s'appliquent à une table unique, ce qui est implicite dans le prédicat FROM. Pour effectuer des recherches sur plusieurs tables, utilisez une table jointe dans votre clause FROM afin de baser votre recherche sur un jeu de résultats qui est le produit de deux tables ou plus.  
  
 Prédicats de texte intégral ne sont pas autorisés dans les [clause OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) lorsque le niveau de compatibilité de base de données est défini à 100.  
  
## <a name="querying-remote-servers"></a>Interrogation de serveurs distants  
 Vous pouvez utiliser un nom en quatre parties dans le CONTAINS ou [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) prédicat de requête de recherche en texte intégral indexées colonnes des tables cibles sur un serveur lié. Pour préparer un serveur distant à recevoir des requêtes de texte intégral, créez un index de recherche en texte intégral sur les tables et colonnes cibles du serveur distant, puis ajoutez le serveur distant comme serveur lié.  
  
## <a name="comparison-of-like-to-full-text-search"></a>Comparaison de LIKE et de recherche en texte intégral  
 Contrairement à la recherche de texte intégral, le [comme](../../t-sql/language-elements/like-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] prédicat fonctionne sur les modèles de caractère uniquement. En outre, vous ne pouvez pas utiliser le prédicat LIKE pour interroger des données binaires mises en forme. De plus, une requête LIKE portant sur un important volume de données de texte non structurées est beaucoup plus lente qu'une requête de texte intégral équivalente exécutée sur les mêmes données. Une requête LIKE portant sur des millions de lignes de données de texte peut prendre plusieurs minutes pour retourner un résultat alors qu'une requête de texte intégral retourne en quelques secondes à peine le même résultat, en fonction du nombre de lignes retournées et de leur taille. Une autre considération à prendre en compte est que LIKE effectue uniquement une analyse de modèle simple d'une table entière. Par opposition, une requête de texte intégral est consciente de la langue et applique des transformations spécifiques au niveau de l'index et de l'heure de requête, telles que le filtrage de mots vides et l'ajout au dictionnaire des synonymes et aux formes fléchies. Ces transformations permettent aux requêtes de texte intégral d'améliorer le rappel et le dernier classement de leurs résultats.  
  
## <a name="querying-multiple-columns-full-text-search"></a>Interrogation de plusieurs colonnes (recherche en texte intégral)  
 Vous pouvez interroger plusieurs colonnes en spécifiant une liste de colonnes à rechercher. Les colonnes doivent être issues de la même table.  
  
 Par exemple, la requête CONTAINS suivante recherche le terme `Red` dans les `Name` et `Color` colonnes de la `Production.Product` table de la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données exemple.  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Name, Color   
FROM Production.Product  
WHERE CONTAINS((Name, Color), 'Red');  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-contains-with-simpleterm"></a>A. Utilisation de CONTAINS avec \<simple_term >  
 L'exemple ci-dessous recherche tous les produits qui contiennent le mot `$80.99` et qui coûtent `Mountain`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain');  
GO  
```  
  
### <a name="b-using-contains-and-phrase-with-simpleterm"></a>B. Utilisation de CONTAINS et une expression avec \<simple_term >  
 L'exemple ci-dessous retourne tous les produits qui contiennent l'expression `Mountain` ou `Road`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' Mountain OR Road ')  
GO  
```  
  
### <a name="c-using-contains-with-prefixterm"></a>C. Utilisation de CONTAINS avec \<prefix_term >  
 L'exemple ci-dessous retourne tous les noms de produits comportant au moins un mot commençant par la chaîne de préfixe dans la colonne `Name`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' "Chain*" ');  
GO  
```  
  
### <a name="d-using-contains-and-or-with-prefixterm"></a>D. Utilisation de CONTAINS et OR avec \<prefix_term >  
 L'exemple ci-dessous retourne toutes les descriptions de catégorie contenant les chaînes `chain` ou `full`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, '"chain*" OR "full*"');  
GO  
```  
  
### <a name="e-using-contains-with-proximityterm"></a>E. Utilisation de CONTAINS avec \<proximity_term >  
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 L’exemple suivant recherche le `Production.ProductReview` table pour tous les commentaires qui contiennent le mot `bike` au sein de 10 termes du mot «`control`» et dans l’ordre spécifié (autrement dit, où «`bike`« précède »`control`»).  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments , 'NEAR((bike,control), 10, TRUE)');  
GO  
```  
  
### <a name="f-using-contains-with-generationterm"></a>F. Utilisation de CONTAINS avec \<generation_term >  
 L'exemple ci-dessous recherche tous les produits comportant des formes dérivées du mot `ride` : riding, ridden, etc.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, ' FORMSOF (INFLECTIONAL, ride) ');  
GO  
```  
  
### <a name="g-using-contains-with-weightedterm"></a>G. Utilisation de CONTAINS avec \<weighted_term >  
 L'exemple ci-dessous recherche tous les noms de produits contenant les termes « `performance` », « `comfortable` » ou « `smooth` ». Une pondération différente est affectée à chacun des mots.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, 'ISABOUT (performance weight (.8),   
comfortable weight (.4), smooth weight (.2) )' );  
GO  
```  
  
### <a name="h-using-contains-with-variables"></a>H. Utilisation de CONTAINS avec des variables  
 L'exemple ci-dessous utilise une variable à la place d'un terme de recherche spécifique.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'Performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
GO  
```  
  
### <a name="i-using-contains-with-a-logical-operator-and"></a>I. Utilisation de CONTAINS avec un opérateur logique (AND)  
 L'exemple suivant utilise la table ProductDescription de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. La requête utilise le prédicat CONTAINS pour rechercher les descriptions dans lequel l’ID de description n’est pas égal à 5 et la description contient à la fois le mot `Aluminum` et le mot `spindle`. La condition de recherche utilise l'opérateur booléen AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'Aluminum AND spindle');  
GO  
```  
  
### <a name="j-using-contains-to-verify-a-row-insertion"></a>J. Utilisation de CONTAINS pour vérifier une insertion de ligne  
 L'exemple suivant utilise CONTAINS dans le cadre d'une sous-requête SELECT. À partir de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], la requête obtient la valeur de tous les commentaires de la table ProductReview pour un cycle particulier. La condition de recherche utilise l'opérateur booléen AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO Production.ProductReview   
  (ProductID, ReviewerName, EmailAddress, Rating, Comments)   
VALUES  
  (780, 'John Smith', 'john@fourthcoffee.com', 5,   
'The Mountain-200 Silver from AdventureWorks2008 Cycles meets and exceeds expectations. I enjoyed the smooth ride down the roads of Redmond');  
  
-- Given the full-text catalog for these tables is Adv_ft_ctlg,   
-- with change_tracking on so that the full-text indexes are updated automatically.  
WAITFOR DELAY '00:00:30';     
-- Wait 30 seconds to make sure that the full-text index gets updated.  
  
SELECT r.Comments, p.Name  
FROM Production.ProductReview AS r  
JOIN Production.Product AS p   
    ON r.ProductID = p.ProductID  
    AND r.ProductID = (SELECT ProductID  
FROM Production.ProductReview  
WHERE CONTAINS (Comments,   
    ' AdventureWorks2008 AND   
    Redmond AND   
    "Mountain-200 Silver" '));  
GO  
```  
  
### <a name="k-querying-on-a-document-property"></a>K. Interrogation sur une propriété de document  
  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 La requête suivante effectue une recherche sur une propriété indexée, `Title`, dans la colonne `Document` de la table `Production.Document`. La requête retourne uniquement les documents dont la propriété `Title` contient la chaîne `Maintenance` ou `Repair`.  
  
> [!NOTE]  
>  Pour qu'une recherche de propriété retourne des lignes, le ou les filtres qui analysent la colonne pendant l'indexation doivent extraire la propriété spécifiée. De même, l'index de recherche en texte intégral de la table spécifiée a dû être configuré afin d'inclure la propriété. Pour plus d’informations, consultez [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Document 
FROM Production.Document  
WHERE CONTAINS(PROPERTY(Document,'Title'), 'Maintenance OR Repair');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commencer à utiliser la recherche en texte intégral](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Créer et gérer des catalogues de texte intégral](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CRÉER le catalogue de texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Créer et gérer des index de recherche en texte intégral](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Requête avec la recherche en texte intégral](../../relational-databases/search/query-with-full-text-search.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Requête avec la recherche en texte intégral](../../relational-databases/search/query-with-full-text-search.md)   
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)   
 [Créer des requêtes de recherche en texte intégral &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)   
 [Rechercher les propriétés du document à l’aide des listes des propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
