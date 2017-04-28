---
title: "Exécuter une requête avec une recherche en texte intégral | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
caps.latest.revision: 80
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5034ce123455c63718fb41b02450c14ca2f68a0b
ms.lasthandoff: 04/11/2017

---
# <a name="query-with-full-text-search"></a>Exécuter une requête avec une recherche en texte intégral

Écrivez des requêtes de texte intégral en utilisant les prédicats de texte intégral **CONTAINS** et **FREETEXT**, ainsi que les fonctions d’ensemble de lignes **CONTAINSTABLE** et **FREETEXTTABLE** avec l’instruction **SELECT**. Cette rubrique fournit des exemples de chaque prédicat et de chaque fonction et vous aide à choisir le meilleur à utiliser.

-   Utilisez **CONTAINS** et **CONTAINSTABLE** pour mettre en correspondance des mots et des expressions.
-   Utilisez **FREETEXT** et **FREETEXTTABLE** pour mettre en correspondance la signification, mais pas le libellé exact.

## <a name="examples_simple"></a> Exemples simples des différents prédicats et fonctions

### <a name="example---contains"></a>Exemple – CONTAINS  
 L'exemple ci-dessous recherche tous les produits qui contiennent le mot `$80.99` et qui coûtent `"Mountain"`.  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
### <a name="example---freetext"></a>Exemple – FREETEXT 
 L’exemple suivant recherche tous les documents qui contiennent des mots liés à « vital », « safety » et « components ».  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```

### <a name="example---containstable"></a>Exemple – CONTAINSTABLE  
 L'exemple suivant retourne l'ID de description et la description de tous les produits dont la colonne **Description** contient le mot « aluminum » à proximité du mot « light » ou du mot « lightweight ». Seules les lignes dont la valeur de classement est supérieure ou égale à 2 sont renvoyées.  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
### <a name="example--freetexttable"></a>Exemple – FREETEXTTABLE  
 L'exemple ci-après étend une requête FREETEXTTABLE afin de retourner en premier les lignes dont le niveau de classement est le plus élevé et d'ajouter le classement de chaque ligne à la liste de sélection. Pour spécifier la requête, il faut savoir que **ProductDescriptionID** est la colonne clé unique de la table **ProductDescription** .  
  
```tsql 
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
Voici l'extension de la même requête qui renvoie uniquement les lignes avec une valeur de rang égale ou supérieure à 10 :  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  

## <a name="pick-the-best-predicate-or-function"></a>Choisir le meilleur prédicat ou la meilleure fonction

`CONTAINS`/`CONTAINSTABLE` et `FREETEXT`/`FREETEXTTABLE` sont utiles pour différents types de mise en correspondance. Le tableau ci-dessous vous aide à choisir le meilleur prédicat ou la meilleure fonction pour votre requête.

