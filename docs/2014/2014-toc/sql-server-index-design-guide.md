---
title: Guide de conception d’index SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: b856ee9a-49e7-4fab-a88d-48a633fce269
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ee47da3e97240ec4573303700e9793ee482821c7
ms.sourcegitcommit: e3f5b70bbb4c66294df8c7b2c70186bdf2365af9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397668"
---
# <a name="sql-server-index-design-guide"></a>Guide de conception d'index SQL Server

  L'engorgement des applications de base de données est souvent imputable à des index mal conçus ou en nombre insuffisant. La conception d'index efficaces est primordiale pour le bon fonctionnement des bases de données et des applications. Ce guide de conception d'index SQL Server contient les informations et les meilleures pratiques nécessaires à la création d'index efficaces pour répondre aux besoins de votre application.  
  
**S'applique à**: [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] et [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , sauf indication contraire.  
  
 Ce guide suppose que le lecteur connaît les types d'index disponibles dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir description générale des types d'index, consultez [Types d'index](../relational-databases/indexes/indexes.md).  
  
##  <a name="Top"></a> Dans ce Guide  

 [Principes fondamentaux de conception de index](#Basics)  
  
 [Instructions de conception d’Index général](#General_Design)  
  
 [Indications pour la conception d’index cluster](#Clustered)  
  
 [Indications pour la conception d’index non-cluster](#Nonclustered)  
  
 [Indications pour la conception d’index uniques](#Unique)  
  
 [Indications pour la conception d’index filtrés](#Filtered)  
  
 [Lecture supplémentaire](#Additional_Reading)  
  
##  <a name="Basics"></a> Notions de base de la conception d'index  

 Un index est une structure sur disque associée à une table ou une vue qui accélère l'extraction des lignes de la table ou de la vue. Il contient des clés créées à partir d'une ou plusieurs colonnes de la table ou de la vue. Ces clés sont stockées dans une structure (B-tree) qui permet à SQL Server de trouver rapidement et efficacement la ou les lignes associées aux valeurs de clé.  
  
 Le choix d'index adaptés à une base de données et à sa charge de travail est une opération complexe qui vise à trouver un compromis entre vitesse des requêtes et coûts de mise à jour. Les index étroits, c'est-à-dire les index ne comportant que quelques colonnes dans la clé d'index, requièrent moins d'espace disque et de besoins de maintenance. En revanche, les index larges couvrent plus de requêtes. Vous devrez éventuellement essayer plusieurs conceptions différentes avant de trouver l'index le plus performant. Il est possible d'ajouter, de modifier et de supprimer des index sans affecter le schéma de la base de données ou la conception des applications. Par conséquent, n'hésitez à faire des essais avec différents index.  
  
 Dans la majorité des cas, l'optimiseur de requête de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] choisit de manière fiable l'index le plus efficace. La stratégie globale de création d'index consiste à fournir à l'optimiseur de requête une sélection variée d'index et à se fier à lui pour faire le bon choix. Ce procédé permet de réduire le temps d'analyse et produit de bons résultats dans bon nombre de cas. Pour déterminer quels sont les index qu'utilise l'optimiseur de requête dans le cas d'une requête donnée, sélectionnez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Inclure le plan d'exécution réel **dans le menu** Requête **de**.  
  
 L'utilisation d'index n'est pas forcément synonyme de bonnes performances, et inversement, de bonnes performances ne sauraient être nécessairement attribuables à l'utilisation d'index efficaces. Si l'utilisation d'un index contribuait toujours à produire les meilleurs résultats, le travail de l'optimiseur de requête en serait simplifié. En réalité, le choix d'un index inapproprié peut aboutir à des performances moins que satisfaisantes. La tâche de l'optimiseur de requête est donc de ne sélectionner un index, ou une combinaison d'index, que dans les cas où cette sélection est susceptible d'améliorer les performances et d'éviter la récupération par index si elle doit les détériorer.  
  
### <a name="index-design-tasks"></a>Tâches de conception d'index  

 La stratégie de conception d'index que nous recommandons est constituée des tâches suivantes :  
  
1.  Comprendre les caractéristiques de la base de données elle-même. Par exemple, s'agit-il d'une base de données de traitement transactionnel en ligne (OLTP) dont les données sont souvent modifiées, ou d'une base de données d'aide à la décision (DSS) ou d'entreposage de données (OLAP) contenant essentiellement des données en lecture seule et devant traiter des jeux de données volumineux rapidement ? Dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], les index *columnstore optimisés en mémoire xVelocity* sont particulièrement adaptés aux jeux de données d'entrepôts de données classiques. Les index columnstore peuvent transformer l'expérience utilisateur des entrepôts de données en améliorant considérablement les performances des requêtes communes liées aux entrepôts de données, par exemple en matière de filtrage, d'agrégation, de regroupement et de jointure en étoile. Pour plus d’informations, consultez [index Columnstore décrits](../relational-databases/indexes/columnstore-indexes-described.md).  
  
2.  Comprendre les caractéristiques des requêtes les plus fréquemment utilisées. Par exemple, si vous savez qu'une requête fréquemment utilisée crée une jointure entre deux tables ou plus, vous serez plus à même de choisir le type d'index le mieux adapté.  
  
3.  Comprendre les caractéristiques des colonnes utilisées dans les requêtes. Par exemple, un index s'avère idéal pour les colonnes associées à des données de type integer et qui sont également uniques ou n'acceptent pas les valeurs NULL. Pour les colonnes qui ont des sous-ensembles de données bien définis, utilisez un index filtré dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et versions ultérieures. Pour plus d'informations, consultez [Instructions de conception d'index filtrés](#Filtered) dans ce guide.  
  
4.  Identifier les options d'index qui peuvent améliorer les performances au moment de la création ou de la maintenance de l'index. Par exemple, si vous créez un index cluster dans une table volumineuse existante, vous aurez tout intérêt à utiliser l'option d'index ONLINE. Cette option permet en effet la poursuite des activités concurrentes sur les données sous-jacentes pendant la création ou la reconstruction de l'index. Pour plus d’informations, consultez [Définir les options d’index](../relational-databases/indexes/set-index-options.md).  
  
5.  Déterminer l'emplacement de stockage optimal pour l'index. Un index non-cluster peut être stocké dans le même groupe de fichiers que celui auquel appartient la table sous-jacente, ou dans un groupe de fichiers distinct. L'emplacement de stockage des index peut améliorer les performances des requêtes par l'amélioration des performances d'E/S des disques. Par exemple, en stockant un index non-cluster dans un groupe de fichiers résidant sur un disque différent de celui du groupe de fichiers de la table, vous pouvez améliorer les performances, car plusieurs disques peuvent être lus simultanément.  
  
     Une autre solution consiste à utiliser un schéma de partition sur plusieurs groupes de fichiers pour les index cluster et non-cluster. Le partitionnement permet une gestion plus simple des tables et index volumineux. Vous pouvez en effet accéder à des sous-ensembles de données ou les gérer de manière rapide et efficace, tout en préservant l'intégrité de la collection globale. Pour plus d'informations, consultez [Partitioned Tables and Indexes](../relational-databases/partitions/partitioned-tables-and-indexes.md). Si vous envisagez de recourir au partitionnement, vous devez déterminer si l'index doit être aligné, c'est-à-dire, partitionné plus ou moins de la même façon que la table, ou s'il doit être partitionné de façon indépendante.  
  
##  <a name="General_Design"></a> Consignes générales pour la création d'index  

 Les administrateurs de bases de données expérimentés peuvent concevoir de bons ensembles d'index, mais cette tâche est très complexe, sujette à erreurs et demande beaucoup de temps, même dans le cas de bases de données et de charges de travail peu complexes. La compréhension des caractéristiques de votre base de données, de vos requêtes et de vos colonnes de données peut vous aider à créer des index optimaux.  
  
### <a name="database-considerations"></a>Remarques sur la base de données  

 Lorsque vous créez un index, prenez en compte les directives suivantes relatives aux bases de données :  
  
-   La définition de nombreux index sur une table affecte les performances des instructions INSERT, UPDATE, DELETE et MERGE, car tous les index doivent être mis à jour en conséquence à mesure que les données de la table changent. Par exemple, si une colonne est utilisée dans plusieurs index et vous exécutez une instruction UPDATE qui modifie les données de cette colonne, chaque index contenant cette colonne doit être mis à jour, ainsi que la colonne de la table de base sous-jacente (segment de mémoire ou index cluster).  
  
    -   Évitez que les tables mises à jour ne soient trop abondamment indexées et faites en sorte que les index soient étroits, c'est-à-dire qu'ils comprennent le moins de colonnes possible.  
  
    -   Utilisez de nombreux index pour améliorer les performances des requêtes sur les tables possédant des besoins réduits en matière de mise à jour, mais de grands volumes de données. Un grand nombre d'index peut améliorer les performances des requêtes qui ne modifient pas les données (instructions SELECT), car l'optimiseur de requête dispose d'un choix d'index plus vaste pour déterminer la méthode d'accès la plus rapide.  
  
-   Il n'est peut-être pas idéal d'indexer des tables de taille réduite, car le temps nécessaire à l'optimiseur de requête pour parcourir l'index à la recherche de données peut être supérieur à la durée d'une simple analyse de la table. Par conséquent, les index de petites tables peuvent ne jamais être utilisés, mais doivent néanmoins être gérés, car les données de la table changent.  
  
-   Les index de vues peuvent vous permettre d'améliorer considérablement les performances lorsque la vue contient des agrégations, des jointures de tables ou une combinaison d'agrégations et de jointures. La vue ne doit pas être explicitement référencée dans la requête pour que l'optimiseur de requête puisse l'utiliser.  
  
-   Servez-vous de l'Assistant Paramétrage du moteur de base de données pour analyser votre base de données et obtenir des recommandations sur les index. Pour plus d'informations, consultez [Database Engine Tuning Advisor](../relational-databases/performance/database-engine-tuning-advisor.md).  
  
### <a name="query-considerations"></a>Remarques sur les requêtes  

 Lorsque vous créez un index, prenez en compte les directives suivantes relatives aux requêtes :  
  
-   Créez des index non cluster sur les colonnes fréquemment utilisées dans des prédicats et des conditions de jointure dans des requêtes. Toutefois, évitez d'ajouter des colonnes superflues. L'ajout d'un trop grand nombre de colonnes d'index peut avoir une influence négative sur les performances de gestion des index et de l'espace disque.  
  
-   La couverture des index peut améliorer les performances des requêtes, car toutes les données nécessaires pour répondre aux exigences de la requête existent dans l'index proprement dit. Cela signifie que seules les pages d'index, et non les pages de données de la table ou de l'index cluster, sont nécessaires pour récupérer les données demandées, réduisant ainsi globalement le nombre d'E/S des disques. Par exemple, une requête de colonnes **a** et **b** sur une table possédant un index composite créé sur les colonnes **a**, **b**et **c** peut récupérer les données spécifiées à partir du seul index.  
  
-   Rédigez des requêtes insérant ou modifiant un maximum de lignes en une seule instruction, plutôt que de recourir à plusieurs requêtes pour mettre à jour les mêmes lignes. De cette façon, la maintenance d'index optimisée peut être exploitée.  
  
-   Évaluez le type de requête et la manière dont les colonnes sont utilisées dans la requête. Par exemple, une colonne utilisée dans un type de requête de correspondance exacte constitue un candidat valable à un index non-cluster ou cluster.  
  
### <a name="column-considerations"></a>Remarques sur les colonnes  

 Lorsque vous créez un index, prenez en compte les directives suivantes relatives aux colonnes :  
  
-   Veillez à ce que la clé d'index des index cluster soit courte. En outre, les index cluster bénéficient du fait d'être créés sur des colonnes uniques ou non NULL.  
  
-   Les colonnes de types de données `ntext`, `text`, `image`, `varchar(max)`, `nvarchar(max)` et `varbinary(max)` ne peuvent pas être spécifiées comme colonnes de clés d'index. Cependant, les types de données `varchar(max)`, `nvarchar(max)`, `varbinary(max)` et `xml` peuvent participer à des index non-cluster en tant que colonnes d'index non clé. Pour plus d'informations, consultez la section [Index avec colonnes incluses](#Included_Columns)dans ce guide.  
  
-   Un type de données `xml` ne peut être qu'une colonne clé dans un index XML. Pour plus d’informations, consultez [Index XML &#40;SQL Server&#41;](../relational-databases/xml/xml-indexes-sql-server.md). SQL Server 2012 SP1 introduit un nouveau type d'index XML appelé index XML sélectif. Ce nouvel index améliore les performances de requête sur les données stockées en XML dans SQL Server, permettant ainsi d'indexer plus rapidement les charges de travail comportant beaucoup de données XML et améliorant l'évolutivité en réduisant les coûts de stockage de l'index en lui-même. Pour plus d’informations, consultez [Index XML sélectifs &#40;SXI&#41;](../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
-   Vérifiez l'unicité des colonnes. Un index unique plutôt que non unique sur la même combinaison de colonnes procure des informations supplémentaires à l'optimiseur de requête, ce qui améliore l'utilité de l'index. Pour plus d'informations, consultez [Instructions de conception d'index uniques](#Unique) dans ce guide.  
  
-   Examinez la distribution des données dans la colonne. Bien souvent, la longueur d'exécution d'une requête est due à l'indexation d'une colonne comportant peu de valeurs uniques ou à la réalisation d'une jointure sur ce type de colonne. Il s'agit d'un problème crucial pour les données et la requête, que l'on ne peut généralement pas résoudre sans identifier clairement la situation. Un répertoire téléphonique physique, par exemple, trié dans l'ordre alphabétique par nom de famille, ne permettra pas l'identification rapide d'une personne si tous les habitants de la ville se nomment Smith ou Jones. Pour plus d'informations sur la distribution de données, consultez [Statistics](../relational-databases/statistics/statistics.md).  
  
-   Envisagez d'utiliser des index filtrés sur les colonnes qui ont des sous-ensembles bien définis, par exemple les colonnes éparses, les colonnes contenant principalement des valeurs NULL, les colonnes contenant des catégories de valeurs et les colonnes contenant des plages de valeurs distinctes. Un index filtré bien conçu peut améliorer les performances des requêtes et réduire les coûts de maintenance et de stockage.  
  
-   Tenez compte de l'ordre des colonnes si l'index doit en contenir plusieurs. La colonne utilisée dans la clause WHERE au sein d'une condition de recherche de type égal à (=), supérieur à (>), inférieur à (<) ou BETWEEN, ou qui participe à une jointure, doit être insérée en premier. Les colonnes supplémentaires doivent être classées en fonction de leur niveau de différenciation, c'est-à-dire de la plus distincte à la moins distincte.  
  
     Par exemple, si l'index est défini en tant que `LastName`, la valeur `FirstName` de l'index sera utile si la condition de recherche est `WHERE LastName = 'Smith'` ou `WHERE LastName = Smith AND FirstName LIKE 'J%'`. Cependant, l'optimiseur de requête n'utilise pas l'index pour une requête portant uniquement sur `FirstName (WHERE FirstName = 'Jane')`.  
  
-   Pensez à indexer les colonnes calculées. Pour plus d'informations, consultez [Indexes on Computed Columns](../relational-databases/indexes/indexes-on-computed-columns.md).  
  
### <a name="index-characteristics"></a>Caractéristiques des index  

 Après avoir déterminé qu'un index est approprié pour une requête, vous pouvez sélectionner le type d'index qui convient le mieux à la situation. Un index doit posséder les caractéristiques suivantes :  
  
-   être cluster ou non-cluster ;  
  
-   être unique ou non unique ;  
  
-   être à une ou plusieurs colonnes ;  
  
-   être trié par ordre croissant ou décroissant d'après les colonnes qui le constituent ;  
  
-   table entière plutôt que filtré pour les index non cluster.  
  
 Vous pouvez également personnaliser les caractéristiques de stockage initiales de l'index afin d'optimiser ses performances ou sa maintenance en définissant une option telle que FILLFACTOR. Vous pouvez également déterminer l'emplacement de stockage de l'index en utilisant des groupes de fichiers ou des schémas de partition pour optimiser les performances.  
  
###  <a name="Index_placement"></a> Placement d'index sur les groupes de fichiers ou les schémas de partition  

 Lors du développement de votre stratégie de conception des index, vous devez tenir compte du placement de ces index sur les groupes de fichiers associés à la base de données. Une sélection rigoureuse du groupe de fichiers ou du schéma de partition peut améliorer les performances des requêtes.  
  
 Par défaut, les index sont stockés dans le même groupe de fichiers que la table de base sur laquelle est créé l'index. Un index cluster non partitionné et la table de base résident toujours dans le même groupe de fichiers. Toutefois, vous pouvez effectuer les opérations suivantes :  
  
-   créer des index non cluster dans un groupe de fichiers différent de celui de la table de base ou de l'index cluster ;  
  
-   partitionner des index cluster et non-cluster pour qu'ils concernent plusieurs groupes de fichiers ;  
  
-   déplacer une table d'un groupe de fichiers à un autre en supprimant l'index cluster et en spécifiant un nouveau groupe de fichiers ou un nouveau schéma de partition dans la clause MOVE TO de l'instruction DROP INDEX ou en utilisant l'instruction CREATE INDEX avec la clause DROP_EXISTING.  
  
 Créer l'index non-cluster dans un autre groupe de fichiers permet de réaliser des gains de performances si les groupes de fichiers utilisent des lecteurs physiques différents avec leurs propres contrôleurs. Les informations d'index et les données peuvent alors être lues en parallèle par plusieurs têtes de disques. Par exemple, si la `Table_A` du groupe de fichiers `f1` et l' `Index_A` du groupe de fichiers `f2` sont utilisés par la même requête, des gains de performances sont possibles, car les deux groupes de fichiers sont utilisés totalement sans contention. Mais si la `Table_A` est analysée par la requête et si l' `Index_A` n'est pas référencé, seul le groupe de fichiers `f1` est utilisé, ce qui n'apporte aucun gain de performance.  
  
 Comme vous ne pouvez pas prévoir le type d'accès qui se met en place ni le moment de cette mise en place, il peut s'avérer plus judicieux de répartir vos tables et vos index sur tous les groupes de fichiers. Ceci garantit l'accès à tous les disques, car toutes les données et tous les index sont répartis uniformément sur tous les disques, quel que soit le mode d'accès aux données. Cette approche est également plus simple pour les administrateurs système.  
  
#### <a name="partitions-across-multiple-filegroups"></a>Partitions sur plusieurs groupes de fichiers  

 Vous pouvez également envisager de partitionner des index cluster et non-cluster sur plusieurs groupes de fichiers. Les index partitionnés sont partitionnés horizontalement ou par ligne, selon la fonction de partition. La fonction de partition définit le mode de mappage de chaque ligne sur un ensemble de partitions basé sur les valeurs de certaines colonnes, nommées colonnes de partition. Un schéma de partition spécifie le mappage des partitions sur un ensemble de groupe de fichiers.  
  
 Le partitionnement d'un index peut présenter les avantages suivants :  
  
-   Systèmes évolutifs permettant de gérer plus facilement les grands index. Par exemple, les systèmes OLTP peuvent mettre en œuvre des applications sensibles aux partitions qui se chargent des grands index.  
  
-   Exécution plus rapide et plus efficace des requêtes. Lorsque des requêtes accèdent à plusieurs partitions d'un index, l'optimiseur de requête peut traiter plusieurs partitions individuelles en même temps et exclure les partitions qui ne sont pas concernées par la requête.  
  
 Pour plus d’informations, consultez [Tables et index partitionnés](../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
###  <a name="Sort_Order"></a> Indications pour la conception de l'ordre de tri des index  

 Lorsque vous définissez des index, vous devez déterminer si les données de la colonne clé d'index doivent être stockées dans l'ordre croissant ou décroissant. L'ordre croissant est l'option par défaut et maintient la compatibilité avec les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La syntaxe des instructions CREATE INDEX, CREATE TABLE et ALTER TABLE permet l'application des mot clés ASC (croissant) et DESC (décroissant) à chaque colonne d'un index et d'une contrainte.  
  
 La spécification de l'ordre dans lequel les valeurs de clé sont stockées dans un index est utile lorsque les requêtes référençant la table possèdent des clauses ORDER BY qui définissent différents sens pour la ou les colonnes clés de cet index. Dans ces situations, l'index peut supprimer la nécessité d'un opérateur SORT dans le plan de requête, ce qui rend la requête plus efficace. Par exemple, les acheteurs du service achat de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] doivent évaluer la qualité des produits qu'ils acquièrent auprès des fournisseurs. Les acheteurs souhaitent notamment rechercher, parmi les produits envoyés par ces fournisseurs, ceux qui affichent un degré de rejet élevé. Comme le montre la requête suivante, l’extraction des données en fonction de ce critère nécessite que la colonne `RejectedQty` de la table `Purchasing.PurchaseOrderDetail` soit triée dans l’ordre décroissant (de la valeur la plus élevée à la valeur la plus faible), et que la colonne `ProductID` soit triée dans l’ordre croissant (de la valeur la plus faible à la valeur la plus élevée).  
  
```sql
SELECT RejectedQty, ((RejectedQty/OrderQty)*100) AS RejectionRate,  
    ProductID, DueDate  
FROM Purchasing.PurchaseOrderDetail  
ORDER BY RejectedQty DESC, ProductID ASC;  
```  
  
 Le plan d'exécution ci-dessous pour cette requête montre que l'optimiseur de requête a utilisé un opérateur SORT pour retourner l'ensemble de résultats dans l'ordre spécifié par la clause ORDER BY.  
  
 ![Plan d’exécution indique un opérateur SORT est utilisé. ](media/indexsort1.gif "Plan d’exécution indique un opérateur SORT est utilisé.")  
  
 Si un index est créé avec les colonnes clés correspondant à celles de la clause ORDER BY de la requête, l'opérateur SORT peut être supprimé du plan de requête, ce qui rend celui-ci plus efficace.  
  
```sql
CREATE NONCLUSTERED INDEX IX_PurchaseOrderDetail_RejectedQty  
ON Purchasing.PurchaseOrderDetail  
    (RejectedQty DESC, ProductID ASC, DueDate, OrderQty);  
```  
  
 Une fois la requête réexécutée, le plan d'exécution ci-dessous montre que l'opérateur SORT a été supprimé et que l'index non-cluster nouvellement créé est utilisé.  
  
 ![Plan d’exécution indique un tri opérateur n’est pas utilisé](media/insertsort2.gif "plan d’exécution indique un tri opérateur n’est pas utilisé.")  
  
 Le [!INCLUDE[ssDE](../includes/ssde-md.md)] peut parcourir les données aussi efficacement dans un sens que dans l'autre. Un index défini sous la forme `(RejectedQty DESC, ProductID ASC)` peut néanmoins être utilisé pour une requête dont la clause ORDER BY inverse le sens du tri des colonnes. Par exemple, une requête possédant la clause ORDER BY `ORDER BY RejectedQty ASC, ProductID DESC` peut utiliser l'index.  
  
 L'ordre de tri ne peut être spécifié que pour les colonnes clés. L’affichage catalogue [sys.index_columns](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) et la fonction INDEXKEY_PROPERTY indiquent si une colonne d’index est stockée dans l’ordre croissant ou décroissant.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans ce Guide](#Top)  
  
##  <a name="Clustered"></a> Indications pour la conception d'index cluster  

 Les index cluster trient et stockent les lignes de données de la table en fonction de leurs valeurs de clé. Il n'y a qu'un index cluster par table car les lignes de données ne peuvent être triées que dans un seul ordre. À quelques exceptions près, toutes les tables doivent avoir un index cluster défini sur la ou les colonnes présentant les caractéristiques suivantes :  
  
-   utilisables pour les requêtes fréquemment utilisées ;  
  
-   assurant un niveau élevé d'unicité ;  
  
    > [!NOTE]  
    >  Lorsque vous créez une contrainte PRIMARY KEY, un index unique sur la ou les colonnes est automatiquement créé. Par défaut, cet index est cluster ; toutefois, vous pouvez spécifier un index non-cluster lorsque vous créez la contrainte.  
  
-   utilisables dans les requêtes de plage.  
  
 Si l'index cluster n'est pas créé avec la propriété UNIQUE, le [!INCLUDE[ssDE](../includes/ssde-md.md)] ajoute automatiquement une colonne d'indicateur d'unicité de 4 octets à la table. Si nécessaire, le [!INCLUDE[ssDE](../includes/ssde-md.md)] ajoute automatiquement une valeur d'indicateur d'unicité une ligne pour que chaque clé soit unique. Cette colonne et ses valeurs sont utilisées en interne et ne sont ni affichables, ni accessibles par les utilisateurs.  
  
### <a name="clustered-index-architecture"></a>Architecture des index cluster  

 Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], les index sont organisés en arborescences binaires. Chaque page d'une arborescence binaire d'index s'appelle un nœud d'index. Le nœud supérieur d'une arborescence binaire est le nœud racine. Les nœuds du niveau inférieur de l'index sont appelés les nœuds feuille. Tous les niveaux d'index situés entre la racine et les nœuds feuille s'appellent des niveaux intermédiaires. Dans un index cluster, les nœuds feuille contiennent les pages de données de la table sous-jacente. Les nœuds racine et de niveau intermédiaire contiennent les pages d'index dans lesquelles se trouvent les lignes d'index. Chaque ligne d'index contient une valeur de clé et un pointeur vers une page de niveau intermédiaire dans l'arborescence binaire ou vers une ligne de données dans le niveau feuille de l'index. Les pages de chaque niveau de l'index sont liées dans une liste à double liaison.  
  
 Un index cluster a une ligne dans [sys.partitions](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql), où **index_id** = 1 pour chaque partition utilisée par celui-ci. Par défaut, un index cluster possède une seule partition. Lorsqu'un index cluster détient plusieurs partitions, chacune d'elles possède une structure d'arborescence binaire qui contient ses données. Par exemple, si un index cluster possède quatre partitions, il existe quatre structures d'arborescence binaire, à raison d'une dans chaque partition.  
  
 Suivant les types de données de l'index cluster, chaque structure d'index cluster possède une ou plusieurs unités d'allocation pour le stockage et la gestion des données d'une partition spécifique. Au minimum, chaque index cluster détient une unité d'allocation IN_ROW_DATA par partition. L'index cluster possède également une unité d'allocation LOB_DATA par partition s'il contient des colonnes LOB (Large Object). En outre, il détient une unité d'allocation ROW_OVERFLOW_DATA par partition s'il contient des colonnes de longueur variable qui dépassent la limite de taille de ligne de 8 060 octets.  
  
 Les pages de la chaîne de données et les lignes qu'elles rassemblent sont organisées en fonction de la valeur de la clé d'index cluster. Toutes les insertions sont faites à l'endroit où la valeur de clé de la ligne insérée correspond parfaitement à la séquence de tri parmi les lignes existantes.  
  
 L'illustration suivante montre la structure d'un index cluster dans une partition unique.  
  
 ![Niveaux d’un index cluster](media/bokind2.gif "niveaux d’un index cluster")  
  
### <a name="query-considerations"></a>Remarques sur les requêtes  

 Avant de créer des index cluster, il est important de comprendre le mode d'accès aux données. Envisagez l'emploi d'un index cluster pour les requêtes qui :  
  
-   retournent une plage de valeurs en utilisant des opérateurs tels que BETWEEN, >, >=, < et <=.  
  
     Dès que la ligne comportant la première valeur est trouvée à l'aide de l'index cluster, les lignes présentant les valeurs indexées suivantes sont garanties comme étant adjacentes physiquement. Par exemple, si une requête extrait des enregistrements compris dans une plage de numéros de commandes, un index cluster sur la colonne `SalesOrderNumber` permet de localiser rapidement la ligne qui contient le premier numéro de commande, puis d'extraire toutes les lignes successives de la table jusqu'à ce que le dernier numéro de commande soit atteint.  
  
-   retournent des jeux de résultats volumineux ;  
  
-   utilisent des clauses JOIN ; ce sont en général des colonnes clés étrangères ;  
  
-   utilisent des clauses ORDER BY ou GROUP BY.  
  
     Si un index est présent sur les colonnes spécifiées dans la clause ORDER BY ou GROUP BY, le [!INCLUDE[ssDE](../includes/ssde-md.md)] n'a plus besoin de trier les données car les lignes le sont déjà. Les requêtes présentent dès lors des performances accrues.  
  
### <a name="column-considerations"></a>Remarques sur les colonnes  

 En général, vous devez définir la clé d'index cluster avec le moins de colonnes possible. Envisagez les colonnes présentant un ou plusieurs des attributs suivants :  
  
-   Colonnes uniques ou qui contiennent de nombreuses valeurs distinctes  
  
     Par exemple, l'ID d'un salarié l'identifie de manière unique. Un index cluster ou une contrainte PRIMARY KEY sur la colonne `EmployeeID` améliore les performances des requêtes qui recherchent des informations sur les salariés en fonction de leur ID. D'une autre manière, un index cluster peut être créé sur `LastName`, `FirstName`, `MiddleName` , car les enregistrements de salariés sont fréquemment groupés et interrogés de cette façon et l'association de ces colonnes présente toujours un niveau élevé de différenciation.  
  
-   Accès séquentiel des colonnes  
  
     Par exemple, l'ID d'un produit l'identifie de manière unique dans la table `Production.Product` de la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . Les requêtes dans lesquelles une recherche séquentielle est spécifiée, telles que `WHERE ProductID BETWEEN 980 and 999`, tireront parti d'un index cluster sur `ProductID`. car les lignes sont stockées dans l'ordre sur cette colonne clé.  
  
-   Défini comme IDENTITY.  
  
-   Colonnes fréquemment utilisées pour trier les données extraites d'une table  
  
     Il peut être judicieux de mettre en cluster, c'est-à-dire de trier physiquement, la table sur cette colonne pour économiser le coup d'une opération de tri à chaque fois que la colonne est interrogée.  
  
 Les index cluster sont déconseillés pour les colonnes présentant les attributs suivants :  
  
-   Les colonnes sujettes à des modifications fréquentes.  
  
     La ligne tout entière est ainsi déplacée, car le [!INCLUDE[ssDE](../includes/ssde-md.md)] doit conserver les valeurs des données de la ligne dans l'ordre physique. Cette observation est importante dans les systèmes de traitement transactionnel à haut volume où les données sont en général éphémères.  
  
-   Les clés étendues.  
  
     Les clés étendues sont composées de plusieurs colonnes ou plusieurs colonnes de grande taille. Les valeurs de clé de l'index cluster sont utilisées par tous les index non-cluster comme clés de recherche. Tous les index non-cluster définis sur la même table sont considérablement plus grands car leurs entrées contiennent la clé de cluster et aussi les colonnes clés définies pour cet index non-cluster.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans ce Guide](#Top)  
  
##  <a name="Nonclustered"></a> Indications pour la conception d'index non-cluster  

 Un index non-cluster contient les valeurs de clé d'index et les localisateurs de ligne qui pointent vers l'emplacement de stockage des données de table. Vous pouvez créer plusieurs index non cluster sur une table ou une vue indexée. Les index non-cluster doivent, en principe, améliorer les performances des requêtes fréquemment utilisées qui ne sont pas couvertes par l'index cluster.  
  
 De la même manière que vous utilisez un index dans un livre, l'optimiseur de requête recherche une valeur de données en examinant l'index non-cluster afin de trouver l'emplacement qu'occupe la valeur dans la table, puis récupère directement les données à partir de cet emplacement. C'est pour cette raison que les index non cluster constituent une solution idéale pour les requêtes à correspondance exacte ; l'index contient en effet des entrées décrivant l'emplacement exact qu'occupent dans la table les valeurs de données recherchées dans les requêtes. Par exemple, pour interroger la table `HumanResources. Employee` pour tous les employés qui réfèrent à un responsable spécifique, l'optimiseur de requête peut utiliser l'index non cluster `IX_Employee_ManagerID`; sa colonne clé est `ManagerID` . L'optimiseur de requête recherche rapidement toutes les entrées de l'index qui correspondent à la valeur `ManagerID`spécifiée. Chaque entrée d'index pointe vers la page et la ligne exactes de la table ou de l'index cluster contenant les données correspondantes. Après avoir trouvé toutes les entrées dans l'index, l'optimiseur de requête peut accéder directement à la page et à la ligne exactes pour récupérer les données.  
  
### <a name="nonclustered-index-architecture"></a>Architecture des index non cluster  

 Les index non-cluster possèdent la même structure arborescente binaire que les index cluster, à ces différences près :  
  
-   Les lignes de données de la table sous-jacente ne sont pas triées et stockées dans l'ordre des clés non cluster.  
  
-   La couche inférieure d'un index non-cluster n'est pas constituée de pages de données, mais de pages d'index.  
  
 Dans les lignes des index non-cluster, le localisateur est soit un pointeur vers une ligne, soit une clé d'index cluster :  
  
-   Si la table est un segment de mémoire (dépourvue d'index cluster), le localisateur de ligne est un pointeur vers la ligne. Le pointeur est construit à partir de l'ID du fichier, du numéro de la page et du numéro de ligne dans la page. Le pointeur complet est appelé une ID de ligne (RID).  
  
-   Si la table a un index cluster, ou si l'index est sur une vue indexée, le localisateur de ligne est la clé d'index cluster pour la ligne.  
  
 Les index non-cluster comprennent une ligne dans [sys.partitions](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) où **index_id** >1 pour chaque partition utilisée par l’index. Par défaut, un index non-cluster contient une seule partition. Lorsqu'un index non-cluster comprend plusieurs partitions, chaque partition a une structure arborescente binaire qui contient les lignes d'index correspondantes. Par exemple, si un index non-cluster a quatre partitions, il y a quatre arborescences binaires, une dans chaque partition.  
  
 En fonction des types de données de l'index non-cluster, chaque structure d'index non-cluster aura une ou plusieurs unités d'allocation dans lesquelles stocker et gérer les données d'une partition spécifique. Chaque index non-cluster aura au minimum une unité d'allocation IN_ROW_DATA par partition pour stocker les pages de l'arborescence binaire de l'index. L'index non-cluster aura également une unité d'allocation LOB_DATA par partition s'il contient des colonnes d'objets volumineux (LOB). Il aura par ailleurs une unité d'allocation ROW_OVERFLOW_DATA par partition s'il contient des colonnes de longueur variable dont les lignes dépassent 8 060 octets.  
  
 L'illustration suivante montre la structure d'un index non-cluster avec une seule partition.  
  
 ![Niveaux d’un index non-cluster](media/bokind1.gif "niveaux d’un index non-cluster")  
  
### <a name="database-considerations"></a>Remarques sur la base de données  

 Les caractéristiques de la base de données sont importantes lors de la conception d'index non-cluster.  
  
-   Les bases de données ou les tables dont les mises à jour sont faibles, mais qui contiennent des volumes importants de données peuvent tirer parti de nombreux index non-cluster en vue d'améliorer les performances des requêtes. Envisagez de créer des index filtrés pour les sous-ensembles de données bien définis afin d'améliorer les performances des requêtes, réduire les coûts de stockage d'index et réduire les coûts de maintenance d'index par rapport aux index non cluster de table entière.  
  
     Les applications et bases de données d'aide à la décision contenant principalement des données en lecture seule peuvent tirer parti de nombreux index non-cluster. L'optimiseur de requête doit choisir parmi davantage d'index pour déterminer la méthode d'accès la plus rapide ; les caractéristiques de mise à jour faible de la base de données sont synonymes d'une maintenance d'index qui n'entravera pas les performances.  
  
-   Les applications et bases de données OLTP (traitement transactionnel en ligne) qui contiennent des tables largement mises à jour doivent éviter la sur-indexation. Les index doivent en outre être réduits, c'est-à-dire contenir le moins de colonnes possible.  
  
     La définition de nombreux index sur une table affecte les performances des instructions INSERT, UPDATE, DELETE et MERGE , car à mesure que les données de la table changent, tous les index doivent être mis à jour en conséquence.  
  
### <a name="query-considerations"></a>Remarques sur les requêtes  

 Avant de créer des index non-cluster, vous devez comprendre comment se déroulera l'accès aux données. Il est conseillé d'utiliser un index non-cluster pour les requêtes avec les attributs suivants :  
  
-   Requêtes qui utilisent des clauses JOIN ou GROUP BY.  
  
     Créez plusieurs index non-cluster sur des colonnes impliquées dans les opérations de jointure et de regroupement, ainsi qu'un index cluster sur les colonnes clés étrangère éventuelles.  
  
-   Requêtes qui ne retournent pas des ensembles de résultats volumineux.  
  
     Créez des index filtrés pour couvrir les requêtes qui retournent un sous-ensemble bien défini de lignes d'une grande table.  
  
-   Requêtes qui contiennent des colonnes souvent impliquées dans les conditions de recherche d'une requête (clause WHERE) qui retournent des correspondances exactes.  
  
### <a name="column-considerations"></a>Remarques sur les colonnes  

 Il est conseillé d'utiliser des colonnes qui possèdent un ou plusieurs de ces attributs :  
  
-   Couvrent la requête.  
  
     Performances accrues lorsque l'index contient toutes les colonnes de la requête. L'optimiseur de requête peut localiser toutes les valeurs de colonnes dans l'index ; les données de table ou d'index cluster ne sont pas accédées, avec pour conséquence une réduction des opérations d'E/S disque. Utilisez un index avec colonnes incluses pour ajouter des colonnes de couverture au lieu de créer une clé d'index de grande taille.  
  
     Si la table a un index cluster, la ou les colonnes définies dans cet index sont automatiquement ajoutées à la fin de chaque index non-cluster de la table. Ceci peut produire une requête couverte sans spécifier les colonnes de l'index cluster dans la définition de l'index non-cluster. Par exemple, si une table a un index cluster sur la colonne `C`, un index non cluster sur les colonnes `B` et `A` aura comme valeurs de clé les colonnes `B`, `A`et `C`.  
  
-   Un nombre élevé de valeurs distinctes, comme une combinaison de nom et prénom, si un index cluster est utilisé pour d'autres colonnes.  
  
     Lorsqu'il existe très peu de valeurs distinctes (1 et 0 uniquement, par exemple), la plupart des requêtes utiliseront une analyse de table, généralement plus efficace, au lieu de l'index. Pour ce type de données, envisagez de créer un index filtré sur une valeur distincte qui se produit uniquement dans un petit nombre de lignes. Par exemple, si la plupart des valeurs sont 0, l'optimiseur de requête peut utiliser un index filtré pour les lignes de données qui contiennent 1.  
  
####  <a name="Included_Columns"></a> Utiliser des colonnes incluses pour étendre les index non cluster  

 Vous pouvez étendre la fonctionnalité des index non cluster en ajoutant des colonnes non-clés au niveau feuille de l'index non cluster. L'inclusion de colonnes non-clés permet de créer des index non-cluster qui couvrent davantage de requêtes. En effet, les colonnes non-clés présentent les avantages suivants :  
  
-   Elles peuvent contenir des types de données qui ne sont pas autorisés dans les colonnes de clés d'index.  
  
-   Elles ne sont pas prises en compte par le [!INCLUDE[ssDE](../includes/ssde-md.md)] lors du calcul du nombre de colonnes clés d'index ou de la taille de la clé d'index.  
  
 Un index contenant des colonnes non-clés incluses peut améliorer considérablement les performances des requêtes lorsque toutes les colonnes de la requête sont incluses dans l'index en tant que colonnes clés ou non-clés. Les gains de performances sont dus au fait que l'optimiseur de requête peut localiser toutes les valeurs des colonnes dans l'index ; l'accès aux données de table et d'index n'a pas lieu, produisant ainsi un nombre moindre d'opérations d'E/S sur le disque.  
  
> [!NOTE]  
>  Lorsqu'un index contient toutes les colonnes auxquelles la requête fait référence, on dit qu'il couvre la requête.  
  
 Alors que les colonnes clés sont stockées à tous les niveaux de l'index, les colonnes non-clés sont stockées uniquement au niveau feuille.  
  
##### <a name="using-included-columns-to-avoid-size-limits"></a>Utilisation de colonnes incluses pour éviter les limites de taille  

 Vous pouvez inclure des colonnes non-clés dans un index non cluster pour éviter de dépasser les limitations actuelles de taille d'index, établies à 16 colonnes clés au maximum et une taille de clé d'index de 900 octets au maximum. Le [!INCLUDE[ssDE](../includes/ssde-md.md)] ne tient pas compte des colonnes non-clés lors du calcul du nombre de colonnes clés d'index ou de la taille de la clé d'index.  
  
 Par exemple, supposons que vous voulez indexer les colonnes suivantes de la table `Document` :  
  
 `Title nvarchar(50)`  
  
 `Revision nchar(5)`  
  
 `FileName nvarchar(400)`  
  
 Comme les types de données `nchar` et `nvarchar` nécessitent deux octets par caractère, un index qui contient ces trois colonnes dépasse de 10 octets (455 * 2) la limitation de taille de 900 octets. En utilisant la clause `INCLUDE` de l'instruction `CREATE INDEX` , la clé d'index peut être définie en tant que (`Title, Revision`) et `FileName` en tant que colonne non-clé. De cette manière, la taille de la clé d’index vaut 110 octets (55 \* 2) et l’index contient toujours toutes les colonnes requises. L'instruction ci-dessous crée cet index.  
  
```sql
CREATE INDEX IX_Document_Title   
ON Production.Document (Title, Revision)   
INCLUDE (FileName);   
```  
  
##### <a name="index-with-included-columns-guidelines"></a>Directives sur les index contenant des colonnes incluses  

 Lors de la conception d'index non-cluster contenant des colonnes incluses, tenez compte des directives suivantes :  
  
-   Les colonnes non-clés sont définies dans la clause INCLUDE de l'instruction CREATE INDEX.  
  
-   Les colonnes non-clés peuvent être définies uniquement sur les index non-cluster de tables ou de vues indexées.  
  
-   Tous les types de données sont autorisés, à l'exception de `text`, `ntext` et `image`.  
  
-   Les colonnes calculées déterministes et précises ou imprécises peuvent être des colonnes incluses. Pour plus d'informations, consultez [Indexes on Computed Columns](../relational-databases/indexes/indexes-on-computed-columns.md).  
  
-   Comme pour les colonnes clés, les colonnes calculées dérivées des types de données `image`, `ntext` et `text` peuvent être des colonnes non-clés (incluses) tant que le type de données de la colonne calculée est autorisé en tant que colonne d'index non-clé.  
  
-   Les noms des colonnes ne peuvent pas être spécifiés à la fois dans la liste INCLUDE et dans la liste des colonnes clés.  
  
-   Les noms des colonnes ne peuvent pas être répétés dans la liste INCLUDE.  
  
##### <a name="column-size-guidelines"></a>Directives sur la taille des colonnes  
  
-   Vous devez spécifier au moins une colonne clé. Le nombre maximal de colonnes non-clés est de 1023. Il équivaut au nombre maximal de colonnes de table moins 1.  
  
-   Les colonnes de clés d'index, colonnes non-clés exclues, doivent respecter les restrictions existantes de taille d'index, à savoir 16 colonnes clés au maximum et une taille totale de clé d'index de 900 octets.  
  
-   La taille totale de toutes les colonnes non-clés est limitée uniquement par la taille des colonnes spécifiées dans la clause INCLUDE ; par exemple, les colonnes `varchar(max)` sont limitées à 2 Go.  
  
##### <a name="column-modification-guidelines"></a>Directives sur la modification des colonnes  

 Lors de la définition d'une colonne de table définie en tant que colonne incluse, les restrictions suivantes s'appliquent :  
  
-   Les colonnes non-clés ne peuvent pas être supprimées de la table, sauf si l'index est d'abord supprimé.  
  
-   Les colonnes non-clés ne peuvent pas être modifiées, sauf pour effectuer les opérations suivantes :  
  
    -   modifier la possibilité de valeur NULL de la colonne de NOT NULL à NULL ;  
  
    -   augmenter la longueur des colonnes `varchar`, `nvarchar` ou `varbinary`.  
  
        > [!NOTE]  
        >  Ces restrictions sur la modification des colonnes s'appliquent également aux colonnes de clés d'index.  
  
##### <a name="design-recommendations"></a>Recommandations relatives à la conception  

 La conception d'index non-cluster doit être réalisée avec une clé d'index de grande taille, de sorte que seules les colonnes utilisées pour la recherche sont les colonnes clés. Toutes les autres colonnes qui couvrent la requête doivent être des colonnes non-clés incluses. De cette manière, vous disposez de toutes les colonnes nécessaires pour couvrir la requête, mais la clé d'index elle-même est petite et efficace.  
  
 Par exemple, supposons que vous voulez concevoir un index qui couvre la requête ci-dessous.  
  
```sql
SELECT AddressLine1, AddressLine2, City, StateProvinceID, PostalCode  
FROM Person.Address  
WHERE PostalCode BETWEEN N'98000' and N'99999';  
```  
  
 Pour couvrir la requête, chaque colonne doit être définie dans l'index. Même si vous pouviez définir toutes les colonnes en tant que colonnes clés, la taille de clé serait 334 octets. Comme la seule colonne vraiment utilisée comme critère de recherche est la colonne `PostalCode` , dont la longueur vaut 30 octets, une meilleure conception d'index définirait `PostalCode` comme colonne clé et inclurait toutes les autres colonnes comme colonnes non-clés.  
  
 L'instruction suivante crée un index contenant des colonnes incluses pour couvrir la requête.  
  
```sql
CREATE INDEX IX_Address_PostalCode  
ON Person.Address (PostalCode)  
INCLUDE (AddressLine1, AddressLine2, City, StateProvinceID);  
```  
  
##### <a name="performance-considerations"></a>Considérations relatives aux performances  

 Évitez d'ajouter des colonnes superflues. L'ajout de trop nombreuses colonnes d'index, clés et non-clés, peut avoir les conséquences suivantes sur les performances :  
  
-   Le nombre de lignes d'index contenues sur une page sera moindre. Ceci pourrait augmenter les E/S et réduire l'efficacité de la mémoire cache.  
  
-   L'espace disque requis pour stocker l'index sera supérieur. En particulier, l'ajout des types de données `varchar(max)`, `nvarchar(max)`, `varbinary(max)` ou `xml` en tant que colonnes d'index non-clés peut accroître considérablement l'espace disque nécessaire. En effet, les valeurs des colonnes sont copiées dans le niveau feuille de l'index. Par conséquent, elles résident à la fois dans l'index et dans la table de base.  
  
-   La maintenance d'un index peut accroître la durée nécessaire pour effectuer des modifications, des insertions, des mises à jour ou des suppressions à la table sous-jacente ou à la vue indexée.  
  
 Vous devez déterminer si les gains de performances des requêtes compensent la dégradation des performances lors de la modification des données et la quantité d'espace disque supplémentaire nécessaire.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans ce Guide](#Top)  
  
##  <a name="Unique"></a> Instructions de conception d'index uniques  

 Un index unique garantit que la clé d'index ne contient aucune valeur dupliquée et que, par conséquent, chaque ligne de la table est unique d'une certaine manière. Spécifier un index unique n'a de sens que si l'unicité est une caractéristique des données elles-mêmes. Par exemple, si vous souhaitez que les valeurs de la colonne `NationalIDNumber` de la table `HumanResources.Employee` soient uniques, lorsque la clé primaire est `EmployeeID`, créez une contrainte UNIQUE sur la colonne `NationalIDNumber` . Si l'utilisateur essaie de saisir la même valeur dans cette colonne pour plusieurs employés, un message d'erreur apparaît et la valeur dupliquée n'est pas entrée.  
  
 Lorsque vous utilisez un index unique multicolonne, celui-ci garantit que chaque combinaison de valeurs dans la clé d'index est unique. Par exemple, si un index unique est créé sur une combinaison des colonnes `LastName`, `FirstName`et `MiddleName` , deux lignes de la table ne peuvent pas posséder la même combinaison de valeurs pour ces colonnes.  
  
 Tant les index cluster que les index non-cluster peuvent être uniques. À condition que les données contenues dans la colonne soient uniques, vous pouvez créer à la fois un index cluster unique et plusieurs index non-cluster uniques sur la même table.  
  
 Les index uniques présentent les avantages suivants :  
  
-   L'intégrité des données des colonnes définies est garantie.  
  
-   L'optimiseur de requête dispose d'informations utiles supplémentaires.  
  
 Lorsque vous créez une contrainte PRIMARY KEY ou UNIQUE, vous créez automatiquement un index unique sur les colonnes spécifiées. Il n'y a pas de différences significatives entre la création d'une contrainte UNIQUE et la création d'un index unique indépendant d'une contrainte. La validation des données se produit de la même manière et l'optimiseur de requête considère un index unique de la même façon, qu'il soit créé par une contrainte or manuellement. Toutefois, vous devez créer une contrainte UNIQUE ou PRIMARY KEY sur la colonne lorsque votre objectif est de préserver l'intégrité des données. Cette opération met en évidence la finalité de l'index.  
  
### <a name="considerations"></a>Observations  
  
-   Un index unique, une contrainte UNIQUE ou une contrainte PRIMARY KEY ne peuvent pas être créés si les données comportent des valeurs de clé dupliquées.  
  
-   Si les données sont uniques et que l'unicité doit être assurée, la création d'un index unique au lieu d'un index non unique sur la même combinaison de colonnes fournit des informations supplémentaires à l'optimiseur de requête, qui peut générer des plans d'exécution plus efficaces. La création d'un index unique (si possible en créant une contrainte UNIQUE) est recommandée dans ce cas.  
  
-   Un index non cluster unique peut contenir des colonnes non-clés incluses. Pour plus d'informations, consultez [Index avec colonnes incluses](#Included_Columns).  
  
 ![Icône de flèche utilisée avec le lien Retour au début](media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans ce Guide](#Top)  
  
##  <a name="Filtered"></a> Instructions de conception d'index filtrés  

 Un index filtré est un index non cluster optimisé, convenant tout particulièrement aux requêtes qui effectuent des sélections dans un sous-ensemble de données bien défini. Il utilise un prédicat de filtre pour indexer une partie des lignes de la table. Un index filtré bien conçu peut améliorer les performances des requêtes, réduire les coûts de maintenance des index et réduire les coûts de stockage des index par rapport aux index de table entière.  
  
||  
|-|  
|**S'applique à**: [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|  
  
 Les index filtrés peuvent présenter les avantages suivants par rapport aux index de table entière :  
  
-   **Meilleures performances des requêtes et qualité de plan améliorée**  
  
     Un index filtré bien conçu améliore les performances des requêtes et la qualité du plan d'exécution car il est plus petit qu'un index non cluster de table entière et contient des statistiques filtrées. Les statistiques filtrées sont plus précises que les statistiques de table entière car elles couvrent uniquement les lignes de l'index filtré.  
  
-   **Coûts réduits de maintenance des index**  
  
     La maintenance d'un index intervient uniquement lorsque les instructions de langage de manipulation de données (DML) affectent les données de l'index. Un index filtré réduit les coûts de maintenance des index par rapport à un index non cluster de table entière car il est plus petit et est demande une maintenance uniquement lorsque les données de l'index sont affectées. Il est possible d'avoir un grand nombre d'index filtrés, notamment s'ils contiennent des données qui sont rarement affectées. De la même façon, si un index filtré contient uniquement les données fréquemment affectées, la plus petite taille de l'index réduit le coût de la mise à jour des statistiques.  
  
-   **Coûts réduits de stockage des index**  
  
     La création d'un index filtré peut réduire le stockage sur disque des index non cluster lorsqu'un index de table entière n'est pas nécessaire. Vous pouvez remplacer un index non cluster de table entière par plusieurs index filtrés sans augmenter considérablement le stockage nécessaire.  
  
 Les index filtrés sont utiles lorsque les colonnes contiennent des sous-ensembles bien définis de données qui sont référencés par des requêtes dans des instructions SELECT. Exemples :  
  
-   Colonnes éparses qui contiennent uniquement quelques valeurs non NULL.  
  
-   Colonnes hétérogènes qui contiennent des catégories de données.  
  
-   Colonnes qui contiennent des plages de valeurs, telles que des montants en devise, des heures et des dates.  
  
-   Partitions de table définies par une logique de comparaison simple pour les valeurs de colonne.  
  
 La réduction des coûts de maintenance pour les index filtrés est plus particulièrement notable lorsque le nombre de lignes de l'index est petit comparé à un index de table entière. Si l'index filtré inclut la plupart des lignes de la table, son coût de maintenance risque d'être plus élevé que celui d'un index de table entière. Dans ce cas, vous devez utiliser un index de table entière à la place d'un index filtré.  
  
 Les index filtrés sont définis sur une seule table et ne prennent en charge que les opérateurs de comparaison simples. Si vous avez besoin d'une expression de filtre qui référence plusieurs tables ou présente une logique complexe, vous devez créer une vue.  
  
### <a name="design-considerations"></a>Remarques sur la conception  

 Pour concevoir des index filtrés efficaces, il est important de comprendre les requêtes utilisées par votre application et leurs relations avec les sous-ensembles de données. Les colonnes contenant principalement des valeurs NULL, les colonnes contenant des catégories hétérogènes de valeurs et les colonnes contenant des plages de valeurs distinctes sont autant d'exemples de données avec des sous-ensembles bien définis. Les considérations suivantes relatives à la conception présentent divers scénarios dans lesquels un index filtré peut présenter des avantages par rapport à des index de table entière.  
  
#### <a name="filtered-indexes-for-subsets-of-data"></a>Index filtrés pour des sous-ensembles de données  

 Lorsqu'une colonne contient seulement un petit nombre de valeurs pertinentes pour les requêtes, vous pouvez créer un index filtré sur ce sous-ensemble de valeurs. Ainsi, lorsque les valeurs d'une colonne sont principalement NULL et que la requête effectue uniquement des sélections dans les valeurs non NULL, vous pouvez créer un index filtré pour les lignes de données non NULL. L'index ainsi créé sera plus petit et coûtera moins cher en maintenance qu'un index non cluster de table entière défini sur les mêmes colonnes clés.  
  
 Par exemple, la base de données `AdventureWorks2012` a une table `Production.BillOfMaterials` avec 2679 lignes. Seules 199 lignes de la colonne `EndDate` contiennent une valeur non NULL ; les 2480 autres contiennent des valeurs NULL. L'index filtré suivant couvre les requêtes qui retournent les colonnes définies dans l'index et qui sélectionnent uniquement les lignes avec une valeur non NULL pour `EndDate`.  
  
```sql
CREATE NONCLUSTERED INDEX FIBillOfMaterialsWithEndDate  
    ON Production.BillOfMaterials (ComponentID, StartDate)  
    WHERE EndDate IS NOT NULL ;  
GO  
```  
  
 L'index filtré `FIBillOfMaterialsWithEndDate` est valide pour la requête suivante. Vous pouvez afficher le plan d'exécution de la requête pour déterminer si l'optimiseur de requête a utilisé l'index filtré.  
  
```sql
SELECT ProductAssemblyID, ComponentID, StartDate   
FROM Production.BillOfMaterials  
WHERE EndDate IS NOT NULL   
    AND ComponentID = 5   
    AND StartDate > '20080101' ;  
```  
  
 Pour plus d'informations sur la création d'index filtrés et la définition de l'expression de prédicat d'index filtré, consultez [Create Filtered Indexes](../relational-databases/indexes/create-filtered-indexes.md).  
  
#### <a name="filtered-indexes-for-heterogeneous-data"></a>Index filtrés pour les données hétérogènes  

 Lorsqu'une table contient des lignes des données hétérogènes, vous pouvez créer un index filtré pour une ou plusieurs catégories de données.  
  
 Par exemple, chacun des produits répertoriés dans la table `Production.Product` est affecté à un `ProductSubcategoryID`, qui est à son tour associé à une catégorie de produits (Bikes, Components, Clothing ou Accessories). Ces catégories sont hétérogènes car leurs valeurs de colonne dans la table `Production.Product` ne sont pas étroitement corrélées. Par exemple, les colonnes `Color`, `ReorderPoint`, `ListPrice`, `Weight`, `Class`et `Style` ont des caractéristiques uniques pour chaque catégorie de produit. Supposons que des requêtes portent fréquemment sur la catégorie Accessories qui comporte les sous-catégories 27-36. Améliorez les performances des requêtes portant sur Accessories en créant un index filtré sur les sous-catégories de la catégorie Accessories, tel que l'illustre l'exemple suivant.  
  
```sql
CREATE NONCLUSTERED INDEX FIProductAccessories  
    ON Production.Product (ProductSubcategoryID, ListPrice)   
        Include (Name)  
WHERE ProductSubcategoryID >= 27 AND ProductSubcategoryID <= 36;
```  
  
 L'index filtré `FIProductAccessories` couvre la requête suivante, car les résultats de la requête  
  
 sont contenus dans l'index et le plan de requête n'inclut pas de recherche de table de base. Par exemple, l'expression de prédicat de requête `ProductSubcategoryID = 33` est un sous-ensemble du prédicat d'index filtré `ProductSubcategoryID >= 27` et `ProductSubcategoryID <= 36`, les colonnes `ProductSubcategoryID` et `ListPrice` dans le prédicat de requête sont toutes deux des colonnes clés dans l'index et le nom est stocké au niveau feuille de l'index en tant que colonne incluse.  
  
```sql
SELECT Name, ProductSubcategoryID, ListPrice  
FROM Production.Product  
WHERE ProductSubcategoryID = 33 AND ListPrice > 25.00 ;  
```  
  
#### <a name="key-columns"></a>Colonnes clés  

 Il est recommandé d'inclure un petit nombre de colonnes clés ou incluses dans une définition d'index filtré, et d'incorporer uniquement les colonnes qui sont nécessaires à l'optimiseur de requête pour choisir l'index filtré pour le plan d'exécution de la requête. L'optimiseur de requête peut choisir un index filtré pour la requête, qu'il couvre ou non la requête. Toutefois, l'optimiseur de requête choisira plus probablement un index filtré s'il couvre la requête.  
  
 Dans certains cas, un index filtré couvre la requête sans inclure les colonnes de l'expression d'index filtré en tant que colonnes clés ou incluses dans la définition de l'index filtré. Les règles suivantes expliquent dans quels cas une colonne de l'expression d'index filtré doit être une colonne clé ou incluse dans la définition de l'index filtré. Les exemples font référence à l'index filtré `FIBillOfMaterialsWithEndDate` qui a été créé précédemment.  
  
 Il n'est pas nécessaire qu'une colonne de l'expression d'index filtré soit une colonne clé ou incluse dans la définition de l'index filtré si l'expression d'index filtré est équivalente au prédicat de requête et si la requête ne retourne pas la colonne dans l'expression d'index filtré avec les résultats de la requête. Par exemple, l'index filtré `FIBillOfMaterialsWithEndDate` couvre la requête suivante car le prédicat de la requête est équivalent à l'expression de filtre et `EndDate` n'est pas retourné avec les résultats de la requête. `FIBillOfMaterialsWithEndDate` n'a pas besoin de la colonne `EndDate` comme colonne clé ou incluse dans la définition de l'index filtré.  
  
```sql
SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
WHERE EndDate IS NOT NULL;   
```  
  
 Une colonne de l'expression d'index filtré doit être une colonne clé ou incluse dans la définition de l'index filtré si le prédicat de la requête utilise cette colonne dans une comparaison qui n'est pas équivalente à l'expression d'index filtré. Par exemple, l'index filtré `FIBillOfMaterialsWithEndDate` est valide pour la requête suivante car il sélectionne un sous-ensemble de lignes dans l'index filtré. Toutefois, il ne couvre pas la requête suivante, car `EndDate` est utilisé dans la comparaison `EndDate > '20040101'`, qui n'est pas équivalente à l'expression d'index filtré. Le processeur de requête ne peut pas exécuter cette requête sans rechercher les valeurs de `EndDate`. Par conséquent, `EndDate` doit être une colonne clé ou incluse dans la définition de l'index filtré.  
  
```sql
SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
WHERE EndDate > '20040101';   
```  
  
 Une colonne de l'expression d'index filtré doit être une colonne clé ou incluse dans la définition de l'index filtré si la colonne se trouve dans le jeu de résultats de la requête. Par exemple, l'index filtré `FIBillOfMaterialsWithEndDate` ne couvre pas la requête suivante car il retourne la colonne `EndDate` dans les résultats de la requête. Par conséquent, `EndDate` doit être une colonne clé ou incluse dans la définition de l'index filtré.  
  
```sql
SELECT ComponentID, StartDate, EndDate FROM Production.BillOfMaterials  
WHERE EndDate IS NOT NULL;  
```  
  
 Il n'est pas nécessaire que la clé de l'index cluster de la table soit une colonne clé ou incluse dans la définition de l'index filtré. La clé de l'index cluster est automatiquement incluse dans tous les index non cluster, y compris les index filtrés.  
  
#### <a name="data-conversion-operators-in-the-filter-predicate"></a>Opérateurs de conversion de données dans le prédicat du filtre  

 Si l'opérateur de comparaison spécifié dans l'expression d'index filtré de l'index filtré provoque une conversion de données implicite ou explicite, une erreur se produit si cette conversion se produit du côté gauche d'un opérateur de comparaison. Une solution consiste à écrire l'expression d'index filtré avec l'opérateur de conversion de données (CAST ou CONVERT) à droite de l'opérateur de comparaison.  
  
 L'exemple suivant crée une table avec différents types de données.  
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE dbo.TestTable (a int, b varbinary(4));  
```  
  
 Dans la définition d'index filtré suivante, la colonne `b` est implicitement convertie en type de données integer afin de la comparer à la constante 1. Le message d'erreur 10611 est alors généré car la conversion se produit à gauche de l'opérateur dans le prédicat filtré.  
  
```sql
CREATE NONCLUSTERED INDEX TestTabIndex ON dbo.TestTable(a,b)  
WHERE b = 1;  
```  
  
 La solution consiste à convertir la constante qui se trouve à droite de manière à ce que son type soit identique à celui de la colonne `b`, comme dans l'exemple suivant :  
  
```sql
CREATE INDEX TestTabIndex ON dbo.TestTable(a,b)  
WHERE b = CONVERT(Varbinary(4), 1);  
```  
  
 Le fait de déplacer la conversion de données de la gauche vers la droite d'un opérateur de comparaison peut modifier la signification de la conversion. Dans l'exemple ci-dessus, lorsque l'opérateur CONVERT a été ajouté à droite, la comparaison de type integer est devenue une comparaison de type `varbinary`.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](media/uparrow16x16.gif "icône de flèche utilisée avec le lien Retour au début") [dans ce Guide](#Top)  
  
##  <a name="Additional_Reading"></a> Lecture supplémentaire  

 [Amélioration des performances avec les vues indexées SQL Server 2008](https://msdn.microsoft.com/library/dd171921(v=sql.100).aspx)  
  
 [Partitioned Tables and Indexes](../relational-databases/partitions/partitioned-tables-and-indexes.md)  
  
  
