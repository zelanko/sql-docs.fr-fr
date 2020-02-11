---
title: Exécuter une requête avec une recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 280f4bc3c20fb65be24ace423f69982ad96bfbff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011110"
---
# <a name="query-with-full-text-search"></a>Exécuter une requête avec une recherche en texte intégral
  Pour définir des recherches en texte intégral, les requêtes de texte intégral de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent les prédicats de texte intégral (CONTAINS et FREETEXT) et les fonctions de texte intégral (CONTAINSTABLE et FREETEXTTABLE). Ces derniers prennent en charge la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] enrichie qui accepte divers formulaires de termes de requête. Pour écrire des requêtes de texte intégral, vous devez apprendre quand et comment utiliser ces prédicats et ces fonctions.  
  
##  <a name="OV_ft_predicates"></a>Vue d’ensemble des prédicats de texte intégral (CONTAINs et FREETEXT)  
 Les prédicats CONTAINS et FREETEXT retournent une valeur TRUE ou FALSE. Ils peuvent être utilisés uniquement pour spécifier des critères de sélection permettant de déterminer si une ligne donnée correspond à la requête de texte intégral. Les lignes correspondantes sont retournées dans le jeu de résultats. CONTAINS et FREETEXT sont spécifiés dans la clause WHERE ou HAVING d'une instruction SELECT. Ils peuvent être associés à l'un quelconque des autres prédicats [!INCLUDE[tsql](../../includes/tsql-md.md)] tels que LIKE et BETWEEN.  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe et les arguments de ces prédicats, consultez [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) et [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql).  
  
 Lorsque vous utilisez CONTAINS ou FREETEXT, vous pouvez spécifier une colonne unique, une liste de colonnes, ou toutes les colonnes de la table sur laquelle porte la recherche. Vous pouvez éventuellement spécifier la langue dont les ressources seront utilisées par une requête de texte intégral donnée pour l'analyse lexicale et la recherche de radical, les consultations de dictionnaire des synonymes et la suppression de mots parasites.  
  
 Les prédicats CONTAINS et FREETEXT sont utiles pour différents types de correspondance, comme expliqué ci-après.  
  
