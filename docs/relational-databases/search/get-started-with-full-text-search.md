---
title: "Commencer &#224; utiliser la recherche en texte int&#233;gral | Microsoft Docs"
ms.date: "08/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "catalogues de texte intégral [SQL Server], création"
  - "index de texte intégral [SQL Server], création"
  - "recherche en texte intégral [SQL Server], à propos de"
  - "recherche en texte intégral [SQL Server], configuration"
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
caps.latest.revision: 76
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 72
---
# Commencer &#224; utiliser la recherche en texte int&#233;gral
La recherche en texte intégral prend en charge plusieurs langues par le biais de l’utilisation des *composants linguistiques* suivants : analyseurs lexicaux et générateurs de formes dérivées, listes de mots vides qui contiennent des mots vides (également appelés mots parasites) et fichiers de dictionnaire des synonymes. Les fichiers de dictionnaire des synonymes et, dans certains cas, les listes de mots vides, doivent être configurés par un administrateur de base de données. Un fichier de dictionnaire des synonymes donné prend en charge tous les index de recherche en texte intégral qui utilisent la langue correspondante, et une liste de mots vides donnée peut être associée à autant d'index de recherche en texte intégral que nécessaire.  
 
Les bases de données SQL Server sont activées en texte intégral par défaut, mais vous devez dans un premier temps [créer un catalogue en texte intégral](https://msdn.microsoft.com/library/bb326035.aspx), puis créer un index en texte intégral sur les tables ou les vues indexées dans lesquelles vous souhaitez effectuer votre recherche.
 
 ## Instructions pas à pas 
 
 Accédez à la rubrique [Utiliser l’Assistant Indexation de texte intégral](https://msdn.microsoft.com/library/ms180091.aspx) si vous souhaitez bénéficier des instructions pas à pas.

Cette rubrique traite des considérations, des exemples et des liens vers d’autres pages.
##  <a name="configure"></a> Planifier votre configuration

Il existe 2 étapes de base pour configurer les colonnes de tables pour une recherche en texte intégral dans une base de données :  
  
- Création d'un catalogue de texte intégral.  
  
- Créez un index de texte intégral sur les tables ou les vues indexées dans lesquelles vous souhaitez effectuer votre recherche. 

     Un index de recherche en texte intégral est un type spécial d’index fonctionnel par jeton qui est construit et géré par le Moteur de recherche en texte intégral. Pour que la création d'une recherche en texte intégral soit possible sur une table ou une vue, celles-ci doivent avoir un index unique ne comportant qu'une seule colonne et n'acceptant pas les valeurs Null. Le Moteur d'indexation et de recherche en texte intégral utilise cet index unique pour mapper chaque ligne de la table à une clé compressible unique. Un index de recherche en texte intégral peut inclure des colonnes **char**, **varchar**, **nchar**, **nvarchar**, **texte**, **ntext**, **image**, **xml**, **varbinary** et **varbinary (max)**. Pour plus d’informations, consultez [Créer et gérer des index de recherche en texte intégral](../../relational-databases/search/create-and-manage-full-text-indexes.md).   
  
     Chaque index de recherche en texte intégral doit appartenir à un catalogue de texte intégral. Vous pouvez créer un catalogue de texte séparé pour chaque index de recherche en texte intégral ou associer plusieurs index de recherche en texte intégral à un catalogue donné. Un catalogue de texte intégral est un objet virtuel qui n'appartient à aucun groupe de fichiers. Le catalogue est un concept logique qui fait référence à un groupe d'index de recherche en texte intégral.  
  

 Différences entre les index en recherche intégral et les index standard SQL Server :  
  
|Index de texte intégral|Index SQL Server classiques|  
|------------------------|--------------------------------|  
|Un seul index de recherche en texte intégral est autorisé par table.|Plusieurs index classiques sont autorisés par table.|  
|L’ajout de données aux index de recherche en texte intégral, opération que l’on appelle *remplissage*, doit être demandé soit dans le cadre de la planification, soit par le biais d’une requête spécifique, ou peut intervenir automatiquement lors de l’ajout de nouvelles données.|Sont mis à jour automatiquement lorsque les données sur lesquelles ils sont fondés sont modifiées, mises à jour ou supprimées.|  
|Sont groupés à l'intérieur d'une même base de données dans un ou plusieurs catalogues de texte intégral.|Ne sont pas groupés.|  
    
##  <a name="options"></a> Options  
  
### Langage de colonne  
 Pour plus d’informations sur la sélection du langage de colonne, consultez la section [Choisir une langue lors de la création d’un index de recherche en texte intégral](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  
  
### Choisir un groupe de fichiers pour une recherche en texte intégral  
 Le processus de création d'un index de recherche en texte intégral est une opération assez intensive en matière d'entrées/sorties (à haut niveau, elle consiste à lire les données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis à propager les données filtrées vers l'index de recherche en texte intégral). Comme meilleure pratique recommandée, localisez un index de recherche en texte intégral dans le groupe de fichiers de base de données qui convient le mieux pour optimiser les performances d'E/S ou localisez les index de recherche en texte intégral dans un groupe de fichiers différent sur un autre volume.  
  
 Nous vous recommandons de stocker les données de tables et les catalogues associés de texte intégral dans le même groupe de fichiers. Quelquefois, pour des raisons de performance, vous pouvez souhaiter avoir les données de table et l’index de recherche en texte intégral dans des groupes de fichiers différents stockés sur des volumes différents afin d’optimiser le parallélisme d’E/S.  

  
### Affecter l’index en recherche intégral   
 
 Nous vous recommandons d'associer les tables ayant les mêmes caractéristiques de mise à jour (par exemple avec peu de modifications ou, au contraire, beaucoup de modifications, ou les tables fréquemment modifiées à un moment donné de la journée) dans le même catalogue de texte intégral. Cette manière de configurer la planification du remplissage du catalogue de texte intégral permet d'assurer la synchronisation perpétuelle des index de texte intégral et des tables, sans nuire à l'utilisation des ressources du serveur de base de données pendant les périodes de forte activité.  
  
 Respectez les consignes suivantes :  
  
-   Sélectionnez systématiquement le plus petit index unique disponible comme clé unique de texte intégral Il s'agira idéalement d'un index de quatre octets, basé sur des entiers. Cela réduit considérablement la quantité de ressources requise par la service Recherche de [!INCLUDE[msCoName](../../includes/msconame-md.md)] dans le système de fichiers. Si la clé primaire est volumineuse (plus de 100 octets), pensez à choisir un autre index unique pour la table (ou créez-le) comme clé unique de texte intégral. Dans le cas contraire, si la taille de la clé unique de texte intégral dépasse la taille maximale autorisée (900 octets), le remplissage de texte intégral est impossible.  
  
-   Si vous indexez une table avec des millions de lignes, affectez la table sur son propre catalogue en recherche intégrale.  
  
-   Prenez en compte la quantité de modifications apparaissant dans les tables soumises à l’indexation de texte intégral ainsi que le nombre total de lignes concernées dans ces tables. Si le nombre total de lignes modifiées, auquel s’ajoute le nombre de lignes de table présentes au cours du dernier remplissage de texte intégral, s’élève à plusieurs millions, affectez la table à un catalogue de texte intégral qui lui est propre.  

  
### Associer une liste de mots vides   
  Une *liste de mots vides* est une liste contenant des mots vides, également appelés mots parasites. Une liste de mots vides est associée à chaque index de recherche en texte intégral, et les mots contenus dans cette liste de mots vides s'appliquent aux requêtes de texte intégral sur cet index. Par défaut, la liste de mots vides système est associée à un nouvel index de recherche en texte intégral. Vous pouvez créer et utiliser votre propre liste de mots vides. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
 Par exemple, l’instruction [CREATE FULLTEXT STOPLIST](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] suivante crée une liste de mots vides de texte intégral nommée myStoplist3 en copiant la liste de mots vides système :  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 L’instruction [ALTER FULLTEXT STOPLIST](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] suivante modifie une liste de mots vides nommée myStoplist en ajoutant le mot « en » (d’abord pour l’espagnol, puis pour le français) :  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
    
## Mettre à jour un index  
 À l'instar des index [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] classiques, les index de recherche en texte intégral peuvent être automatiquement mis à jour à mesure que les données sont modifiées dans les tables associées. Il s'agit du comportement par défaut. Vous pouvez, également, garder manuellement vos index de recherche en texte intégral à jour ou à intervalles planifiés spécifiés. L'alimentation d'un index de recherche en texte intégral peut être exigeante en termes de temps et de ressources ; par conséquent, la mise à jour de l'index est effectuée habituellement en mode de processus asynchrone qui s'exécute en arrière-plan et conserve l'index de recherche en texte intégral à jour après les modifications opérées dans la table de base. 
 
 La mise à jour immédiate d'un index de recherche en texte intégral après chaque modification dans la table de base peut être gourmande en ressources. Par conséquent, si vous avez un taux de mise à jour/insertion/suppression très élevé, vous pouvez constater une baisse dans les performances des requêtes. Si cela se produit, pensez à planifier de temps à autre des mises à jour manuelles du suivi des modifications afin de ne pas perdre trace des nombreuses modifications, au lieu de mettre des requêtes en concurrence pour les ressources.  
  
 Pour analyser l’état du remplissage, utilisez les fonctions FULLTEXTCATALOGPROPERTY ou OBJECTPROPERTYEX. Pour connaître l'état du remplissage du catalogue, exécutez l'instruction suivante :  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 En règle générale, si un remplissage complet est en cours, le résultat retourné est 1.  
 

##  <a name="example"></a> Exemple : Configurer une recherche en texte intégral  
 L'exemple en deux parties ci-dessous crée un catalogue de texte intégral nommé `AdvWksDocFTCat` sur la base de données AdventureWorks, puis crée un index de recherche en texte intégral sur la table `Document` dans [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Cette instruction permet de créer le catalogue de texte intégral dans le répertoire par défaut spécifié durant l'installation. Le dossier nommé `AdvWksDocFTCat` se trouve dans le répertoire par défaut.  
  
1.  Pour créer un catalogue de texte intégral nommé `AdvWksDocFTCat`, l’exemple utilise une instruction [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md) :  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  Avant de créer un index de recherche en texte intégral sur la table Document, assurez-vous que la table dispose d'un index unique qui n'accepte pas les valeurs NULL et ne comporte qu'une seule colonne. L’instruction [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) suivante crée un index unique, `ui_ukDoc`, sur la colonne DocumentID de la table Document :  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  Une fois que vous avez une clé unique, vous pouvez créer un index de recherche en texte intégral sur la table `Document` en utilisant l’instruction [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     Le paramètre TYPE COLUMN défini dans cet exemple spécifie la colonne de type dans la table qui contient le type du document dans chaque ligne de la colonne Document (lequel est de type binaire). La colonne de type stocke l'extension de fichier fournie par l'utilisateur (.doc, .xls, etc.) du document dans une ligne donnée. Le moteur d'indexation et de recherche en texte intégral utilise l'extension de fichier dans une ligne donnée afin d'appeler le filtre approprié pour l'analyse des données de cette ligne. Une fois que le filtre a analysé les données binaires de la ligne, l'analyseur lexical spécifié analyse le contenu (dans cet exemple, c'est l'analyseur lexical pour l'anglais britannique qui est utilisé). Notez que le processus de filtrage se produit uniquement au moment de l'indexation ou si un utilisateur insère ou met à jour une colonne dans la table de base alors que le suivi automatique des modifications est activé pour l'index de recherche en texte intégral. Pour plus d’informations, consultez [Configurer et gérer les extensions analytiques avancées](../../relational-databases/search/configure-and-manage-filters-for-search.md).  
  
   
## Création d'un catalogue de texte intégral  
  
-   [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)  
  
-   [Créer et gérer des catalogues de texte intégral](../../relational-databases/search/create-and-manage-full-text-catalogs.md)  
  
## Afficher les index  
  
-   [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
## Créer un index unique  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
-   [Ouvrir le Concepteur de tables &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-table-designer-visual-database-tools.md)  
  
## Créer un index de recherche en texte intégral  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)  
  
-   [Créer et gérer des index de recherche en texte intégral](../../relational-databases/search/create-and-manage-full-text-indexes.md)  
  
## Afficher des informations sur un index de recherche en texte intégral  
  
|Vue catalogue ou vue de gestion dynamique|Description|  
|----------------------------------------|-----------------|  
|[sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)|Retourne une ligne pour chaque catalogue de texte intégral vers une référence d'index de recherche en texte intégral.|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)|Contient une ligne pour chaque colonne qui fait partie d'un index de recherche en texte intégral.|  
|[sys.fulltext_index_fragments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)|Un index de recherche en texte intégral utilise des tables internes appelées fragments d'index de recherche en texte intégral pour stocker les données d'index inversées. Cette vue permet d'interroger les métadonnées relatives à ces fragments. Cette vue contient une ligne pour chaque fragment d'index de recherche en texte intégral dans chaque table qui contient un index.|  
|[sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)|Contient une ligne par index de recherche en texte intégral d'un objet tabulaire.|  
|[sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)|Retourne des informations sur le contenu d'un index de recherche en texte intégral pour la table spécifiée.|  
|[sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)|Retourne des informations sur le contenu de niveau document d'un index de recherche en texte intégral pour la table spécifiée. Un mot clé donné peut apparaître dans plusieurs documents.|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)|Retourne des informations sur les remplissages d'index de texte intégral actuellement en cours.|  
  

  
## Informations supplémentaires 
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Alimenter des index de recherche en texte intégral](../../relational-databases/search/populate-full-text-indexes.md)   
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)  
  
  