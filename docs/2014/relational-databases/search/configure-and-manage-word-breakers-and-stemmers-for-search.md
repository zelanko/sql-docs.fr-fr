---
title: Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- full-text search [SQL Server], stemmers
- linguistic analysis [full-text search]
- full-text indexes [SQL Server], linguistic analysis
- full-text search [SQL Server], word breakers
- default full-text language option
- stemmers [full-text search]
- conjugating verbs [full-text search]
- word breakers [full-text search]
ms.assetid: d4bdd16b-a2db-4101-a946-583d1c674229
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: eaa80c71dcc58cbd780a664d2466a3bf3cec2a4c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011542"
---
# <a name="configure-and-manage-word-breakers-and-stemmers-for-search"></a>Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche
  Ils effectuent une analyse linguistique de l'ensemble des données indexées en texte intégral. Elle implique la recherche des limites de mots (coupure de mots) et la conjugaison des verbes (outil de conjugaison). Les analyseurs lexicaux et les générateurs de formes dérivées sont spécifiques à la langue, et les règles de l'analyse linguistique diffèrent selon les langues. Pour une langue donnée, un *analyseur lexical* identifie des mots individuels en déterminant l’emplacement des limites de mots d’après les règles lexicales de cette langue. Chaque mot (également appelé *jeton*) est inséré dans l’index de recherche en texte intégral dans une représentation compressée afin de réduire sa taille. Le *générateur de formes dérivées* génère des formes flexionnelles d’un mot particulier selon les règles spécifiques d’une langue (par exemple, « running », « ran » et « runner » constituent différentes formes du mot « run »).  
  
 L'utilisation d'analyseurs lexicaux spécifiques aux langues permet d'obtenir des termes plus précis pour chaque langue. Quand il existe un analyseur lexical pour une famille de langues, et non pour une sous-langue spécifique, la langue principale est utilisée. Par exemple, l'analyseur lexical en français gère le texte écrit en français canadien. Si aucun analyseur lexical n'est disponible pour une langue particulière, l'analyseur lexical en langue neutre est utilisé. Avec l'analyseur lexical en langue neutre, les mots sont décomposés en caractères neutres tels que des espaces et des signes de ponctuation.  
  
##  <a name="registering-word-breakers"></a><a name="register"></a>Inscription des analyseurs lexicaux  
 Pour utiliser les analyseurs lexicaux d'une langue, vous devez les inscrire. Pour les analyseurs lexicaux inscrits, les ressources linguistiques associées (générateurs de formes dérivées, mots parasites (mots vides) et fichiers de dictionnaire des synonymes) sont également disponibles pour les opérations d’indexation et d’interrogation de texte intégral. Pour consulter la liste des langues dont les analyseurs lexicaux sont actuellement inscrits auprès de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
 SELECT * FROM sys.fulltext_languages  
  
 Si vous ajoutez, supprimez ou modifiez un analyseur lexical, vous devez actualiser la liste des identificateurs de paramètres régionaux Microsoft Windows pris en charge pour l'indexation et les requêtes de texte intégral. Pour plus d’informations, consultez [Afficher ou modifier des filtres et des analyseurs lexicaux inscrits](view-or-change-registered-filters-and-word-breakers.md).  
  
##  <a name="setting-the-default-full-text-language-option"></a><a name="default"></a>Définition de l’option langue de texte intégral par défaut  
 Pour une version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d' `default full-text language` installation de définit l’option sur la langue du serveur s’il existe une correspondance appropriée. Pour une version non localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'anglais est la valeur affectée par défaut à l'option `default full-text language`.  
  
 Lorsque vous créez ou modifié un index de recherche en texte intégral, vous devez spécifier une langue différente pour chaque colonne indexée de texte intégral. Si aucune langue n'est spécifiée pour une colonne, la valeur par défaut est déterminée par l'option de configuration `default full-text language`.  
  
