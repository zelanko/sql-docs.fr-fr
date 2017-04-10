---
title: "Publier des donn&#233;es et des objets de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types définis par l'utilisateur [réplication SQL Server]"
  - "articles [réplication SQL Server], suppression"
  - "objets [réplication SQL Server]"
  - "publications [réplication SQL Server], création"
  - "réplication de fusion [réplication SQL Server], publications"
  - "articles de schéma uniquement [réplication SQL Server]"
  - "publication [réplication SQL Server], objets de base de données"
  - "articles [réplication SQL Server], définition"
  - "publication [réplication SQL Server], fonctions"
  - "réplication [SQL Server], publications"
  - "publication [réplication SQL Server], vues"
  - "tables [réplication SQL Server]"
  - "schémas [SQL Server replication]"
  - "publication [réplication SQL Server], données"
  - "schémas [réplication SQL Server], publication"
  - "articles [réplication SQL Server], et procédures stockées"
  - "publication [réplication SQL Server], tables"
  - "types de données d'alias [réplication SQL Server]"
  - "publications [réplication SQL Server], suppression"
  - "réplication d’instantané [SQL Server], publications"
  - "articles [réplication SQL Server], modification"
  - "réplication transactionnelle, publications"
  - "publication [réplication SQL Server], procédures stockées"
  - "publication [SQL Server replication]"
  - "vues [réplication SQL Server]"
  - "procédures stockées [réplication SQL Server], publication"
  - "publications [réplication SQL Server], options de schéma"
  - "articles [réplication SQL Server], ajout"
  - "publications [réplication SQL Server], modification"
  - "fonctions définies par l'utilisateur [réplication SQL Server]"
ms.assetid: d986032c-3387-4de1-a435-3ec5e82185a2
caps.latest.revision: 83
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 83
---
# Publier des donn&#233;es et des objets de base de donn&#233;es
  Lors de la création d'une publication, vous choisissez les tables et les autres objets de base de données à publier. Vous pouvez publier les objets de base de données suivants à l'aide de la réplication.  
  
|Objet de base de données|Réplication d'instantané et réplication transactionnelle|Réplication de fusion|  
|---------------------|--------------------------------------------------------|-----------------------|  
|Tables|X|X|  
|Tables partitionnées|X|X|  
|Procédures stockées – Définition ([!INCLUDE[tsql](../../../includes/tsql-md.md)] et CLR)|X|X|  
|Procédures stockées – Exécution ([!INCLUDE[tsql](../../../includes/tsql-md.md)] et CLR)|X|non|  
|Vues|X|X|  
|Vues indexées|X|X|  
|Vues indexées comme des tables|X|non|  
|Types définis par l'utilisateur (CLR)|X|X|  
|Fonctions définies par l'utilisateur ([!INCLUDE[tsql](../../../includes/tsql-md.md)] et CLR)|X|X|  
|Types de données d'alias|X|X|  
|Index de texte intégral|X|X|  
|Objets de schéma (contraintes, index, déclencheurs DML utilisateur, propriétés étendues et classement)|X|X|  
  
## Création de publications  
 Pour créer une publication, vous fournissez les informations suivantes :  
  
-   Le serveur de distribution.  
  
-   L'emplacement des fichiers d'instantanés.  
  
-   La base de données de publication.  
  
-   Le type de publication à créer (instantané, transactionnelle, transactionnelle avec abonnements pouvant être mis à jour ou fusion).  
  
-   les données et les objets de base de données (articles) à inclure à la publication ;  
  
-   Filtres de lignes statiques et filtres de colonnes statiques pour tous les types de publications, et filtres de lignes paramétrés et filtres de jointure pour les publications de fusion.  
  
-   La planification de l'Agent d'instantané.  
  
-   les comptes sous lesquels les agents suivants s'exécutent : l'Agent d'instantané pour toutes les publications, l'Agent de lecture du journal pour toutes les publications transactionnelles et l'Agent de lecture de la file d'attente pour les publications transactionnelles qui autorisent la mise à jour des abonnements ;  
  
