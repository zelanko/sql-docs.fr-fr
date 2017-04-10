---
title: "Vue d’ensemble et sc&#233;narios d’utilisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62c964c5-eae4-4cf1-9024-d5a19adbd652
caps.latest.revision: 5
author: "jodebrui"
ms.author: "jodebrui"
manager: "jhubbard"
caps.handback.revision: 5
---
# Vue d’ensemble et sc&#233;narios d’utilisation
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

OLTP en mémoire est la technologie de premier plan disponible dans SQL Server et Azure SQL Database pour optimiser les performances du traitement transactionnel, l’intégration et le chargement des données, et les scénarios de données temporaires. Cette rubrique inclut une vue d’ensemble de cette technologie et une présentation des scénarios d’utilisation de l’OLTP en mémoire. Grâce à ces informations, vous pourrez déterminer si l’OLTP en mémoire est adapté à votre application. À la fin de cette rubrique, vous trouverez un exemple illustrant les objets de l’OLTP en mémoire, ainsi que des liens vers une démonstration des performances de cette technologie et vers des ressources que vous pourrez utiliser pour la suite.


## <a name="in-memory-oltp-overview"></a>Vue d’ensemble de l’OLTP en mémoire

L’OLTP en mémoire peut offrir des gains de performance considérables pour les charges de travail appropriées. En tirant parti de l’OLTP en mémoire, un client, bwin, a réussi à [atteindre 1,2 million de requêtes par seconde](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/) avec un seul ordinateur exécutant SQL Server 2016. Un autre client, Quorum, est parvenu à doubler sa charge de travail tout en [réduisant son utilisation des ressources de 70 %](https://customers.microsoft.com/en-US/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database) en exploitant l’OLTP en mémoire disponible dans Azure SQL Database. Si certains clients ont pu observer une multiplication de leurs performances par 30 dans certains cas, les gains constatés dépendent de la charge de travail.

Mais d’où proviennent exactement ces gains de performance ? En substance, l’OLTP en mémoire améliore les performances de traitement transactionnel en rendant l’accès aux données et l’exécution des transactions plus efficaces, et en supprimant la contention de verrous et de verrous internes entre les transactions exécutées simultanément. Cette technologie n’est pas rapide parce qu’elle est en mémoire, mais parce qu’elle est optimisée à travers la présence des données en mémoire. Les algorithmes de stockage des données, d’accès et de traitement ont été entièrement repensés pour tirer parti des dernières améliorations en matière de calcul en mémoire et haute simultanéité.

Le fait que les données se trouvent en mémoire ne signifie pas pour autant que vous les perdez en cas de défaillance. Par défaut, toutes les transactions présentent une durabilité complète. Vous bénéficiez donc des mêmes garanties de durabilité que pour toute autre table de SQL Server : dans le cadre de la validation de transaction, toutes les modifications sont écrites dans le journal des transactions sur le disque. Si une défaillance survient après la validation de la transaction, vos données sont présentes lorsque la base de données est remise en ligne. En outre, l’OLTP en mémoire est compatible avec toutes les fonctionnalités de haute disponibilité et de récupération d’urgence de SQL Server, telles qu’AlwaysOn, la sauvegarde/restauration, etc.

Pour tirer parti de l’OLTP en mémoire dans votre base de données, vous devez utiliser un ou plusieurs des types d’objets suivants :

- Les *tables optimisées en mémoire* servent à stocker les données utilisateur. Vous déclarez qu’une table doit être optimisée en mémoire au moment de sa création.
- Les *tables non durables* sont utilisées pour les données temporaires, soit pour la mise en cache, soit pour le jeu de résultats intermédiaire (à la place des tables temporaires traditionnelles). Une table non durable est une table optimisée en mémoire qui est déclarée avec DURABILITY=SCHEMA_ONLY, ce qui veut dire que les modifications apportées à ces tables n’entraînent aucune E/S. Cela évite la consommation de ressources d’E/S de journal lorsque la durabilité n’est pas un critère important.
- Les *types de tables optimisées en mémoire* sont utilisés pour les paramètres table, ainsi que pour les jeux de résultats intermédiaires dans les procédures stockées. Ils peuvent être utilisés au lieu des types de tables traditionnels. Les variables de table et les paramètres table qui sont déclarés à l’aide d’un type de table optimisée en mémoire héritent des avantages des tables optimisées en mémoire non durables : accès efficace aux données et absence d’E/S.
- Les *modules T-SQL compilés en mode natif* permettent d’accélérer encore plus l’exécution d’une transaction individuelle en réduisant les cycles processeur requis pour traiter les opérations. Vous déclarez qu’un module Transact-SQL doit être compilé en mode natif au moment de sa création. À l’heure actuelle, les modules T-SQL suivants peuvent être compilés en mode natif : procédures stockées, déclencheurs et fonctions scalaires définies par l’utilisateur.

L’OLTP en mémoire est intégré dans SQL Server et Azure SQL Database. Et étant donné que ces objets se comportent de façon très similaire à leurs homologues traditionnels, vous pouvez souvent bénéficier de performances améliorées en apportant seulement des modifications minimes à la base de données et à l’application. De plus, vous pouvez avoir des tables optimisées en mémoire et des tables sur disque traditionnelles dans la même base de données, et exécuter simultanément des requêtes sur ces deux types de tables. Vous trouverez un script Transact-SQL présentant un exemple pour chacun de ces types d’objets à la fin de cette rubrique.

## <a name="usage-scenarios-for-in-memory-oltp"></a>Scénarios d’utilisation pour l’OLTP en mémoire

L’OLTP en mémoire n’est pas un bouton d’accélération magique et ne convient pas à toutes les charges de travail. Par exemple, les tables optimisées en mémoire ne réduiront pas vraiment l’utilisation du processeur si la plupart des requêtes effectuent des opérations d’agrégation sur des plages importantes de données (les index Columnstore sont d’une grande aide pour ce scénario).

Voici une liste de scénarios et de modèles d’application pour lesquels des clients ont pu tirer profit de l’OLTP en mémoire.

### <a name="high-throughput-and-low-latency-transaction-processing"></a>Traitement transactionnel à débit élevé et latence faible

C’est le scénario principal pour lequel nous avons créé l’OLTP en mémoire : prendre en charge de grands volumes de transactions, avec une latence faible homogène pour les transactions individuelles.

Les scénarios de charge de travail les plus fréquents sont les suivants : négoce d’instruments financiers, paris sportifs, jeux mobiles et diffusion publicitaire. Un autre modèle courant observé est un « catalogue » souvent lu ou mis à jour. Par exemple, vous disposez de fichiers volumineux, chacun réparti sur un certain nombre de nœuds dans un cluster, et vous cataloguez l’emplacement de chaque partition de fichier dans une table optimisée en mémoire.

#### <a name="implementation-considerations"></a>Considérations relatives à la mise en œuvre

Utilisez des tables optimisées en mémoire pour vos tables de transactions principales, c’est-à-dire pour les tables qui présentent les transactions les plus critiques pour les performances. Utilisez des procédures stockées compilées en mode natif pour optimiser l’exécution de la logique associée à la transaction commerciale. Plus vous pourrez transmettre la logique aux procédures stockées de la base de données, plus vous tirerez profit de l’OLTP en mémoire.

Pour commencer avec une application existante :
1. Utilisez le [rapport d’analyse des performances de transaction](https://msdn.microsoft.com/library/dn205133.aspx) pour identifier les objets à migrer. 
2. Utilisez le [Conseiller d’optimisation de la mémoire](https://msdn.microsoft.com/library/dn284308.aspx) et le [Conseiller de compilation native](https://msdn.microsoft.com/library/dn358355.aspx) pour faciliter la migration.

#### <a name="customer-case-studies"></a>Études de cas clients

- CMC Markets tire parti de l’OLTP en mémoire dans SQL Server 2016 pour obtenir une latence faible homogène : [Because a second is too long to wait, this financial services firm is updating its trading software now](https://customers.microsoft.com/en-us/story/because-a-second-is-too-long-to-wait-this-financial-services-firm-is-updating-its-trading-software) (Une seconde étant un délai d’attente trop long, ce cabinet de services financiers met à jour son logiciel de trading maintenant)
- Derivco tire parti de l’OLTP en mémoire dans SQL Server 2016 pour prendre en charge le surcroît de débit et gérer les pics de charge de travail : [When an online gaming company doesn’t want to risk its future, it bets on SQL Server 2016](https://customers.microsoft.com/en-us/story/when-an-online-gaming-company-doesnt-want-to-risk-its-future-it-bets-on-sql-server-2016) (Lorsqu’une entreprise de jeux en ligne ne veut pas mettre son avenir en danger, elle parie sur SQL Server 2016)


### <a name="data-ingestion-including-iot-internet-of-things"></a>Intégration de données, IoT (Internet des objets) compris

L’OLTP en mémoire est très efficace pour intégrer en même temps d’importants volumes de données provenant de nombreuses sources différentes. Et il est souvent plus intéressant d’intégrer des données dans une base de données SQL Server que dans d’autres destinations, car SQL assure une exécution très rapide des requêtes sur les données et vous permet d’en extraire des informations en temps réel.

Les modèles d’application courants sont les suivants : intégration de relevés et d’événements de capteurs à des fins de notification et d’analyse d’historique ; gestion des mises à jour par lot, même à partir de plusieurs sources, tout en réduisant l’impact sur la charge de travail de lecture simultanée.

#### <a name="implementation-considerations"></a>Considérations relatives à la mise en œuvre

Utilisez une table optimisée en mémoire pour l’intégration de données. Si l’intégration consiste principalement en des insertions (plutôt que des mises à jour) et l’encombrement de stockage des données dans l’OLTP en mémoire est un critère important :

- Utilisez un travail pour décharger régulièrement les données par lot dans une table sur disque comportant un [index Columnstore cluster](https://msdn.microsoft.com/library/gg492088.aspx), à l’aide d’un travail qui exécute `INSERT INTO <disk-based table> SELECT FROM <memory-optimized table>` ; ou
- Utilisez une [table optimisée en mémoire temporelle ](https://msdn.microsoft.com/library/mt590207.aspx) pour gérer les données d’historique ; dans ce mode, les données d’historique se trouvent sur le disque et le déplacement des données est géré par le système.

Le référentiel d’exemples SQL Server contient une application de réseau de distribution d’électricité intelligent qui utilise une table optimisée en mémoire temporelle, un type de table optimisée en mémoire et une procédure stockée compilée en mode natif afin d’accélérer l’intégration de données tout en gérant l’encombrement de stockage des données de capteur dans l’OLTP en mémoire : 

 - [smart-grid-release](https://github.com/Microsoft/sql-server-samples/releases/tag/iot-smart-grid-v1.0) 
 - [smart-grid-source-code](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/iot-smart-grid)
 
#### <a name="customer-case-studies"></a>Études de cas clients

- [Quorum doubles key database’s workload while lowering utilization by 70% by leveraging In-Memory OLTP in Azure SQL Database](http://customers.microsoft.com/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database) (Quorum double la charge de travail de sa base de données principale tout en diminuant l’utilisation de 70 % en tirant parti de l’OLTP en mémoire dans Azure SQL Database)
- EdgeNet a amélioré les performances de chargement de données par lot et supprimé la nécessité de maintenir un cache de niveau intermédiaire grâce à l’OLTP en mémoire dans SQL Server 2014 : [Data Services Firm Gains Real-Time Access to Product Data with In-Memory Technology](https://customers.microsoft.com/en-us/story/data-services-firm-gains-real-time-access-to-product-d) (Une entreprise de services de données profite d’un accès en temps réel aux données de produits grâce à une technologie en mémoire)
- L’établissement Beth Israel Deaconess Medical Center a pu améliorer considérablement la vitesse d’intégration des données des contrôleurs de domaine et gère efficacement les pics de charge de travail à l’aide de l’OLTP en mémoire dans SQL Server 2014 : [https://customers.microsoft.com/en-us/story/strengthening-data-security-and-creating-more-time-for]

### <a name="caching-and-session-state"></a>Mise en cache et état de session

La technologie d’OLTP en mémoire rend SQL vraiment intéressant pour le maintien de l’état de session (par exemple, pour une application ASP.NET) et pour la mise en cache.

L’état de session ASP.NET est un cas d’utilisation très efficace pour l’OLTP en mémoire. Avec SQL Server, un client est parvenu à atteindre 1,2 million de requêtes par seconde. Dans le même temps, il a commencé à utiliser l’OLTP en mémoire pour les besoins de mise en cache de toutes les applications de niveau intermédiaire de l’entreprise. Détails : [How bwin is using SQL Server 2016 In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/) (Comment bwin utilise la technologie OLTP en mémoire de SQL Server 2016 pour atteindre des performances et un nombre d’utilisateurs sans précédent)

#### <a name="implementation-considerations"></a>Considérations relatives à la mise en œuvre

Vous pouvez utiliser les tables optimisées en mémoire non durables en tant que magasin clé-valeur simple en stockant un objet blob dans une colonne varbinary(max). Vous pouvez également implémenter un cache semi-structuré avec [prise en charge JSON](https://azure.microsoft.com/blog/json-support-is-generally-available-in-azure-sql-database/) dans SQL Server et Azure SQL Database. Enfin, vous pouvez créer un cache relationnel complet via des tables non durables présentant un schéma relationnel complet, avec divers types et contraintes de données.

Pour bien démarrer avec l’état de session ASP.NET optimisé en mémoire, tirez parti des scripts publiés sur GitHub pour remplacer les objets créés par le fournisseur d’état de session intégré de SQL Server :

- [aspnet-session-state](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/aspnet-session-state)

#### <a name="customer-case-studies"></a>Études de cas clients

- bwin est parvenu à considérablement augmenter le débit et réduire l’encombrement matériel pour l’état de session ASP.NET avec l’OLTP en mémoire dans SQL Server 2014 : [Gaming Site Can Scale to 250,000 Requests Per Second and Improve Player Experience](https://customers.microsoft.com/en-us/story/gaming-site-can-scale-to-250000-requests-per-second-an) (Un site de jeux peut prendre en charge jusqu’à 250 000 requêtes par seconde afin d’optimiser l’expérience des joueurs)
- bwin a augmenté encore plus le débit avec l’état de session ASP.NET et implémenté un système de mise en cache de niveau intermédiaire à l’échelle de l’entreprise grâce à l’OLTP en mémoire dans SQL Server 2016 : [How bwin is using SQL Server 2016 In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/) (Comment bwin utilise la technologie OLTP en mémoire de SQL Server 2016 pour atteindre des performances et un nombre d’utilisateurs sans précédent)

### <a name="tempdb-object-replacement"></a>Remplacement d’objet tempdb

Tirez parti des tables non durables et des types de tables optimisées en mémoire pour remplacer vos tables #temp basées sur tempdb, variables de table et paramètres table traditionnels.

Les variables de table et les tables non durables optimisées en mémoire réduisent généralement l’utilisation du processeur par rapport aux variables de table et aux tables #temp traditionnels, et suppriment complètement les E/S de journal.



#### <a name="implementation-considerations"></a>Considérations relatives à la mise en œuvre

Pour bien démarrer, consultez : [Improving temp table and table variable performance using memory optimization.](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/) (Amélioration des performances des tables temporaires et des variables de table à l’aide de l’optimisation de la mémoire)

#### <a name="customer-case-studies"></a>Études de cas clients

- Un client est parvenu à améliorer les performances de 40 % simplement en remplaçant les paramètres table traditionnels par des paramètres table optimisés en mémoire : [High Speed IoT Data Ingestion Using In-Memory OLTP in Azure](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/04/07/a-technical-case-study-high-speed-iot-data-ingestion-using-in-memory-oltp-in-azure/) (Intégration de données IoT haute vitesse à l’aide de l’OLTP en mémoire dans Azure)


### <a name="etl-extract-transform-load"></a>ETL (extraction, transformation, chargement)

Les flux de travail ETL incluent souvent le chargement de données dans une table de mise en lots, les transformations de données et le chargement dans les tables finales.

#### <a name="implementation-considerations"></a>Considérations relatives à la mise en œuvre

Utilisez des tables optimisées en mémoire non durables pour la mise en lots des données. Elles suppriment complètement les E/S et optimisent l’efficacité de l’accès aux données.

Si vous effectuez des transformations sur la table de mise en lots dans le cadre du flux de travail, vous pouvez utiliser des procédures stockées compilées en mode natif pour accélérer ces transformations. Si vous pouvez procéder à ces transformations en parallèle, l’optimisation de la mémoire vous offre des avantages supplémentaires en matière de mise à l’échelle.

## <a name="sample-script"></a>Exemple de script

Avant de pouvoir commencer à utiliser l’OLTP en mémoire, vous devez créer un groupe de fichiers MEMORY_OPTIMIZED_DATA. Nous vous recommandons également d’utiliser le niveau de compatibilité de base de données 130 (ou supérieur) et de définir l’option de base de données MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT sur ON.

Vous pouvez utiliser le script situé à l’emplacement suivant pour créer le groupe de fichiers dans le dossier de données par défaut et configurer les paramètres recommandés :

- [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)

Le script suivant illustre les objets de l’OLTP en mémoire que vous pouvez créer dans votre base de données :
  
     -- configure recommended DB option
     ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
     GO
     -- memory-optimized table
     CREATE TABLE dbo.table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- non-durable table
     CREATE TABLE dbo.temp_table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON,
           DURABILITY=SCHEMA_ONLY)
     GO
     -- memory-optimized table type
     CREATE TYPE dbo.tt_table1 AS TABLE
     ( c1 INT IDENTITY,
       c2 NVARCHAR(MAX),
       is_transient BIT NOT NULL DEFAULT (0),
       INDEX ix_c1 HASH (c1) WITH (BUCKET_COUNT=1024))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- natively compiled stored procedure
     CREATE PROCEDURE dbo.usp_ingest_table1
       @table1 dbo.tt_table1 READONLY
     WITH NATIVE_COMPILATION, SCHEMABINDING
     AS
     BEGIN ATOMIC
         WITH (TRANSACTION ISOLATION LEVEL=SNAPSHOT,
               LANGUAGE=N'us_english')
     
       DECLARE @i INT = 1
     
       WHILE @i > 0
       BEGIN
         INSERT dbo.table1
         SELECT c2
         FROM @table1
         WHERE c1 = @i AND is_transient=0
     
         IF @@ROWCOUNT > 0
           SET @i += 1
         ELSE
         BEGIN
           INSERT dbo.temp_table1
           SELECT c2
           FROM @table1
           WHERE c1 = @i AND is_transient=1
     
           IF @@ROWCOUNT > 0
             SET @i += 1
           ELSE
             SET @i = 0
         END
       END
     
     END
     GO
     -- sample execution of the proc
     DECLARE @table1 dbo.tt_table1
     INSERT @table1 (c2, is_transient) VALUES (N'sample durable', 0)
     INSERT @table1 (c2, is_transient) VALUES (N'sample non-durable', 1)
     EXECUTE dbo.usp_ingest_table1 @table1=@table1
     SELECT c1, c2 from dbo.table1
     SELECT c1, c2 from dbo.temp_table1
     GO
   

## <a name="resources-to-learn-more"></a>Ressources supplémentaires :

- [Démarrage rapide 1 : technologies OLTP en mémoire pour accélérer les performances T-SQL](http://msdn.microsoft.com/library/mt694156.aspx)
- Vous trouverez la démonstration des performances avec l’OLTP en mémoire ici : [in-memory-oltp-perf-demo-v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)
- [Vidéo de 17 minutes expliquant l’OLTP en mémoire et présentant la démonstration](https://www.youtube.com/watch?v=l5l5eophmK4) (démonstration à 8:25)
- [Script pour activer l’OLTP en mémoire et définir les options recommandées](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)
- [Documentation principale sur l’OLTP en mémoire](https://msdn.microsoft.com/library/dn133186.aspx)
- [Improving temp table and table variable performance using memory optimization](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/) (Amélioration des performances des tables temporaires et des variables de table à l’aide de l’optimisation de la mémoire) 
[Optimize Performance using In-Memory Technologies in SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory) (Optimiser les performances à l’aide des technologies en mémoire dans SQL Database)
- [Tables temporelles à système par version avec tables optimisées en mémoire](https://msdn.microsoft.com/library/mt590207.aspx)
-  [In-Memory OLTP – Common Workload Patterns and Migration Considerations](http://msdn.microsoft.com/library/dn673538.aspx) (OLTP en mémoire – Modèles de charge de travail courants et considérations relatives à la migration). 