---
title: Bien démarrer avec la recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text indexes [SQL Server], creating
- full-text search [SQL Server], about
- full-text search [SQL Server], setting up
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fd5ced641ee8fc17f0be7d7b6e19aff17dcb69bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011286"
---
# <a name="get-started-with-full-text-search"></a>Commencer à utiliser la recherche en texte intégral
  Les bases de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent en charge le texte intégral par défaut. Cependant, pour utiliser l'index de recherche en texte intégral dans une table, vous devez configurer l'outil d'indexation de texte intégral dans les colonnes des tables auxquelles vous souhaitez accéder via le moteur de texte intégral.  
  
##  <a name="configure"></a> Configuration d’une base de données pour la recherche en texte intégral  
 Dans n'importe quel scénario, un administrateur de base de données effectue les étapes de base suivantes afin de configurer les colonnes de table d'une base de données pour la recherche en texte intégral :  
  
1.  Création d'un catalogue de texte intégral.  
  
2.  Sur chaque table devant faire l'objet d'une recherche, créez un index de recherche en texte intégral en procédant comme suit :  
  
    1.  Identifiez chaque colonne de texte que vous souhaitez inclure dans l'index de recherche en texte intégral.  
  
    2.  Si une colonne donnée contient des documents stockés en tant que données binaires (`varbinary(max)`, ou `image` données), vous devez spécifier une colonne de table (la *colonne de type*) qui identifie le type de chaque document dans la colonne indexée.  
  
    3.  Spécifiez la langue à utiliser par la recherche en texte intégral sur les documents contenus dans la colonne.  
  
    4.  Choisissez le mécanisme de suivi des modifications que vous souhaitez utiliser sur l'index de recherche en texte intégral afin de suivre les modifications effectuées dans la table de base et dans ses colonnes.  
  
 La recherche en texte intégral prend en charge plusieurs langues par le biais de l’utilisation des *composants linguistiques* suivants : analyseurs lexicaux et générateurs de formes dérivées, listes de mots vides qui contiennent des mots vides (également appelés mots parasites) et fichiers de dictionnaire des synonymes. Les fichiers de dictionnaire des synonymes et, dans certains cas, les listes de mots vides, doivent être configurés par un administrateur de base de données. Un fichier de dictionnaire des synonymes donné prend en charge tous les index de recherche en texte intégral qui utilisent la langue correspondante, et une liste de mots vides donnée peut être associée à autant d'index de recherche en texte intégral que nécessaire.  
  
##  <a name="setup"></a> Configuration d’un catalogue de texte intégral et les Index  
 Cette opération implique les étapes fondamentales suivantes :  
  
1.  Créez un catalogue de texte intégral pour stocker les index de recherche en texte intégral.  
  
     Chaque index de recherche en texte intégral doit appartenir à un catalogue de texte intégral. Vous pouvez créer un catalogue de texte séparé pour chaque index de recherche en texte intégral ou associer plusieurs index de recherche en texte intégral à un catalogue donné. Un catalogue de texte intégral est un objet virtuel qui n'appartient à aucun groupe de fichiers. Le catalogue est un concept logique qui fait référence à un groupe d'index de recherche en texte intégral.  
  
2.  Créez un index de recherche en texte intégral sur la table ou vue indexée.  
  
     Un index de recherche en texte intégral est un type spécial d'index fonctionnel par jeton qui est construit et géré par le Moteur d'indexation et de recherche en texte intégral. Pour que la création d'une recherche en texte intégral soit possible sur une table ou une vue, celles-ci doivent avoir un index unique ne comportant qu'une seule colonne et n'acceptant pas les valeurs Null. Le Moteur d'indexation et de recherche en texte intégral utilise cet index unique pour mapper chaque ligne de la table à une clé compressible unique. Un index de recherche en texte intégral peut inclure les colonnes `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary` et `varbinary(max)`. Pour plus d’informations, consultez [Créer et gérer des index de recherche en texte intégral](create-and-manage-full-text-indexes.md).  
  
 Avant d'apprendre à créer des index de recherche en texte intégral, il est important de déterminer en quoi ils diffèrent des index [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] classiques. Le tableau suivant répertorie les différences.  
  