> [!NOTE]  
>  Toutes les colonnes répertoriées dans une clause de fonction de requête de texte intégral doivent utiliser la même langue, sauf si l'option LANGUAGE est spécifiée dans la requête. La langue utilisée pour la colonne d’index de recherche en texte intégral faisant l’objet d’une requête détermine l’analyse linguistique menée sur les arguments des prédicats de requête de texte intégral ([CONTAINS](/sql/t-sql/queries/contains-transact-sql) et [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)) et des fonctions de requête de texte intégral ([CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) et [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)).  
  
##  <a name="choosing-the-language-for-an-indexed-column"></a><a name="lang"></a>Choix de la langue d’une colonne indexée  
 Lors de la création d'un index de recherche en texte intégral, nous vous recommandons de spécifier une langue pour chaque colonne indexée. Si tel n'est pas le cas, la langue par défaut du système est utilisée. La langue d'une colonne détermine l'analyseur lexical et le générateur de formes dérivées utilisés pour indexer cette colonne. En outre, le fichier de dictionnaire des synonymes de cette langue est utilisé par les requêtes de texte intégral sur la colonne.  
  
 Plusieurs aspects doivent être pris en considération pour le choix de la langue d'une colonne lors de la création d'un index de recherche en texte intégral. Ces aspects sont liés à la façon dont les unités lexicales de votre texte sont créées et à la façon dont ce texte est ensuite indexé par le Moteur d'indexation et de recherche en texte intégral. Pour plus d’informations, consultez [Choisir une langue lors de la création d’un index de recherche en texte intégral](choose-a-language-when-creating-a-full-text-index.md).  
  
 **Pour afficher la langue de l'analyseur lexical d'une colonne**  
  
-   [Gérer les index de recherche en texte intégral](../indexes/indexes.md)  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="obtaining-information-about-word-breakers"></a><a name="info"></a>Obtention d’informations sur les analyseurs lexicaux  
 **Affichage du résultat de la segmentation du texte en unités lexicales d'une combinaison d'analyseur lexical, de dictionnaire des synonymes et de liste de mots vides**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).  
  
 **Pour retourner des informations sur les analyseurs lexicaux inscrits**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)  
  
##  <a name="troubleshooting-word-breaking-time-out-errors"></a><a name="tshoot"></a>Résolution des erreurs d’expiration de la césure des mots  
 Une erreur de délai d'attente lors de l'analyse lexicale peut se produire dans un grand nombre de situations. Pour plus d’informations sur ces situations et sur la façon de résoudre le problème correspondant, consultez [MSSQLSERVER_30053](../errors-events/mssqlserver-30053-database-engine-error.md).  
  
##  <a name="understanding-the-impact-of-new-word-breakers"></a><a name="impact"></a>Comprendre l’impact des nouveaux analyseurs lexicaux  
 Chaque version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut généralement de nouveaux analyseurs lexicaux qui possèdent de meilleures règles linguistiques et sont plus précis que les anciens analyseurs lexicaux. Les nouveaux analyseurs lexicaux peuvent se comporter légèrement différemment des analyseurs lexicaux dans les index de recherche en texte intégral qui ont été importés à partir de versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cela est significatif si un catalogue de texte intégral a été importé lorsqu'une base de données a été mise à niveau vers la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une ou plusieurs langues utilisées par les index de recherche en texte intégral dans le catalogue de texte intégral peuvent maintenant être associées aux nouveaux analyseurs lexicaux. Pour plus d’informations, consultez [Mise à niveau de la fonction de recherche en texte intégral](upgrade-full-text-search.md).  
  
 Pour obtenir une liste complète de tous les analyseurs lexicaux, consultez [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)   
 [sys. fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [Configurer et gérer mots vides et mots vides pour la recherche en texte intégral](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Mise à niveau de la fonction de recherche en texte intégral](upgrade-full-text-search.md)  
  
  