Pour obtenir des exemples, consultez [Exemples simples des différents prédicats et fonctions](#examples_simple) et [Exemples de types spécifiques de recherche](#examples_specific). Consultez également [Éléments pouvant faire l’objet d’une recherche](#supported).

| |CONTAINS/CONTAINSTABLE|FREETEXT/FREETEXTTABLE|
|---|---|---|
|**Type de requête**|Recherchez des correspondances exactes ou approximatives (moins précises) de mots et d’expressions.|Recherchez des correspondances de signification, et non pas du libellé exact, des mots, expressions ou phrases spécifiés (*chaîne en texte libre*).<br/><br/>Des correspondances sont générées si un terme ou une forme de quelque terme que ce soit est trouvé dans l'index de recherche en texte intégral d'une colonne spécifiée.|
|**Autres options de requête**|Vous pouvez spécifier la proximité de mots à une certaine distance les uns des autres.<br/><br/>Vous pouvez retourner des correspondances pondérées.<br/><br/>Vous pouvez utiliser une opération logique pour combiner les conditions de recherche. Pour plus d’informations, consultez [Utilisation des opérateurs booléens (AND, OR et NOT)](#Using_Boolean_Operators) plus loin dans cette rubrique.|N/a|

## <a name="compare-predicates-and-functions"></a>Comparer des prédicats et des fonctions

Les prédicats `CONTAINS` / `FREETEXT` et les fonctions d’ensemble de lignes `CONTAINSTABLE`/`FREETEXTTABLE` ont une syntaxe et des options différentes. Le tableau ci-dessous vous aide à choisir le meilleur prédicat ou la meilleure fonction pour votre requête.

Pour obtenir des exemples, consultez [Exemples simples des différents prédicats et fonctions](#examples_simple) et [Exemples de types spécifiques de recherche](#examples_specific). Consultez également [Éléments pouvant faire l’objet d’une recherche](#supported).

| |Prédicats<br/>CONTAINS/FREETEXT|Fonctions<br/>CONTAINSTABLE/FREETEXTTABLE|
|---|---|---|
|**Utilisation**|Utilisez les **prédicats** de texte intégral CONTAINS et FREETEXT dans la clause WHERE ou HAVING d’une instruction SELECT.|Utilisez les **fonctions** de texte intégral CONTAINSTABLE et FREETEXTTABLE comme un nom de table standard dans la clause FROM d’une instruction SELECT.|
|**Autres options de requête**|Vous pouvez les combiner à l’un quelconque des autres prédicats [!INCLUDE[tsql](../../includes/tsql-md.md)], tel que LIKE et BETWEEN.<br/><br/>Vous pouvez spécifier une colonne unique, une liste de colonnes ou toutes les colonnes de la table sur laquelle porte la recherche.<br/><br/>Vous pouvez éventuellement spécifier la langue dont les ressources seront utilisées par la requête de texte intégral pour l’analyse lexicale et la recherche de radical, les consultations de dictionnaire des synonymes et la suppression de mots parasites.|Vous devez spécifier la table de base à rechercher lorsque vous utilisez l’une de ces fonctions. Comme avec les prédicats, vous pouvez spécifier une colonne unique, une liste de colonnes, ou toutes les colonnes de la table sur laquelle doit porter la recherche, et éventuellement, la langue dont les ressources seront utilisées par une requête de texte intégral donnée.<br/><br/>En général, vous devez joindre les résultats des fonctions CONTAINSTABLE ou FREETEXTTABLE avec la table de base. Pour cela, vous devez connaître le nom de la colonne clé unique. Cette colonne, qui est présente dans toutes les tables activées pour la recherche en texte intégral, garantit l’unicité des lignes de la table ( *colonne clé**unique*). Pour plus d’informations sur la colonne clé, consultez [Créer et gérer des index de recherche en texte intégral](../../relational-databases/search/create-and-manage-full-text-indexes.md).|
|**Résultats**|Les prédicats CONTAINS et FREETEXT retournent une valeur TRUE ou FALSE qui indique si une ligne donnée correspond à la requête de texte intégral. Les lignes correspondantes sont retournées dans le jeu de résultats.|Ces fonctions retournent une table contenant zéro, une ou plusieurs lignes correspondant à la requête de texte intégral. La table retournée contient uniquement les lignes de la table de base qui correspondent aux critères de sélection spécifiés dans la condition de recherche en texte intégral de la fonction.<br/><br/>Les requêtes qui utilisent l’une de ces fonctions retournent également une valeur de classement de pertinence (RANK) et une clé de texte intégral (KEY) pour chaque ligne retournée, comme suit :<br/><ul><li>Colonne **KEY**. La colonne KEY retourne les valeurs uniques des lignes retournées. La colonne KEY peut être utilisée pour spécifier des critères de sélection.</li><li>Colonne **RANK**. La colonne RANK retourne une *valeur de classement* pour chaque ligne qui indique le degré de correspondance de cette dernière avec les critères de sélection. Plus la valeur de classement du texte ou document d'une ligne est élevée, plus celle-ci est pertinente pour la requête de texte intégral. Notez que différentes lignes peuvent avoir le même classement. Vous pouvez limiter le nombre de correspondances à retourner en spécifiant le paramètre facultatif *top_n_by_rank* . Pour plus d’informations, consultez [Limiter les résultats de la recherche avec RANK](../../relational-databases/search/limit-search-results-with-rank.md).</li></ul>|
|**Options supplémentaires**|Vous pouvez utiliser un nom en quatre parties dans le prédicat CONTAINS ou FREETEXT pour interroger les colonnes indexées de texte intégral des tables cibles d'un serveur lié. Pour préparer un serveur distant à recevoir des requêtes de texte intégral, créez un index de recherche en texte intégral sur les tables et colonnes cibles du serveur distant, puis ajoutez le serveur distant comme serveur lié.|N/a|
|**En savoir plus**|Pour plus d’informations sur la syntaxe et les arguments de ces prédicats, consultez [CONTAINS](../../t-sql/queries/contains-transact-sql.md) et [FREETEXT](../../t-sql/queries/freetext-transact-sql.md).|Pour plus d’informations sur la syntaxe et les arguments de ces fonctions, consultez [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) et [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md).|

##  <a name="supported"></a> Éléments pouvant faire l’objet d’une recherche

Le tableau ci-dessous décrit les types de mots et d’expressions que vous pouvez rechercher.
  
|Formulaire de terme de la requête|Description|Pris en charge par|  
|----------------------|-----------------|------------------|  
|Un ou plusieurs mots ou expressions spécifiques<br/>(*terme simple*)|Par exemple, « croissant » constitue un mot et « café au lait » une expression. De tels mots et expressions sont considérés comme des termes simples.<br /><br /> Dans une recherche en texte intégral, un *mot* (ou *jeton*) est une chaîne dont les limites sont identifiées par les analyseurs lexicaux appropriés, qui suivent les règles linguistiques de la langue spécifiée. Une *expression* valide est constituée de plusieurs mots, avec ou sans signes de ponctuation entre eux.<br /><br /> Pour plus d’informations, consultez [Recherche d’un mot ou d’une expression spécifique (terme simple)](#Simple_Term), dans la suite de cette rubrique.|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) et [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) recherchent une correspondance exacte pour l'expression.<br /><br /> [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) et [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) décomposent l'expression en mots distincts.|  
|Un mot ou une expression commençant par un texte spécifié<br/>(*terme de préfixe*)|Pour un terme de préfixe unique, tout mot qui démarre avec le terme spécifié fera partie du jeu de résultats. Par exemple, le terme « auto* » correspond à « automatique », « automobile », etc.<br /><br /> Dans le cas d'une expression, chaque mot faisant partie de l'expression est considéré comme un terme préfixe. Par exemple, le terme « auto tran\*» correspond à « automatic transmission » et « automobile transducer » mais pas à « automatic motor transmission ».<br /><br /> Un *terme de préfixe* fait référence à une chaîne apposée au devant d’un mot pour produire un mot dérivatif ou une forme fléchie.<br /><br /> Pour plus d’informations, consultez [Recherche de préfixes (terme de préfixe)](#Prefix_Term), dans la suite de cette rubrique.|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) et [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  
|Les formes fléchies d’un mot spécifique<br/>(*forme canonique - fléchie*)|Par exemple, rechercher les formes fléchies du verbe « drive ». Si plusieurs lignes de la table comportent les mots « drive », « drives », « drove », « driving » et « driven », tous ces termes apparaîtront dans le jeu de résultats, dans la mesure où chacun d'entre eux peut être généré à partir du mot « drive ».<br /><br /> Les *formes fléchies* correspondent aux différents temps et conjugaisons d’un verbe et au pluriel et au singulier d’un nom. <br /><br /> Pour plus d’informations, consultez [Recherche de formes fléchies d’un mot spécifique (forme canonique)](#Inflectional_Generation_Term), dans la suite de cette rubrique.|[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) et [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) recherchent par défaut des termes fléchis de tous les mots spécifiés.<br /><br /> [CONTAINS](../../t-sql/queries/contains-transact-sql.md) et [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) prennent en charge un argument INFLECTIONAL facultatif.|  
|Les formes synonymes d’un mot spécifique<br/>(*forme canonique - dictionnaire des synonymes*)|Par exemple, si une entrée « {car, automobile, truck, van} » est ajoutée à un dictionnaire des synonymes, vous pouvez rechercher la forme du dictionnaire des synonymes pour le mot « car ». Toutes les lignes de la table interrogée qui contiennent les mots « automobile », « truck », « van » ou « car » s'affichent dans le jeu de résultats, car chacun de ces mots appartient au jeu d'expansion des synonymes contenant le mot « car ».<br /><br />Un *dictionnaire des synonymes* définit des synonymes spécifiés par l’utilisateur pour les termes.<br /><br />  Pour plus d’informations sur la structure des fichiers de dictionnaire des synonymes, consultez [Configurer et gérer les fichiers de dictionnaire des synonymes pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).|[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) et [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) utilisent le dictionnaire des synonymes par défaut.<br /><br /> [CONTAINS](../../t-sql/queries/contains-transact-sql.md) et [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) prennent en charge un argument THESAURUS facultatif.|  
|Un mot ou une expression proche d’un autre mot ou d’une autre expression<br/>(*terme de proximité*)|Par exemple, vous pouvez rechercher les lignes dans lesquelles le mot « ice » est voisin du mot « hockey » et celles dans lesquelles l'expression « ice skating » est voisine de « ice hockey ».<br /><br /> Un *terme de proximité* indique des mots ou des expressions proches les uns des autres. Vous pouvez également spécifier le nombre maximal de termes n’entrant pas dans le cadre de la recherche qui séparent le premier et le dernier termes de recherche. De plus, vous pouvez rechercher des mots ou des expressions dans n'importe quel ordre, ou dans l'ordre dans lequel vous les spécifiez.<br /><br /> Pour plus d’informations, consultez [Recherche de mots dans le voisinage d’autres mots avec NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) et [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  
|Mots ou expressions utilisant des valeurs pondérées<br/>(*terme pondéré*)|Par exemple, dans une requête de recherche de plusieurs termes, vous pouvez affecter à chaque mot de recherche une valeur de pondération indiquant son importance par rapport aux autres mots figurant dans la condition de recherche. Les résultats de ce type de requête renvoient les lignes les plus pertinentes en premier, en fonction du poids relatif affecté aux mots de recherche. Les jeux de résultats contiennent des documents ou des lignes qui contiennent chacun des termes spécifiés (ou contenu entre eux) ; toutefois, certains résultats seront considérés comme plus pertinents que d'autres à cause de la variation dans les valeurs pondérées associées aux différents termes recherchés.<br /><br /> Une *valeur pondérée* indique le degré d’importance de chaque mot ou expression au sein d’un ensemble de mots ou d’expressions. L'échelle de valeurs oscille entre un minimum de 0,0 et un maximum de 1,0.<br /><br /> Pour plus d’informations, consultez [Recherche de mots et d’expressions à l’aide de valeurs pondérées (termes pondérés)](#Weighted_Term), dans la suite de cette rubrique.|[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  

## <a name="examples_specific"></a> Exemples de types spécifiques de recherche

###  <a name="Simple_Term"></a> Recherche d’un mot ou d’une expression spécifique (terme simple)  
 Vous pouvez utiliser [CONTAINS](../../t-sql/queries/contains-transact-sql.md), [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md), [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)ou [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) pour rechercher une expression spécifique dans une table. Par exemple, si vous souhaitez effectuer une recherche dans la table **ProductReview** de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] afin de trouver tous les commentaires de produits contenant l’expression « learning curve », vous pouvez utiliser le prédicat CONTAINS en procédant comme suit :  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 La condition de recherche, en l’occurrence « learning curve », peut être complexe et comporter un ou plusieurs termes.  
  
###  <a name="Prefix_Term"></a> Recherche d’un mot avec un préfixe (terme de préfixe)  
 Vous pouvez utiliser [CONTAINS](../../t-sql/queries/contains-transact-sql.md) ou [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) pour rechercher des mots ou des expressions ayant un préfixe que vous spécifiez. Toutes les entrées de la colonne qui contiennent le texte commençant par le préfixe spécifié sont retournées. Par exemple, rechercher toutes les lignes qui contiennent le préfixe `top`-, comme dans `top``ple`, `top``ping`et `top`. La requête est la suivante :  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 Tout texte correspondant au texte spécifié avant l'astérisque (*) est renvoyé. Si le texte et l'astérisque ne sont pas délimités par des guillemets doubles, comme dans `CONTAINS (DESCRIPTION, 'top*')`, la recherche en texte intégral ne considère pas l'astérisque comme un caractère générique.  
  
 Lorsque le préfixe est une expression, chaque jeton à l'intérieur de l'expression est considéré comme un préfixe distinct. Toutes les lignes qui possèdent des mots qui commencent par les préfixes seront renvoyés. Par exemple, le préfixe « light bread* » trouve des lignes contenant le texte « light breaded », « lightly breaded » ou « light bread », mais il ne retourne pas « lightly toasted bread ».  
  
###  <a name="Inflectional_Generation_Term"></a> Recherche de formes fléchies d’un mot spécifique (forme canonique)  
Vous pouvez utiliser [CONTAINS](../../t-sql/queries/contains-transact-sql.md), [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md), [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)ou [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) pour rechercher tous les différents temps et conjugaisons d’un verbe, le pluriel et le singulier d’un nom (recherche des formes fléchies) ou les formes synonymes d’un mot spécifique (recherche dans le dictionnaire des synonymes).  
  
L'exemple suivant recherche toutes les formes de « foot » (« foot », « feet », etc.) dans la colonne `Comments` de la table `ProductReview` dans la base de données `AdventureWorks` .  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
La recherche en texte intégral utilise des *générateurs de formes dérivées*, qui vous permettent de rechercher les différents temps et conjugaisons d’un verbe, ou à la fois le pluriel et le singulier d’un nom. Pour plus d’informations sur les générateurs de formes dérivées, consultez [Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
   
###  <a name="Weighted_Term"></a> Recherche de mots et d’expressions à l’aide de valeurs pondérées (termes pondérés)  
Vous pouvez utiliser [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) pour rechercher des mots ou des expressions et spécifier une valeur pondérée. La pondération d'un terme, qui est une mesure numérique comprise entre 0.0 et 1.0, indique l'importance de chaque mot et expression au sein d'un ensemble de mots et d'expressions. L'échelle de pondération oscille entre un minimum de 0.0 et un maximum de 1.0.  
  
L'exemple suivant affiche une requête qui recherche toutes les adresses de client à l'aide de pondérations, où tout texte qui commence par la chaîne « Bay » comporte soit « Street » soit « View ». Les résultats accordent un rang plus élevé aux lignes qui contiennent le plus de mots, parmi ceux spécifiés.  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 Un terme pondéré peut être utilisé avec tout terme simple, terme de préfixe, terme canonique ou terme de proximité.  

##  <a name="Using_Boolean_Operators"></a> Utiliser les opérateurs booléens (AND, OR et NOT)
 
Le prédicat CONTAINS et la fonction CONTAINSTABLE utilisent les mêmes conditions de recherche. Ils permettent tous les deux de combiner plusieurs termes à rechercher via les opérateurs booléens (AND, OR et NOT), pour effectuer des opérations logiques. Par exemple, vous pouvez utiliser AND pour rechercher des lignes qui contiennent à la fois « latte » et « New York-style bagel ». Vous pouvez utiliser AND NOT pour rechercher les lignes qui contiennent « bagel » mais qui ne contiennent pas « cream cheese ».  
  
En revanche, FREETEXT et FREETEXTTABLE traitent les termes booléens comme des mots à rechercher.  
  
 Pour plus d’informations sur la façon de combiner CONTAINS avec d’autres prédicats qui utilisent les opérateurs logiques AND, OR et NOT, consultez [Condition de recherche &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise le prédicat CONTAINS pour rechercher les descriptions dont l’ID de description n’est pas égal à 5 et la description contient les mots « Aluminum » et « spindle ». La condition de recherche utilise l'opérateur booléen AND. Cet exemple utilise la table ProductDescription de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
##  <a name="Additional_Considerations"></a> Autres options de requête

 Lorsque vous écrivez des requêtes de texte intégral, vous pouvez également spécifier les options suivantes.
  
-   **Langue**, avec l’option **LANGUAGE**. De nombreux termes de requête dépendent fortement du comportement de l'analyseur lexical. Pour être certain d'utiliser l'analyseur lexical (et le générateur de formes dérivées) et le dictionnaire des synonymes appropriés, nous vous recommandons de spécifier l'option LANGUAGE. Pour plus d’informations, consultez [Choisir une langue lors de la création d’un index de recherche en texte intégral](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  

-   **Respect de la casse**. Les requêtes de recherche en texte intégral ne respectent pas la casse. Néanmoins, en ce qui concerne le Japonais, il existe plusieurs orthographes phonétiques pour lesquelles le concept de normalisation orthographique est apparenté au respect de la casse (par exemple kana = non respect). Ce genre de normalisation orthographique n'est pas pris en charge.  

-   **Mots vides**. Lorsqu'une requête de texte intégral est définie, le Moteur d'indexation et de recherche en texte intégral supprime les mots vides (également appelés mots parasites) des critères de recherche. Les mots vides sont des mots tels que « un », « et », « est » ou « le » dont les occurrences sont fréquentes mais qui ne sont pas utiles pour une recherche de texte spécifique. Les mots vides sont répertoriés dans une liste de mots vides. Chaque index de recherche en texte intégral est associé à une liste de mots vides spécifique, qui détermine les mots vides à omettre de la requête ou de l'index au moment de l'indexation. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
-   **Dictionnaire des synonymes**. Les requêtes FREETEXT et FREETEXTTABLE utilisent le dictionnaire des synonymes par défaut. CONTAINS et CONTAINSTABLE prennent en charge un argument THESAURUS facultatif. Pour plus d’informations, consultez [Configurer et gérer les fichiers de dictionnaire des synonymes pour la recherche en texte intégral](configure-and-manage-thesaurus-files-for-full-text-search.md).
  
##  <a name="tokens"></a> Vérifier les résultats de la création de jetons

Après avoir appliqué une combinaison d’analyseur lexical, de dictionnaire des synonymes et de liste de mots vides dans une requête, vous pouvez afficher les résultats de la création de jetons à l’aide de la vue de gestion dynamique **sys.dm_fts_parser**. Pour plus d’informations, consultez [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Créer des requêtes de recherche en texte intégral &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [Améliorer les performances des requêtes de texte intégral](../../relational-databases/search/improve-the-performance-of-full-text-queries.md)
 