|Index de texte intégral|Index SQL Server classiques|  
|------------------------|--------------------------------|  
|Un seul index de recherche en texte intégral est autorisé par table.|Plusieurs index classiques sont autorisés par table.|  
|L’ajout de données aux index de recherche en texte intégral, opération que l’on appelle *remplissage*, doit être demandé soit dans le cadre de la planification, soit par le biais d’une requête spécifique, ou peut intervenir automatiquement lors de l’ajout de nouvelles données.|Sont mis à jour automatiquement lorsque les données sur lesquelles ils sont fondés sont modifiées, mises à jour ou supprimées.|  
|Sont groupés à l'intérieur d'une même base de données dans un ou plusieurs catalogues de texte intégral.|Ne sont pas groupés.|  
  
  
##  <a name="options"></a> Sélection des Options pour un Index de recherche en texte intégral  
 Cette section couvre ce qui suit :  
  
-   Sélection du langage de la colonne  
  
-   Sélection d'un groupe de fichiers pour un index de recherche en texte intégral  
  
-   Affectation de l'index de recherche en texte intégral à un catalogue de texte intégral  
  
-   Association d'une liste de mots vides à l'index de recherche en texte intégral  
  
-   Mise à jour d'un index de recherche en texte intégral  
  
### <a name="choosing-the-column-language"></a>Sélection de la langue de la colonne  
 Pour plus d’informations sur les éléments à prendre en considération lors du choix de la langue de la colonne, consultez [Choisir une langue lors de la création d’un index de recherche en texte intégral](choose-a-language-when-creating-a-full-text-index.md).  
  
