---
title: "Configurer et g&#233;rer les analyseurs lexicaux et g&#233;n&#233;rateurs de formes d&#233;riv&#233;es pour la recherche | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langues [recherche en texte intégral]"
  - "recherche en texte intégral [SQL Server], générateurs de formes dérivées"
  - "analyse linguistique [recherche en texte intégral]"
  - "index de recherche en texte intégral [SQL Server], analyse linguistique"
  - "recherche en texte intégral [SQL Server], analyseurs lexicaux"
  - "option de langue de texte intégral par défaut"
  - "générateurs de formes dérivées [recherche en texte intégral]"
  - "conjugaison de verbes [recherche en texte intégral]"
  - "analyseurs lexicaux [recherche en texte intégral]"
ms.assetid: d4bdd16b-a2db-4101-a946-583d1c674229
caps.latest.revision: 89
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 88
---
# Configurer et g&#233;rer les analyseurs lexicaux et g&#233;n&#233;rateurs de formes d&#233;riv&#233;es pour la recherche
  Ils effectuent une analyse linguistique de l'ensemble des données indexées en texte intégral. Elle implique la recherche des limites de mots (coupure de mots) et la conjugaison des verbes (outil de conjugaison). Les analyseurs lexicaux et les générateurs de formes dérivées sont spécifiques à la langue, et les règles de l'analyse linguistique diffèrent selon les langues. Pour une langue donnée, un *analyseur lexical* identifie des mots individuels en déterminant l’emplacement des limites de mots d’après les règles lexicales de cette langue. Chaque mot (également appelé *jeton*) est inséré dans l’index de recherche en texte intégral dans une représentation compressée afin de réduire sa taille. Le *générateur de formes dérivées* génère des formes flexionnelles d’un mot particulier selon les règles spécifiques d’une langue (par exemple, « running », « ran » et « runner » constituent différentes formes du mot « run »).  
  
 L'utilisation d'analyseurs lexicaux spécifiques aux langues permet d'obtenir des termes plus précis pour chaque langue. Quand il existe un analyseur lexical pour une famille de langues, et non pour une sous-langue spécifique, la langue principale est utilisée. Par exemple, l'analyseur lexical en français gère le texte écrit en français canadien. Si aucun analyseur lexical n'est disponible pour une langue particulière, l'analyseur lexical en langue neutre est utilisé. Avec l'analyseur lexical en langue neutre, les mots sont décomposés en caractères neutres tels que des espaces et des signes de ponctuation.  
  
##  <a name="register"></a> Inscription d'analyseurs lexicaux  
 Pour utiliser les analyseurs lexicaux d'une langue, vous devez les inscrire. Pour les analyseurs lexicaux inscrits, les ressources linguistiques associées (générateurs de formes dérivées, mots parasites [mots vides] et fichiers de dictionnaire des synonymes) deviennent également disponibles pour des opérations d'indexation et d'interrogation de texte intégral. Pour consulter la liste des langues dont les analyseurs lexicaux sont actuellement inscrits auprès de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
 SELECT * FROM sys.fulltext_languages  
  
 Si vous ajoutez, supprimez ou modifiez un analyseur lexical, vous devez actualiser la liste des identificateurs de paramètres régionaux Microsoft Windows pris en charge pour l'indexation et les requêtes de texte intégral. Pour plus d’informations, consultez [View or Change Registered Filters and Word Breakers](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md).  
  
##  <a name="default"></a> Définition de l'option Langue de texte intégral par défaut  
 Dans le cas d’une version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit l’option **Langue de texte intégral par défaut** en fonction de la langue du serveur s’il existe une correspondance appropriée. Pour une version non localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’anglais est la **langue de texte intégral par défaut**.  
  
 Lorsque vous créez ou modifié un index de recherche en texte intégral, vous devez spécifier une langue différente pour chaque colonne indexée de texte intégral. Si aucune langue n’est spécifiée pour une colonne, la valeur par défaut est déterminée par l’option de configuration **Langue de texte intégral par défaut**.  
  
> [!NOTE]  
>  Toutes les colonnes répertoriées dans une clause de fonction de requête de texte intégral doivent utiliser la même langue, sauf si l'option LANGUAGE est spécifiée dans la requête. La langue utilisée pour la colonne d’index de recherche en texte intégral faisant l’objet d’une requête détermine l’analyse linguistique menée sur les arguments des prédicats de requête de texte intégral ([CONTAINS](../../t-sql/queries/contains-transact-sql.md) et [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)) et des fonctions de requête de texte intégral ([CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) et [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md)).  
  
##  <a name="lang"></a> Choix de la langue pour une colonne indexée  
 Lors de la création d'un index de recherche en texte intégral, nous vous recommandons de spécifier une langue pour chaque colonne indexée. Si tel n'est pas le cas, la langue par défaut du système est utilisée. La langue d'une colonne détermine l'analyseur lexical et le générateur de formes dérivées utilisés pour indexer cette colonne. En outre, le fichier de dictionnaire des synonymes de cette langue est utilisé par les requêtes de texte intégral sur la colonne.  
  
 Plusieurs aspects doivent être pris en considération pour le choix de la langue d'une colonne lors de la création d'un index de recherche en texte intégral. Ces aspects sont liés à la façon dont les unités lexicales de votre texte sont créées et à la façon dont ce texte est ensuite indexé par le Moteur d'indexation et de recherche en texte intégral. Pour plus d’informations, consultez [Choisir une langue lors de la création d’un index de recherche en texte intégral](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  
  
 **Pour afficher la langue de l'analyseur lexical d'une colonne**  
  
-   [Gérer les index de recherche en texte intégral](../Topic/Manage%20Full-Text%20Indexes.md)  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="info"></a> Obtention d'informations sur les analyseurs lexicaux  
 **Affichage du résultat de la segmentation du texte en unités lexicales d'une combinaison d'analyseur lexical, de dictionnaire des synonymes et de liste de mots vides**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md).  
  
 **Pour retourner des informations sur les analyseurs lexicaux inscrits**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
  
##  <a name="tshoot"></a> Dépannage des erreurs de délai d'attente de l'analyse lexicale  
 Une erreur de délai d'attente lors de l'analyse lexicale peut se produire dans un grand nombre de situations. Pour plus d’informations sur ces situations et sur la façon de résoudre le problème correspondant, consultez [MSSQLSERVER_30053](../Topic/MSSQLSERVER_30053.md).  
  
##  <a name="impact"></a> Comprendre l'impact de nouveaux analyseurs lexicaux  
 Chaque version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut généralement de nouveaux analyseurs lexicaux qui possèdent de meilleures règles linguistiques et sont plus précis que les anciens analyseurs lexicaux. Les nouveaux analyseurs lexicaux peuvent se comporter légèrement différemment des analyseurs lexicaux dans les index de recherche en texte intégral qui ont été importés à partir de versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cela est significatif si un catalogue de texte intégral a été importé lorsqu'une base de données a été mise à niveau vers la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une ou plusieurs langues utilisées par les index de recherche en texte intégral dans le catalogue de texte intégral peuvent maintenant être associées aux nouveaux analyseurs lexicaux. Pour plus d’informations, consultez [Mise à niveau de la fonction de recherche en texte intégral](../../relational-databases/search/upgrade-full-text-search.md).  
  
 Pour obtenir une liste complète de tous les analyseurs lexicaux, consultez [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
  
## Voir aussi  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)   
 [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Mise à niveau de la fonction de recherche en texte intégral](../../relational-databases/search/upgrade-full-text-search.md)  
  
  