-   Utilisez CONTAINS (ou CONTAINSTABLE) pour des concordances précises ou approximatives (moins précises) avec des mots isolés ou des expressions, des répétitions ou des concordances pondérées. Lorsque vous utilisez CONTAINS, vous devez spécifier au moins une condition de recherche qui indique le texte que vous recherchez ainsi que les conditions qui déterminent les correspondances.  
  
     Vous pouvez utiliser une opération logique entre les conditions de recherche. Pour plus d’informations, consultez [utilisation des opérateurs booléens-and, or et not (dans Contains et CONTAINSTABLE)](#Using_Boolean_Operators), plus loin dans cette rubrique.  
  
-   Utilisez FREETEXT (ou FREETEXTTABLE) pour rechercher des correspondances de signification, et non pas le libellé exact, des mots, expressions ou phrases spécifiés ( *chaîne en texte libre*). Des correspondances sont générées si un terme ou une forme de quelque terme que ce soit est trouvé dans l'index de recherche en texte intégral d'une colonne spécifiée.  
  
 Vous pouvez utiliser un nom en quatre parties dans le prédicat CONTAINS ou FREETEXT pour interroger les colonnes indexées de texte intégral des tables cibles d'un serveur lié. Pour préparer un serveur distant à recevoir des requêtes de texte intégral, créez un index de recherche en texte intégral sur les tables et colonnes cibles du serveur distant, puis ajoutez le serveur distant comme serveur lié.  
  
> [!NOTE]  
>  Les prédicats de texte intégral ne sont pas autorisés dans la [clause OUTPUT](/sql/t-sql/queries/output-clause-transact-sql) lorsque le niveau de compatibilité de la base de données est défini sur 100.  
  
 
  
### <a name="examples"></a>Exemples  
  
#### <a name="a-using-contains-with-simple_term"></a>R. Utilisation de CONTAINS avec <simple_term>  
 L'exemple ci-dessous recherche tous les produits qui contiennent le mot `$80.99` et qui coûtent `"Mountain"`.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
#### <a name="b-using-freetext-to-search-for-words-containing-specified-character-values"></a>B. Utilisation de FREETEXT pour rechercher des mots contenant les valeurs de caractère spécifiées  
 L'exemple suivant recherche tous les documents contenant les mots liés à « vital », « safety » et « components ».  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```  
  
 
  
##  <a name="OV_ft_functions_CONTAINSTABLE_FREETEXTTABLE"></a>Vue d’ensemble des fonctions de texte intégral (CONTAINSTABLE et FREETEXTTABLE)  
 Les fonctions CONTAINSTABLE et FREETEXTTABLE sont référencées comme un nom de table régulier dans la clause FROM d'une instruction SELECT. Ils retournent une table contenant aucune, une ou plusieurs ligne(s) correspondant à la requête de texte intégral. La table retournée contient uniquement les lignes de la table de base qui correspondent aux critères de sélection spécifiés dans la condition de recherche en texte intégral de la fonction.  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe et les arguments de ces fonctions, consultez [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) et [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql).  
  
 Les requêtes utilisant l'une de ces fonctions retournent une valeur de classement de pertinence (RANK) et une clé de texte intégral (KEY) pour chaque ligne, comme suit :  
  
-   KEY (colonne)  
  
     La colonne KEY retourne les valeurs uniques des lignes retournées. La colonne KEY peut être utilisée pour spécifier des critères de sélection.  
  
-   RANK (colonne)  
  
     La colonne RANK retourne une *valeur de classement* pour chaque ligne qui indique le degré de correspondance de cette dernière avec les critères de sélection. Plus la valeur de classement du texte ou document d'une ligne est élevée, plus celle-ci est pertinente pour la requête de texte intégral. Notez que différentes lignes peuvent avoir le même classement. Vous pouvez limiter le nombre de correspondances à retourner en spécifiant le paramètre facultatif *top_n_by_rank* . Pour plus d’informations, consultez [Limiter les résultats de la recherche avec RANK](limit-search-results-with-rank.md).  
  
 Lorsque vous utilisez l'une ou l'autre de ces fonctions, vous devez spécifier la table de base sur laquelle doit porter la recherche en texte intégral. Comme avec les prédicats, vous pouvez spécifier une colonne unique, une liste de colonnes, ou toutes les colonnes de la table sur laquelle doit porter la recherche, et éventuellement, la langue dont les ressources seront utilisées par une requête de texte intégral donnée.  
  
 CONTAINSTABLE est utile pour les mêmes types de correspondance que CONTAINS, et FREETEXTTABLE est utile pour les mêmes types de correspondance que FREETEXT. Pour plus d’informations, consultez [Vue d’ensemble des prédicats de texte intégral (CONTAINS et FREETEXT)](#OV_ft_predicates), plus haut dans cette rubrique. Lors de l'exécution de requêtes utilisant les fonctions CONTAINSTABLE et FREETEXTTABLE, vous devez joindre de manière explicite les lignes retournées aux lignes de la table de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 En général, le résultat des fonctions CONTAINSTABLE ou FREETEXTTABLE doit être joint avec la table de base. Dans ce cas-là, vous devez connaître le nom de la colonne clé unique. Cette colonne, qui est présente dans toutes les tables activées pour la recherche en texte intégral, garantit l’unicité des lignes de la table (*colonne clé**unique*). Pour plus d’informations, consultez [Gérer les index de recherche en texte intégral](../indexes/indexes.md).  
  
 
  
### <a name="examples"></a>Exemples  
  
#### <a name="a-using-containstable"></a>R. Utilisation de CONTAINSTABLE  
 L'exemple suivant retourne l'ID de description et la description de tous les produits dont la colonne **Description** contient le mot « aluminum » à proximité du mot « light » ou du mot « lightweight ». Seules les lignes dont la valeur de classement est supérieure ou égale à 2 sont renvoyées.  
  
```  
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
  
#### <a name="b-using-freetexttable"></a>B. Utilisation de FREETEXTTABLE  
 L'exemple ci-après étend une requête FREETEXTTABLE afin de retourner en premier les lignes dont le niveau de classement est le plus élevé et d'ajouter le classement de chaque ligne à la liste de sélection. Pour spécifier la requête, vous devez savoir que **ProductDescriptionID** est la colonne clé unique de la `ProductDescription` table.  
  
```  
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
  
```  
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
  
 
  
##  <a name="Using_Boolean_Operators"></a>Utilisation d’opérateurs booléens-AND, OR et NOT-in CONTAINs et CONTAINSTABLE  
 Le prédicat CONTAINS et la fonction CONTAINSTABLE utilisent les mêmes conditions de recherche. Les deux prennent en charge la combinaison de plusieurs termes de recherche à l’aide d’opérateurs booléens (AND, OR et NOT) pour effectuer des opérations logiques. Par exemple, vous pouvez utiliser AND pour rechercher des lignes qui contiennent à la fois « latte » et « New York-style bagel ». Vous pouvez utiliser AND NOT pour rechercher les lignes qui contiennent « bagel » mais qui ne contiennent pas « cream cheese ».  
  
> [!NOTE]  
>  En revanche, FREETEXT et FREETEXTTABLE traitent les termes booléens comme des mots à rechercher.  
  
 Pour plus d’informations sur la façon de combiner CONTAINS avec d’autres prédicats qui utilisent les opérateurs logiques AND, OR et NOT, consultez [Condition de recherche &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant utilise la table ProductDescription de la base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] . La requête utilise le prédicat CONTAINS pour rechercher les descriptions dont l'ID de description n'est pas égal à 5 et la description contient les mots « Aluminum » et « spindle ». La condition de recherche utilise l'opérateur booléen AND.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
 
  
##  <a name="Additional_Considerations"></a>Considérations supplémentaires pour les requêtes de texte intégral  
 Lors de l'écriture de requêtes de texte intégral, prenez également en considération les points suivants :  
  
-   LANGUAGE (option)  
  
     De nombreux termes de requête dépendent fortement du comportement de l'analyseur lexical. Pour être certain d'utiliser l'analyseur lexical (et le générateur de formes dérivées) et le dictionnaire des synonymes appropriés, nous vous recommandons de spécifier l'option LANGUAGE. Pour plus d’informations, consultez [Choisir une langue lors de la création d’un index de recherche en texte intégral](choose-a-language-when-creating-a-full-text-index.md).  
  
-   Mots vides  
  
     Lorsqu'une requête de texte intégral est définie, le Moteur d'indexation et de recherche en texte intégral supprime les mots vides (également appelés mots parasites) des critères de recherche. Les mots vides sont des mots tels que « un », « et », « est » ou « le » dont les occurrences sont fréquentes mais qui ne sont pas utiles pour une recherche de texte spécifique. Les mots vides sont répertoriés dans une liste de mots vides. Chaque index de recherche en texte intégral est associé à une liste de mots vides spécifique, qui détermine les mots vides à omettre de la requête ou de l'index au moment de l'indexation. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](full-text-search.md).  
  
-   Dictionnaire des synonymes  
  
     Les requêtes FREETEXT et FREETEXTTABLE utilisent le dictionnaire des synonymes par défaut. CONTAINS et CONTAINSTABLE prennent en charge un argument THESAURUS facultatif.  
  
-   Respect de la casse  
  
     Les requêtes de recherche en texte intégral ne respectent pas la casse. Néanmoins, en ce qui concerne le Japonais, il existe plusieurs orthographes phonétiques pour lesquelles le concept de normalisation orthographique est apparenté au respect de la casse (par exemple kana = non respect). Ce genre de normalisation orthographique n'est pas pris en charge.  
  

  
##  <a name="varbinary"></a>Interrogation de colonnes varbinary (max) et XML  
 Si une colonne `varbinary(max)`, `varbinary` ou `xml` est indexée en texte intégral, elle peut faire l'objet d'une requête à l'aide des prédicats de texte intégral (CONTAINS et FREETEXT) et des fonctions de texte intégral (CONTAINSTABLE et FREETEXTTABLE), au même titre que n'importe quelle autre colonne indexée en texte intégral.  
  
> [!IMPORTANT]  
>  La recherche en texte intégral fonctionne également avec des colonnes de type image. Cependant, le type de données `image` sera supprimé dans une version ultérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser ce type de données dans un nouveau travail de développement et prévoyez de modifier les applications qui l'utilisent actuellement. Utilisez à la place le type de données `varbinary(max)`.  
  
### <a name="varbinarymax-or-varbinary-data"></a>Données varbinary(max) ou varbinary  
 Une même colonne `varbinary(max)` ou `varbinary` peut stocker de nombreux types de documents. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge tout type de document pour lequel un filtre est installé et disponible dans le système d'exploitation. Le type d'un document est identifié par l'extension de fichier de celui-ci. Par exemple, pour une extension de fichier .doc, la recherche en texte intégral utilise le filtre qui prend en charge les documents Microsoft Word. Pour obtenir la liste des types de documents disponibles, interrogez l’affichage catalogue [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) .  
  
 Notez que le Moteur d'indexation et de recherche en texte intégral peut bénéficier des filtres installés dans le système d'exploitation. Avant de pouvoir utiliser des filtres de système d'exploitation, des analyseurs lexicaux et des générateurs de formes dérivées, vous devez les charger dans l'instance de serveur, comme suit :  
  
```  
EXEC sp_fulltext_service @action='load_os_resources', @value=1  
```  
  
 Pour créer un index de recherche en texte intégral sur une colonne `varbinary(max)`, le Moteur d'indexation et de recherche en texte intégral a besoin d'accéder aux extensions de fichier des documents dans la colonne `varbinary(max)`. Ces informations doivent être stockées dans une colonne de table, appelée colonne de type, qui doit être associée à la colonne `varbinary(max)` dans l'index de recherche en texte intégral. Lors de l'indexation d'un document, le Moteur d'indexation et de recherche en texte intégral utilise l'extension de fichier indiquée dans la colonne de type pour identifier le filtre à utiliser.  
  
 
  
### <a name="xml-data"></a>Données xml  
 Une colonne de type de données `xml` stocke uniquement des documents et des fragments XML, et seul le filtre XML est utilisé pour les documents. Par conséquent, une colonne de type est inutile. Sur les colonnes `xml`, l'index de recherche en texte intégral indexe le contenu des éléments XML, sans prendre en compte les balises XML. Les valeurs d'attributs sont indexées en texte intégral, à moins qu'il ne s'agisse de valeurs numériques. Des balises d'éléments sont utilisées comme limites de jeton. Les fragments et les documents XML ou HTML correctement formés contenant plusieurs langues sont pris en charge.  
  
 Pour plus d’informations sur l’interrogation `xml` d’une colonne, consultez [utiliser la recherche en texte intégral avec des colonnes XML](../xml/use-full-text-search-with-xml-columns.md).  
  
 
  
##  <a name="supported"></a>Formes de termes de requête prises en charge  
 Cette section récapitule la prise en charge fournie pour chaque formulaire de requête par les prédicats de texte intégral et les fonctions d'ensemble de lignes.  
  
> [!NOTE]  
>  Pour connaître la syntaxe d’un terme de requête donné, cliquez sur les liens correspondants dans la colonne **Pris en charge par** du tableau suivant.  
  
|Formulaire de terme de la requête|Description|Pris en charge par|  
|----------------------|-----------------|------------------|  
|Un ou plusieurs mots ou expressions spécifiques (*terme simple*)|Dans une recherche en texte intégral, un mot (ou *jeton*) est une chaîne dont les limites sont identifiées par les analyseurs lexicaux appropriés, qui suivent les règles linguistiques de la langue spécifiée. Une expression valide est constituée de plusieurs mots, avec ou sans signes de ponctuation entre eux.<br /><br /> Par exemple, « croissant » est un mot et «CAF ?? le lait est une expression. De tels mots et expressions sont considérés comme des termes simples.<br /><br /> Pour plus d’informations, consultez [Recherche d’un mot ou d’une expression spécifique (terme simple)](#Simple_Term), dans la suite de cette rubrique.|[Contains](/sql/t-sql/queries/contains-transact-sql) et [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) recherchent une correspondance exacte pour l’expression.<br /><br /> [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) et [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) découpent l’expression en mots distincts.|  
|Un mot ou une expression commençant par un texte spécifié (*préfixe*)|Un terme de préfixe fait référence à une chaîne apposée au devant d'un mot pour produire un mot dérivatif ou une forme fléchie.<br /><br /> Pour un terme de préfixe unique, tout mot qui démarre avec le terme spécifié fera partie du jeu de résultats. Par exemple, le terme « auto* » correspond à « automatique », « automobile », etc.<br /><br /> Dans le cas d'une expression, chaque mot faisant partie de l'expression est considéré comme un terme préfixe. Par exemple, le terme « auto tran\*» correspond à « automatic transmission » et « automobile transducer » mais pas à « automatic motor transmission ».<br /><br /> Pour plus d’informations, consultez [Recherche de préfixes (terme de préfixe)](#Prefix_Term), dans la suite de cette rubrique.|[Contains](/sql/t-sql/queries/contains-transact-sql) et [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
|Formes fléchies d’un mot spécifique (*génération de termes de génération*)|Les formes fléchies correspondent aux différents temps et conjugaisons d'un verbe ou au pluriel et au singulier d'un non. Par exemple, rechercher les formes fléchies du verbe « drive ». Si plusieurs lignes de la table comportent les mots « drive », « drives », « drove », « driving » et « driven », tous ces termes apparaîtront dans le jeu de résultats, dans la mesure où chacun d'entre eux peut être généré à partir du mot « drive ».<br /><br /> Pour plus d’informations, consultez [Recherche de formes fléchies d’un mot spécifique (forme canonique)](#Inflectional_Generation_Term), dans la suite de cette rubrique.|[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) et [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) recherchent par défaut des termes fléchis de tous les mots spécifiés.<br /><br /> [Contains](/sql/t-sql/queries/contains-transact-sql) et [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) prennent en charge un argument fléchial facultatif.|  
|Formes synonymes d’un mot spécifique (*terme de génération-Thésaurus*)|Un dictionnaire des synonymes définit des synonymes spécifiés par l'utilisateur pour les termes. Par exemple, si une entrée « {car, automobile, truck, van} » est ajoutée à un dictionnaire des synonymes, vous pouvez rechercher la forme du dictionnaire des synonymes pour le mot « car ». Toutes les lignes de la table interrogée qui contiennent les mots « automobile », « truck », « van » ou « car » s'affichent dans le jeu de résultats, car chacun de ces mots appartient au jeu d'expansion des synonymes contenant le mot « car ».<br /><br /> Pour plus d’informations sur la structure des fichiers de dictionnaire des synonymes, consultez [Configurer et gérer les fichiers de dictionnaire des synonymes pour la recherche en texte intégral](configure-and-manage-thesaurus-files-for-full-text-search.md).|[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) et [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) utilisent le dictionnaire des synonymes par défaut.<br /><br /> [Contains](/sql/t-sql/queries/contains-transact-sql) et [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) prennent en charge un argument thesaurus facultatif.|  
|Un mot ou une expression proches d’un autre mot ou d’une autre expression (*terme de proximité*)|Un terme de proximité indique des mots ou expressions qui sont proches les uns des autres. Vous pouvez également spécifier le nombre maximal de termes n'entrant pas dans le cadre de la recherche qui séparent le premier et le dernier termes de recherche. De plus, vous pouvez rechercher des mots ou des expressions dans n'importe quel ordre, ou dans l'ordre dans lequel vous les spécifiez.<br /><br /> Par exemple, vous pouvez rechercher les lignes dans lesquelles le mot « ice » est voisin du mot « hockey » et celles dans lesquelles l'expression « ice skating » est voisine de « ice hockey ».<br /><br /> Pour plus d’informations, consultez [Recherche de mots dans le voisinage d’autres mots avec NEAR](search-for-words-close-to-another-word-with-near.md).|[Contains](/sql/t-sql/queries/contains-transact-sql) et [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
|Mots ou expressions utilisant des valeurs pondérées (*termes pondérés*)|Une valeur pondérée indique le degré d'importance de chaque mot et expression au sein d'un ensemble de mots et d'expressions. L'échelle de valeurs oscille entre un minimum de 0,0 et un maximum de 1,0.<br /><br /> Par exemple, dans une requête de recherche de plusieurs termes, vous pouvez affecter à chaque mot de recherche une valeur de pondération indiquant son importance par rapport aux autres mots figurant dans la condition de recherche. Les résultats de ce type de requête renvoient les lignes les plus pertinentes en premier, en fonction du poids relatif affecté aux mots de recherche. Les jeux de résultats contiennent des documents ou des lignes qui contiennent chacun des termes spécifiés (ou contenu entre eux) ; toutefois, certains résultats seront considérés comme plus pertinents que d'autres à cause de la variation dans les valeurs pondérées associées aux différents termes recherchés.<br /><br /> Pour plus d’informations, consultez [Recherche de mots et d’expressions à l’aide de valeurs pondérées (termes pondérés)](#Weighted_Term), dans la suite de cette rubrique.|[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
  

  
###  <a name="Simple_Term"></a>Recherche d’un mot ou d’une expression spécifique (terme simple)  
 Vous pouvez utiliser [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)ou [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) pour rechercher une expression spécifique dans une table. Par exemple, si vous souhaitez effectuer une recherche dans la table `ProductReview` de la base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] afin de trouver tous les commentaires de produits contenant l'expression « learning curve », vous pouvez utiliser le prédicat CONTAINS en procédant comme suit :  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 La condition de recherche, en l'occurrence « learning curve », peut être complexe et comporter un ou plusieurs termes.  
  
 
  
###  <a name="Prefix_Term"></a>Réalisation de recherches de préfixes (terme de préfixe)  
 Vous pouvez utiliser [CONTAINS](/sql/t-sql/queries/contains-transact-sql) ou [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) pour rechercher des mots ou des expressions ayant un préfixe que vous spécifiez. Toutes les entrées de la colonne qui contiennent le texte commençant par le préfixe spécifié sont retournées. Par exemple, rechercher toutes les lignes qui contiennent le préfixe `top`-, comme dans `top``ple`, `top``ping`et `top`. La requête ressemble à ceci :  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 Tout texte correspondant au texte spécifié avant l'astérisque (*) est renvoyé. Si le texte et l'astérisque ne sont pas délimités par des guillemets doubles, comme dans `CONTAINS (DESCRIPTION, 'top*')`, la recherche en texte intégral ne considère pas l'astérisque comme un caractère générique.  
  
 Lorsque le préfixe est une expression, chaque jeton à l'intérieur de l'expression est considéré comme un préfixe distinct. Toutes les lignes qui possèdent des mots qui commencent par les préfixes seront renvoyés. Par exemple, le préfixe « light bread* » trouve des lignes contenant le texte « light breaded », « lightly breaded » ou « light bread », mais il ne retourne pas « lightly toasted bread ».  
  
 
  
###  <a name="Inflectional_Generation_Term"></a>Recherche de formes fléchies d’un mot spécifique (terme de génération)  
 Vous pouvez utiliser [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)ou [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) pour rechercher tous les différents temps et conjugaisons d’un verbe, le pluriel et le singulier d’un nom (recherche des formes fléchies) ou les formes synonymes d’un mot spécifique (recherche dans le dictionnaire des synonymes).  
  
 L'exemple suivant recherche toutes les formes de « foot » (« foot », « feet », etc.) dans la colonne `Comments` de la table `ProductReview` dans la base de données `AdventureWorks` .  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
> [!NOTE]  
>  La recherche en texte intégral utilise des générateurs de formes dérivées, qui vous permettent de rechercher les différents temps et conjugaisons d'un verbe, ou à la fois le pluriel et le singulier d'un nom. Pour plus d’informations sur les générateurs de formes dérivées, consultez [Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche](configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  

  
###  <a name="Weighted_Term"></a>Recherche de mots ou d’expressions à l’aide de valeurs pondérées (termes pondérés)  
 Vous pouvez utiliser [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) pour rechercher des mots ou des expressions et spécifier une valeur pondérée. La pondération d'un terme, qui est une mesure numérique comprise entre 0.0 et 1.0, indique l'importance de chaque mot et expression au sein d'un ensemble de mots et d'expressions. L'échelle de pondération oscille entre un minimum de 0.0 et un maximum de 1.0.  
  
 L'exemple suivant affiche une requête qui recherche toutes les adresses de client à l'aide de pondérations, où tout texte qui commence par la chaîne « Bay » comporte soit « Street » soit « View ». Les résultats accordent un rang plus élevé aux lignes qui contiennent le plus de mots, parmi ceux spécifiés.  
  
```  
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
  

  
##  <a name="tokens"></a>Affichage du résultat de la création de jetons d’une combinaison d’analyseur lexical, de dictionnaire des synonymes et de la STOPLIST  
 Après avoir appliqué une combinaison d’analyseur lexical, de dictionnaire des synonymes et de liste de mots vides à une entrée de chaîne de requête, vous pouvez afficher le résultat de la segmentation du texte en unités lexicales à l’aide de la vue de gestion dynamique **sys.dm_fts_parser**. Pour plus d’informations, consultez [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).  
  
 
  
## <a name="see-also"></a>Voir aussi  
 [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)   
 [Créer des requêtes de recherche en texte intégral &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)   
 [Améliorer les performances des requêtes de texte intégral](improve-the-performance-of-full-text-queries.md)  
  
  
