---
title: FREETEXT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREETEXT
- FREETEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXT predicate (Transact-SQL)
- words in predicate [full-text search]
- column searches [full-text search]
ms.assetid: 2f199d3c-440e-4bcf-bdb5-82bb3994005d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6687946e13dd6c801fcd256a0e463bdacb3779f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="freetext-transact-sql"></a>FREETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Prédicat utilisé dans le [!INCLUDE[tsql](../../includes/tsql-md.md)] [clause WHERE](../../t-sql/queries/where-transact-sql.md) d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] une instruction SELECT pour effectuer une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recherche en texte intégral sur la recherche en texte intégral indexées colonnes contenant des types de données de type caractère. Ce prédicat recherche des valeurs qui correspondent à la signification, et non pas seulement au libellé exact des mots dans la condition de recherche. Lorsque FREETEXT est utilisé, le moteur de requête de recherche en texte intégral effectue en interne les actions suivantes sur le *chaîne_texte_libre*, affecte à chaque terme, un poids, puis recherche les correspondances :  
  
-   Il scinde la chaîne en mots en se basant sur les limites de mot (coupure de mots).  
  
-   Il génère des formes fléchies des mots (extraction de la racine).  
  
-   Il identifie une liste d'extensions ou de substituts en fonction des correspondances fournies par le dictionnaire des synonymes.  
  
> [!NOTE]  
>  Pour plus d’informations sur les formes de recherches en texte intégral qui sont prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [requête avec la recherche en texte intégral](../../relational-databases/search/query-with-full-text-search.md).  
  