-   Nom et description de la publication.  
  
 Pour plus d'informations sur la manière de travailler avec des publications, consultez les rubriques suivantes :  
  
-   [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)  
  
-   [Afficher et modifier les propriétés d'une publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [Afficher et modifier les propriétés d'un article](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
-   [Supprimer une publication](../../../relational-databases/replication/publish/delete-a-publication.md)  
  
-   [Delete an Article](../../../relational-databases/replication/publish/delete-an-article.md)  
  
> [!NOTE]  
>  La suppression d'un article ou d'une publication ne supprime pas les objets sur l'Abonné.  
  
## Publication de tables  
 L'objet le plus couramment publié est une table. Les liens suivants donnent des informations supplémentaires sur les éléments relatifs à la publication des tables :  
  
-   [Filtrer des données publiées](../../../relational-databases/replication/publish/filter-published-data.md)  
  
-   [Options d'articles pour la réplication transactionnelle](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
-   [Options d'articles pour la réplication de fusion](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)  
  
-   [Répliquer des colonnes d'identité](../../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
 Lors de la publication d'une table pour la réplication, vous pouvez spécifier les objets de schéma qui doivent être copiés vers l'Abonné, tels que l'intégrité référentielle déclarée (contraintes de clé primaire, contraintes référentielles, contraintes uniques), des index, des déclencheurs DML utilisateur (des déclencheurs DDL qui ne peuvent pas être répliqués), des propriétés étendues et des classements. Les propriétés étendues sont répliquées uniquement dans la synchronisation initiale entre le serveur de publication et l'Abonné. Si vous ajoutez ou modifiez une propriété étendue après la synchronisation initiale, la modification n'est pas répliquée.  
  
 Pour spécifier les options de schéma, consultez [spécifier les Options de schéma](../../../relational-databases/replication/publish/specify-schema-options.md) ou <xref:Microsoft.SqlServer.Replication.Article.SchemaOption%2A>.  
  
### Tables et index partitionnés  
 La réplication prend en charge la publication de tables et d'index partitionnés. Le niveau de prise en charge dépend du type de réplication utilisé, ainsi que des options que vous spécifiez pour la publication et les articles associés aux tables partitionnées. Pour plus d’informations, consultez [répliquer des Tables partitionnées et des index](../../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md).  
  
## Publication de procédures stockées  
 Tous les types de réplication vous permettent de répliquer des définitions de procédure stockée : l'instruction CREATE PROCEDURE est copiée sur chaque Abonné. Dans le cas de procédures stockées CLR (Common Language Runtime), l'assembly associé est également copié. Les modifications des procédures sont répliquées vers les Abonnés ; les modifications des assemblys associés ne le sont pas.  
  
 En plus de répliquer la définition d'une procédure stockée, la réplication transactionnelle vous permet de répliquer l'exécution des procédures stockées. Ceci est particulièrement utile lors de la réplication des résultats de procédures stockées de maintenance qui affectent de gros volumes de données. Pour plus d’informations, voir [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
## Publication de vues  
 Tous les types de réplication vous permettent de répliquer des vues. La vue (et l'index qui l'accompagne s'il s'agit d'une vue indexée) peut être copiée vers l'Abonné, mais la table de base doit aussi être répliquée.  
  
 Pour les vues indexées, la réplication transactionnelle vous permet aussi de répliquer la vue indexée en tant que table et non pas en tant que vue, éliminant ainsi la nécessité de répliquer aussi la table de base. Pour ce faire, spécifiez une des options « indexed view logbased » pour le *@type* paramètre de [sp_addarticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Pour plus d’informations sur l’utilisation de **sp_addarticle**, consultez [définir un Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## Publication de fonctions définies par l'utilisateur  
 Les instructions CREATE FUNCTION pour les fonctions CLR et pour les fonctions [!INCLUDE[tsql](../../../includes/tsql-md.md)] sont copiées vers chaque Abonné. Dans le cas des fonctions CLR, l'assembly associé est également copié. Les modifications des fonctions sont répliquées vers les Abonnés ; les modifications aux assemblys associés ne le sont pas.  
  
## Publication de types définis par l'utilisateur et de types de données alias  
 Les colonnes qui utilisent des types définis par l'utilisateur et des types de données alias sont répliquées vers les Abonnés, tout comme les autres colonnes. Le TYPEstatement de créer pour chaque type répliqué est exécutée sur l’abonné avant la création de la table. Dans le cas de types définis par l'utilisateur, l'assembly associé est également copié vers chaque Abonné. Les modifications aux types définis par l'utilisateur et aux types de données alias ne sont pas répliquées vers les Abonnés.  
  
 Si un type est défini dans une base de données mais qu'il n'est référencé par aucune des colonnes quand une publication est créée, le type n'est pas copié vers les Abonnés. Si vous créez plus tard une colonne de ce type dans la base de données et que vous souhaitez la répliquer, vous devez d'abord copier manuellement le type (et l'assembly associé pour un type défini par l'utilisateur) vers chaque Abonné.  
  
## Publication d'index de texte intégral  
 L'instruction CREATE FULLTEXT INDEX est copiée sur chaque Abonné, et l' index de recherche en texte intégral est créé sur l'Abonné. Les modifications apportées aux  index de recherche en texte intégral à l'aide d'ALTER FULLTEXT INDEX ne sont pas répliquées.  
  
## Modifications de schéma pour des objets publiés  
 La réplication prend en charge une grande variété de modifications de schéma pour les objets publiés. Quand vous effectuez une des modifications de schéma suivantes sur l'objet publié approprié sur un Abonné [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , cette modification est propagée par défaut à tous les Abonnés [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 Pour plus d’informations, consultez [apporter des modifications de schéma sur les bases de données de Publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## Considérations sur la publication  
 Soyez attentif aux problèmes suivants lors de la publication d'objets de base de données :  
  
-   La base de données est accessible aux utilisateurs lors de la création de la publication et de l'instantané initial, mais il est conseillé de créer les publications à des moments où l'activité est faible sur le serveur de publication.  
  
-   Une base de données ne peut pas être renommée après qu'une publication y ait été créée. Pour la renommer, vous devez d'abord supprimer la réplication de la base de données.  
  
-   Si vous publiez un objet de base de données qui dépend d'un ou de plusieurs autres objets de base de données, vous devez publier tous les objets référencés. Par exemple, si vous publiez une vue qui dépend d'une table, vous devez publier la table également.  
  
    > [!NOTE]  
    >  Si vous ajoutez un article à une publication de fusion et un article existant dépend du nouvel article, vous devez spécifier un ordre de traitement pour les deux articles à l’aide de la **@processing_order** paramètre de [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) et [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Examinez le scénario suivant : vous publiez une table, mais vous ne publiez pas de fonction référencée par la table. Si vous ne publiez pas la fonction, la table ne peut pas être créée au niveau de l'abonné. Lorsque vous ajoutez la fonction à la publication : spécifiez la valeur **1** pour la **@processing_order** paramètre de **sp_addmergearticle**; et spécifiez une valeur de **2** pour la **@processing_order** paramètre de **sp_changemergearticle**, en spécifiant le nom de table pour le paramètre **@article**. Cet ordre de traitement permet de créer la fonction au niveau de l'Abonné avant la table qui en dépend. Vous pouvez utiliser différents nombres pour chaque article tant que le nombre de la fonction est inférieur au nombre de la table.  
  
-   Les noms de publication ne peuvent pas contenir les caractères suivants : % * [ ] | : " ? \ / \< >.  
  
### Limitations de la publication d'objets  
  
-   Le nombre maximal d'articles et de colonnes publiables diffère selon le type de publication. Pour plus d’informations, consultez la section « Objets de réplication » de [des spécifications de capacité maximale de SQL Server](../../../sql-server/maximum-capacity-specifications-for-sql-server.md).  
  
-   Les procédures stockées, les vues, les déclencheurs et les fonctions définies par l'utilisateur qui sont définies avec WITH ENCRYPTION ne peuvent pas être publiées en tant que composants d'une réplication [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Les collections de schémas XML peuvent être répliquées, mais les modifications ne sont pas répliquées après l'instantané initial.  
  
-   Les tables publiées pour la réplication transactionnelle doivent avoir une clé primaire. Si une table est dans une publication de réplication transactionnelle, vous ne pouvez pas désactiver les index qui sont associés à des colonnes clés primaire. Ces index sont requis par la réplication. Pour désactiver un index, vous devez d'abord supprimer la table de la réplication.  
  
-   Limite par défaut créés avec [sp_bindefault & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md) ne sont pas répliqués (les valeurs par défaut liées sont déconseillées au profit des valeurs par défaut créés avec le mot clé DEFAULT de ALTER TABLE ou CREATE TABLE).  
  
-   Les fonctions contenant l'indicateur **NOEXPAND** sur des vues indexées ne peuvent pas être publiées dans la même publication que les tables référencées et les vues d'index, en raison de l'ordre dans lequel l'agent de distribution les livre. Pour contourner ce problème, placez la création de la table et de la vue indexée dans une première publication, puis ajoutez les fonctions contenant l'indicateur **NOEXPAND** sur les vues indexées à une seconde publication que vous publierez à la fin de la première publication. Ou, créer des scripts pour ces fonctions et de fournir le script à l’aide de la *@post_snapshot_script* paramètre de **sp_addpublication**.  
  
### Schémas et propriété des objets  
 La réplication fonctionne par défaut de la façon suivante dans l'Assistant Nouvelle publication quant aux schémas et à la propriété des objets :  
  
-   Pour les articles de publications de fusion d'un niveau de compatibilité de 90 ou supérieur, les publications d'instantané et les publications transactionnelles : par défaut, le propriétaire de l'objet sur l'Abonné est le même que le propriétaire de l'objet correspondant sur le serveur de publication. Si les schémas propriétaires des objets n'existent pas sur l'Abonné, ils sont créés automatiquement.  
  
-   Pour les articles de publications de fusion d'un niveau de compatibilité inférieur à 90 : par défaut, le propriétaire est laissé vide et spécifié comme **dbo** pendant la création de l'objet sur l'Abonné.  
  
-   Pour les articles des publications Oracle : par défaut, le propriétaire est spécifié comme **dbo**.  
  
-   Pour les articles de publications utilisant les instantanés en mode caractère (utilisées pour les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et les abonnés [!INCLUDE[ssEW](../../../includes/ssew-md.md)]) : le propriétaire est laissé vide par défaut. Le propriétaire prend les valeurs par défaut du propriétaire associé au compte utilisé par l'Agent de distribution ou l'Agent de fusion pour se connecter à l'Abonné.  
  
 Le propriétaire de l’objet peut être modifié via le **Propriétés de l’Article - \<***Article***>** boîte de dialogue et par le biais de procédures stockées : **sp_addarticle**, **sp_addmergearticle**, **sp_changearticle**, et **sp_changemergearticle**. Pour plus d’informations, consultez [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md), [définir un Article](../../../relational-databases/replication/publish/define-an-article.md), et [Afficher et modifier les propriétés d’Article](../../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
### Publication de données sur les Abonnés exécutant des versions antérieures de SQL Server  
  
-   Si vous publiez sur un Abonné exécutant une version antérieure de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous êtes limité par les fonctionnalités de cette version, en termes de fonctionnalités spécifiques à la réplication et en termes de fonctionnalités globales du produit.  
  
-   Les publications de fusion utilisent un niveau de compatibilité, qui détermine les fonctionnalités qui peuvent être utilisées dans une publication et qui vous permet de prendre en charge des Abonnés exécutant des versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
### Publication de tables dans plusieurs publications  
 La réplication prend en charge la publication d'articles dans plusieurs publications (y compris la réédition de données) avec les restrictions suivantes :  
  
-   Si un article est publié dans une publication transactionnelle et une publication de fusion, assurez-vous que le *@published_in_tran_pub* propriété est définie sur TRUE pour l’article de fusion. Pour plus d’informations sur la définition des propriétés, consultez [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md) et [Afficher et modifier les propriétés d’Article](../../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
     Vous devez également définir le *@published_in_tran_pub* propriété si un article fait partie d’un abonnement transactionnel et est inclus dans une publication de fusion. Si tel est le cas, gardez à l'esprit que, par défaut, la réplication transactionnelle suppose que les tables sur l'Abonné soient traitées en tant qu'objets accessibles en lecture seule ; si la réplication de fusion apporte des modifications aux données d'une table dans un abonnement transactionnel, une non-convergence de données peut se produire. Pour éviter cette éventualité, il est recommandé de spécifier toute table de ce type en tant qu'objet en téléchargement seul dans la publication de fusion. Cela empêche un Abonné de fusion de télécharger les modifications apportées aux données de la table. Pour plus d’informations, consultez [optimiser les performances de réplication de fusion avec des Articles avec](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
-   Un article ne peut pas être publié à la fois dans une publication de fusion et dans une publication transactionnelle avec des abonnements mis à jour en file d'attente.  
  
-   Les articles inclus dans les publications transactionnelles qui prennent en charge les abonnements mis à jour ne peuvent pas être republiés.  
  
-   Si un article est publié dans plusieurs publications transactionnelles qui prennent en charge les abonnements mis à jour en attente, les propriétés suivantes doivent avoir la même valeur pour l'article dans toutes les publications :  
  
    |Propriété|Paramètre dans sp_addarticle|  
    |--------------|---------------------------------|  
    |Gestion de plages d'identités|**@auto_identity_range** (obsolète) et **@identityrangemangementoption**|  
    |Plage d'identités du serveur de publication|**@pub_identity_range**|  
    |Plage d'identités|**@identity_range**|  
    |Seuil de plage d'identités|**@threshold**|  
  
     Pour plus d’informations sur ces paramètres, consultez la page [sp_addarticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
-   Si un article est publié dans plusieurs publications de fusion, les propriétés suivantes doivent avoir la même valeur pour l'article dans toutes les publications :  
  
    |Propriété|Paramètre dans sp_addmergearticle|  
    |--------------|--------------------------------------|  
    |Suivi de colonne|**@column_tracking**|  
    |Options de schéma|**@schema_option**|  
    |Filtrage de colonnes|**@vertical_partition**|  
    |Options de chargement de l'Abonné|**@subscriber_upload_options**|  
    |Suivi des suppressions conditionnelles|**@delete_tracking**|  
    |Compensation d'erreur|**@compensate_for_errors**|  
    |Gestion de plages d'identités|**@auto_identity_range** (obsolète) et **@identityrangemangementoption**|  
    |Plage d'identités du serveur de publication|**@pub_identity_range**|  
    |Plage d'identités|**@identity_range**|  
    |Seuil de plage d'identités|**@threshold**|  
    |Options de la partition|**@partition_options**|  
    |Diffusion de colonne de BLOB|**@stream_blob_columns**|  
    |Type de filtre|**@filter_type** (paramètre **sp_addmergefilter**)|  
  
     Pour plus d’informations sur ces paramètres, consultez la page [sp_addmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) et [sp_addmergefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md).  
  
-   La réplication transactionnelle et la réplication de fusion non filtrée prennent en charge la publication d'une table dans plusieurs publications, puis les abonnements dans une table unique de la base de données d'abonnement (communément appelée un scénario de cumul (roll up)). Le cumul est souvent utilisé pour agréger en une seule table des sous-ensembles de données provenant de plusieurs emplacements sur un Abonné central. Les publications de fusion filtrées ne prennent pas en charge le scénario avec un Abonné central. Pour la réplication de fusion, le cumul est généralement mis en œuvre via une seule publication avec des filtres de lignes personnalisés. Pour plus d'informations, voir [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
## Voir aussi  
 [Ajouter et supprimer des articles de publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Configurer la distribution](../../../relational-databases/replication/configure-distribution.md)   
 [Initialiser un abonnement](../../../relational-databases/replication/initialize-a-subscription.md)   
 [Création de scripts de réplication](../../../relational-databases/replication/scripting-replication.md)   
 [Sécuriser le serveur de publication](../../../relational-databases/replication/security/secure-the-publisher.md)   
 [S'abonner à des publications](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  