### <a name="choosing-a-filegroup-for-a-full-text-index"></a>Choix d'un groupe de fichiers pour un index de recherche en texte intégral  
 Le processus de création d'un index de recherche en texte intégral est une opération assez intensive en matière d'entrées/sorties (à haut niveau, elle consiste à lire les données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis à propager les données filtrées vers l'index de recherche en texte intégral). Comme meilleure pratique recommandée, localisez un index de recherche en texte intégral dans le groupe de fichiers de base de données qui convient le mieux pour optimiser les performances d'E/S ou localisez les index de recherche en texte intégral dans un groupe de fichiers différent sur un autre volume.  
  
 Lorsque la facilité de gestion représente un critère important pour vous, nous vous recommandons de stocker les données de table et tout catalogue de texte intégral affilié dans le même groupe de fichiers. Quelquefois, en raison de critères de performance, vous pouvez souhaiter avoir les données de table et l'index de recherche en texte intégral dans des groupes de fichiers différents stockés sur des volumes différents afin d'optimiser le parallélisme d'E/S.  
  
  
### <a name="assigning-the-full-text-index-to-a-full-text-catalog"></a>Affectation de l'index de recherche en texte intégral à un catalogue de texte intégral  
 Il est important de planifier le placement d'index de recherche en texte intégral pour les tables des catalogues de texte intégral.  
  
 Nous vous recommandons d'associer les tables ayant les mêmes caractéristiques de mise à jour (par exemple avec peu de modifications ou, au contraire, beaucoup de modifications, ou les tables fréquemment modifiées à un moment donné de la journée) dans le même catalogue de texte intégral. Cette manière de configurer la planification du remplissage du catalogue de texte intégral permet d'assurer la synchronisation perpétuelle des index de texte intégral et des tables, sans nuire à l'utilisation des ressources du serveur de base de données pendant les périodes de forte activité.  
  
 Lorsque vous affectez une table à un catalogue de texte intégral, prenez en considération les directives suivantes :  
  
-   Sélectionnez systématiquement le plus petit index unique disponible comme clé unique de texte intégral Il s'agira idéalement d'un index de quatre octets, basé sur des entiers. Ainsi, les ressources exigées par le service [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search dans le système de fichiers sont réduites de manière significative. Si la clé primaire est volumineuse (plus de 100 octets), pensez à choisir un autre index unique pour la table (ou créez-le) comme clé unique de texte intégral. Dans le cas contraire, si la taille de la clé unique de texte intégral dépasse la taille maximale autorisée (900 octets), le remplissage de texte intégral est impossible.  
  
-   Si vous indexez une table de plusieurs millions de lignes, affectez-la à un catalogue de texte intégral qui lui est propre.  
  
-   Prenez en compte la quantité de modifications apparaissant dans les tables soumises à l'indexation de texte intégral ainsi que le nombre total de lignes concernées dans ces tables. Si le nombre total de lignes modifiées, auquel s'ajoute le nombre de lignes de table présentes au cours du dernier remplissage de texte intégral, s'élève à plusieurs millions, affectez la table à un catalogue de texte intégral qui lui est propre.  
  
  
### <a name="associating-a-stoplist-with-the-full-text-index"></a>Association d'une liste de mots vides à l'index de recherche en texte intégral  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduit les listes de mots vides. Une *liste de mots vides* est une liste contenant des mots vides, également appelés mots parasites. Une liste de mots vides est associée à chaque index de recherche en texte intégral, et les mots contenus dans cette liste de mots vides s'appliquent aux requêtes de texte intégral sur cet index. Par défaut, la liste de mots vides système est associée à un nouvel index de recherche en texte intégral. Toutefois, vous pouvez créer et utiliser à la place votre propre liste de mots vides. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
 Par exemple, l’instruction [CREATE FULLTEXT STOPLIST](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante crée une liste de mots vides de texte intégral nommée myStoplist3 en copiant la liste de mots vides système :  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 L’instruction [ALTER FULLTEXT STOPLIST](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante modifie une liste de mots vides nommée myStoplist en ajoutant le mot « en » (d’abord pour l’espagnol, puis pour le français) :  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
  
  
### <a name="updating-a-full-text-index"></a>Mise à jour d'un index de recherche en texte intégral  
 À l'instar des index [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] classiques, les index de recherche en texte intégral peuvent être automatiquement mis à jour à mesure que les données sont modifiées dans les tables associées. Il s'agit du comportement par défaut. Vous pouvez, également, garder manuellement vos index de recherche en texte intégral à jour ou à intervalles planifiés spécifiés. L'alimentation d'un index de recherche en texte intégral peut être exigeante en termes de temps et de ressources ; par conséquent, la mise à jour de l'index est effectuée habituellement en mode de processus asynchrone qui s'exécute en arrière-plan et conserve l'index de recherche en texte intégral à jour après les modifications opérées dans la table de base. La mise à jour immédiate d'un index de recherche en texte intégral après chaque modification dans la table de base peut être gourmande en ressources. Par conséquent, si vous avez un taux de mise à jour/insertion/suppression très élevé, vous pouvez constater une baisse dans les performances des requêtes. Si cela se produit, pensez à planifier de temps à autre des mises à jour manuelles du suivi des modifications afin de ne pas perdre trace des nombreuses modifications, au lieu de mettre des requêtes en concurrence pour les ressources.  
  
 Pour analyser l'état du remplissage, utilisez les fonctions FULLTEXTCATALOGPROPERTY ou OBJECTPROPERTYEX. Pour connaître l'état du remplissage du catalogue, exécutez l'instruction suivante :  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 En règle générale, si un remplissage complet est en cours, le résultat retourné est 1.  
  
  
##  <a name="example"></a> Exemple : Configuration de recherche en texte intégral  
 L'exemple en deux parties ci-dessous crée un catalogue de texte intégral nommé `AdvWksDocFTCat` sur la base de données AdventureWorks, puis crée un index de recherche en texte intégral sur la table `Document` dans [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Cette instruction permet de créer le catalogue de texte intégral dans le répertoire par défaut spécifié durant l'installation. Le dossier nommé `AdvWksDocFTCat` se trouve dans le répertoire par défaut.  
  
1.  Pour créer un catalogue de texte intégral nommé `AdvWksDocFTCat`, l’exemple utilise une instruction [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) :  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  Avant de créer un index de recherche en texte intégral sur la table Document, assurez-vous que la table dispose d'un index unique qui n'accepte pas les valeurs NULL et ne comporte qu'une seule colonne. L’instruction [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) suivante crée un index unique, `ui_ukDoc`, sur la colonne DocumentID de la table Document :  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  Une fois que vous avez une clé unique, vous pouvez créer un index de recherche en texte intégral sur la table `Document` en utilisant l’instruction [CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) .  
  
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
  
     Le paramètre TYPE COLUMN défini dans cet exemple spécifie la colonne de type dans la table qui contient le type du document dans chaque ligne de la colonne Document (lequel est de type binaire). La colonne de type stocke le fichier fourni par l’utilisateur d’extension-« .doc », « .xls » et ainsi de suite du document dans une ligne donnée. Le moteur d'indexation et de recherche en texte intégral utilise l'extension de fichier dans une ligne donnée afin d'appeler le filtre approprié pour l'analyse des données de cette ligne. Une fois que le filtre a analysé les données binaires de la ligne, l'analyseur lexical spécifié analyse le contenu (dans cet exemple, c'est l'analyseur lexical pour l'anglais britannique qui est utilisé). Notez que le processus de filtrage se produit uniquement au moment de l'indexation ou si un utilisateur insère ou met à jour une colonne dans la table de base alors que le suivi automatique des modifications est activé pour l'index de recherche en texte intégral. Pour plus d’informations, consultez [Configurer et gérer les extensions analytiques avancées](configure-and-manage-filters-for-search.md).  
  
  
##  <a name="tasks"></a> Tâches courantes  
  
### <a name="to-create-a-full-text-catalog"></a>Pour créer un catalogue de texte intégral  
  
-   [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [Créer et gérer des catalogues de texte intégral](create-and-manage-full-text-catalogs.md)  
  
### <a name="to-view-the-indexes-of-a-table-or-view"></a>Pour afficher les index d'une table (ou vue)  
  
-   [sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
### <a name="to-create-a-unique-index"></a>Pour créer un index unique  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [Ouvrir le Concepteur de tables &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)  
  
### <a name="to-create-a-full-text-index"></a>Pour créer un index de recherche en texte intégral  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [Créer et gérer des index de recherche en texte intégral](create-and-manage-full-text-indexes.md)  
  
### <a name="to-view-information-about-a-full-text-index"></a>Pour afficher des informations sur un index de recherche en texte intégral  
  
|Vue catalogue ou vue de gestion dynamique|Description|  
|----------------------------------------|-----------------|  
|[sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)|Retourne une ligne pour chaque catalogue de texte intégral vers une référence d'index de recherche en texte intégral.|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|Contient une ligne pour chaque colonne qui fait partie d'un index de recherche en texte intégral.|  
|[sys.fulltext_index_fragments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)|Un index de recherche en texte intégral utilise des tables internes appelées fragments d'index de recherche en texte intégral pour stocker les données d'index inversées. Cette vue permet d'interroger les métadonnées relatives à ces fragments. Cette vue contient une ligne pour chaque fragment d'index de recherche en texte intégral dans chaque table qui contient un index.|  
|[sys.fulltext_indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)|Contient une ligne par index de recherche en texte intégral d'un objet tabulaire.|  
|[sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)|Retourne des informations sur le contenu d'un index de recherche en texte intégral pour la table spécifiée.|  
|[sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)|Retourne des informations sur le contenu de niveau document d'un index de recherche en texte intégral pour la table spécifiée. Un mot clé donné peut apparaître dans plusieurs documents.|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|Retourne des informations sur les remplissages d'index de texte intégral actuellement en cours.|  
  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)   
 [Alimenter des index de recherche en texte intégral](populate-full-text-indexes.md)   
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)   
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)  
  
  