**S'applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via la [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FREETEXT ( { column_name | (column_list) | * }   
          , 'freetext_string' [ , LANGUAGE language_term ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *column_name*  
 Nom d'une ou de plusieurs colonnes de texte intégral indexées de la table spécifiée dans la clause FROM. Les colonnes peuvent être de type **char**, **varchar**, **nchar**, **nvarchar**, **texte**, **ntext**, **image**, **xml**, **varbinary**, ou **varbinary (max)**.  
  
 *column_list*  
 Indique que plusieurs colonnes, délimitées par des virgules, peuvent être spécifiées. *column_list* doit être mis entre parenthèses. À moins que *language_term* est spécifié, la langue de toutes les colonnes de *column_list* doivent être identiques.  
  
 \*  
 Spécifie que toutes les colonnes qui ont été enregistrés pour la recherche en texte intégral doivent être utilisés pour rechercher la donnée *chaîne_texte_libre*. Si plusieurs tables se trouve dans la clause FROM, \* doit être qualifié par le nom de table. À moins que *language_term* est spécifié, la langue de toutes les colonnes de la table doit être le même.  
  
 *freetext_string*  
 Est du texte à rechercher dans le *column_name*. Tout texte, y compris des mots, expressions et phrases peuvent être entrés. Des correspondances sont générées si l'un des termes ou les formes de quelque terme que ce soit sont trouvés dans l'index de texte intégral.  
  
 Contrairement à CONTAINS et CONTAINSTABLE rechercher condition where et est un mot clé, lorsqu’il est utilisé dans *chaîne_texte_libre* le mot « et » est considéré comme un mot parasite, ou [mot vide](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)et seront ignorées.  
  
 L'utilisation de WEIGHT, de FORMSOF, de caractères génériques, de NEAR et d'autres syntaxes n'est pas autorisée. *chaîne_texte_libre* est découpée, traitées et transmises via le dictionnaire des synonymes.  
  
 *chaîne_texte_libre* est **nvarchar**. Une conversion implicite se produit lorsqu'un autre type de données character est utilisé comme entrée. Varchar (max) et nvarchar (max) types de données chaîne de grande taille ne peut pas être utilisés. Dans l'exemple suivant, la variable `@SearchWord`, à laquelle est attribuée la valeur `varchar(30)`, provoque une conversion implicite dans le prédicat `FREETEXT`.  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 Étant donné que « détection des paramètres » ne fonctionne pas lors de la conversion, utilisez **nvarchar** pour de meilleures performances. Dans l’exemple, déclarer `@SearchWord` comme `nvarchar(30)`.  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 Vous pouvez également utiliser l’indicateur de requête OPTIMIZE FOR pour les cas dans lequel un plan non optimal est généré.  
  
 LANGUAGE *language_term*  
 Langue dont les ressources seront utilisées pour l'analyse lexicale, la recherche de radical, l'utilisation du dictionnaire de synonymes et la suppression de mots vides dans la requête. Ce paramètre est facultatif et peut être spécifié sous la forme d'une chaîne, d'un entier ou d'une valeur hexadécimale correspondant à l'identificateur de paramètres régionaux (LCID) d'une langue. Si *language_term* est spécifié, la langue représentée est appliquée à tous les éléments de la condition de recherche. Si aucune valeur n'est définie, la langue du texte intégral de la colonne est utilisée.  
  
 Si des documents de langues différentes sont stockés ensemble en tant qu'objets blob dans une colonne unique, l'identificateur de paramètres régionaux (LCID) d'un document donné détermine la langue utilisée pour l'indexation de son contenu. Lorsque vous interrogez une telle colonne, en spécifiant *langage ** language_term* permet d’augmenter la probabilité d’une correspondance correcte.  
  
 Lorsque spécifié sous forme de chaîne, *language_term* correspond à la **alias** valeur de colonne dans il [sys.syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) affichage de compatibilité.  La chaîne doit être entourée de guillemets simples, comme dans «*language_term*'. Lorsque spécifié en tant qu’entier, *language_term* est l’identificateur LCID réel qui identifie la langue. Lorsque spécifié en tant que valeur hexadécimale *language_term* est 0 x suivi de la valeur hexadécimale du LCID. La valeur hexadécimale ne doit pas dépasser huit caractères, y compris les zéros non significatifs.  
  
 Si la valeur est dans un format de caractères de deux octets (DBCS), [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit en Unicode.  
  
 Si la langue spécifiée n’est pas valide ou il n’y a aucune ressource n’installées qui correspondent à cette langue, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie une erreur. Pour utiliser les ressources de langue neutre, spécifiez 0 x 0 *language_term*.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Les prédicats et les fonctions de texte intégral s'appliquent à une table unique, ce qui est implicite dans le prédicat FROM. Pour effectuer des recherches sur plusieurs tables, utilisez une table jointe dans votre clause FROM afin de baser votre recherche sur un jeu de résultats qui est le produit de deux tables ou plus.  
  
Les requêtes de texte intégral qui utilisent FREETEXT sont moins précises que celles qui utilisent CONTAINS. Le moteur de recherche en texte intégral de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifie les expressions et les mots importants. Aucune signification particulière est donnée à un des mots clés réservés ou des caractères génériques qui ont généralement un sens lorsque spécifié dans le \<contains_search_condition > paramètre du prédicat CONTAINS.
  
 Prédicats de texte intégral ne sont pas autorisés dans les [clause OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) lorsque le niveau de compatibilité de base de données est défini à 100.  
  
> [!NOTE]  
>  La fonction FREETEXTTABLE est utile pour les mêmes types de correspondance que le prédicat FREETEXT. Vous pouvez référencer cette fonction comme un nom de table classique dans le [à partir de la clause](../../t-sql/queries/from-transact-sql.md) d’une instruction SELECT. Pour plus d’informations, consultez [FREETEXTTABLE &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/freetexttable-transact-sql.md).  
  
## <a name="querying-remote-servers"></a>Interrogation de serveurs distants  
 Vous pouvez utiliser un nom en quatre parties dans le [CONTAINS](../../t-sql/queries/contains-transact-sql.md) ou prédicat FREETEXT pour interroger la recherche en texte intégral indexées colonnes des tables cibles sur un serveur lié. Pour préparer un serveur distant à recevoir des requêtes de texte intégral, créez un index de recherche en texte intégral sur les tables et colonnes cibles du serveur distant, puis ajoutez le serveur distant comme serveur lié.  
  
## <a name="comparison-of-like-to-full-text-search"></a>Comparaison de LIKE et de recherche en texte intégral  
 Contrairement à la recherche de texte intégral, le [comme](../../t-sql/language-elements/like-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] prédicat fonctionne sur les modèles de caractère uniquement. En outre, vous ne pouvez pas utiliser le prédicat LIKE pour interroger des données binaires mises en forme. De plus, une requête LIKE portant sur un important volume de données de texte non structurées est beaucoup plus lente qu'une requête de texte intégral équivalente exécutée sur les mêmes données. Une requête LIKE portant sur des millions de lignes de données de texte peut prendre plusieurs minutes pour retourner un résultat alors qu'une requête de texte intégral retourne en quelques secondes à peine le même résultat, en fonction du nombre de lignes retournées.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-freetext-to-search-for-words-containing-specified-character-values"></a>A. Utilisation de FREETEXT pour rechercher des mots contenant les valeurs de caractère spécifiées  
 L'exemple suivant recherche tous les documents contenant les mots liés à « vital », « safety » et « components ».  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components' );  
GO  
```  
  
### <a name="b-using-freetext-with-variables"></a>B. Utilisation de FREETEXT avec des variables  
 L'exemple ci-dessous utilise une variable à la place d'un terme de recherche spécifique.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30);  
SET @SearchWord = N'high-performance';  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commencer à utiliser la recherche en texte intégral](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Créer et gérer des catalogues de texte intégral](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CRÉER le catalogue de texte intégral &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Créer et gérer des index de recherche en texte intégral](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Requête avec la recherche en texte intégral](../../relational-databases/search/query-with-full-text-search.md)   
 [Créer des requêtes de recherche en texte intégral &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
