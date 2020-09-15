---
title: Configuration pour une utilisation avec R
description: Cet article fournit des conseils sur la configuration matérielle et réseau de l’ordinateur utilisé pour exécuter SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 03/29/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f9d4d3eab9f8f6d1d19b107eaf3825e9488df382
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180465"
---
# <a name="sql-server-configuration-for-use-with-r"></a>Configuration de SQL Server pour une utilisation avec R
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Cet article est le deuxième d’une série qui décrit l’optimisation des performances pour R Services sur la base de deux études de cas.  Cet article fournit des conseils sur la configuration matérielle et réseau de l’ordinateur utilisé pour exécuter SQL Server R Services. Il contient également des informations sur les méthodes de configuration de l’instance SQL Server, de la base de données ou des tables utilisées dans une solution. Étant donné que l’utilisation de NUMA dans SQL Server atténue la séparation entre les optimisations matérielles et celles de la base de données, une troisième section décrit en détail le processus pour configurer l’affinité et gouverner les ressources du processeur.

> [!TIP]
> Si vous débutez avec SQL Server, nous vous recommandons vivement de consulter aussi le guide d’optimisation des performances de SQL Server : [Surveiller et régler les performances](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance).

## <a name="hardware-optimization"></a>Optimisation matérielle

L’optimisation de l’ordinateur serveur est importante pour s’assurer que vous disposez des ressources nécessaires pour exécuter des scripts externes. Lorsque les ressources sont limitées, vous pouvez observer des symptômes tels que ceux-ci :

- L’exécution du travail est différée ou annulée pour traiter en priorité les autres opérations de base de données
- Une erreur « quota dépassé » provoque l’arrêt du script R sans que celui n’aille jusqu’au bout
- Les données chargées dans la mémoire R sont tronquées et les résultats sont incomplets

### <a name="memory"></a>Mémoire

La quantité de mémoire disponible sur l’ordinateur peut avoir un impact important sur les performances des algorithmes d’analyse avancés. Une quantité de mémoire insuffisante peut affecter le degré de parallélisme quand le contexte de calcul SQL est utilisé. Cela peut aussi affecter la taille de segment (lignes par opération de lecture) qui peut être traitée, ainsi que le nombre de sessions simultanées qui peuvent être prises en charge.

La quantité de mémoire minimale recommandée est de 32 Go. Si vous disposez de plus de 32 Go, vous pouvez configurer la source de données SQL de façon à augmenter le nombre de lignes utilisées dans chaque opération de lecture et donc à améliorer les performances.

Vous pouvez également gérer la mémoire utilisée par l’instance. Par défaut, SQL Server est prioritaire sur les processus de script externes lorsque la mémoire est allouée. Dans une installation par défaut de R Services, 20 % seulement de la mémoire disponible est allouée à R.

En règle générale, ce n’est pas suffisant pour les tâches de science des données, mais vous ne voulez pas non plus priver SQL Server de mémoire. Vous devez expérimenter et ajuster la répartition de la mémoire entre le moteur de base de données, les services associés et les scripts externes, en sachant que la configuration optimale varie en fonction des cas.

Pour le modèle reprise-correspondance, l’utilisation de script externe était lourde et aucun autre service de moteur de base de données n’était en cours d’exécution. Par conséquent, les ressources allouées aux scripts externes ont été augmentées à 70 %, ce qui était la meilleure configuration pour optimiser les performances des scripts.

### <a name="power-options"></a>Options d’alimentation

Sur le système d’exploitation Windows, il convient d’utiliser l’option d’alimentation **Performances élevées**. L’utilisation d’un autre paramètre d’alimentation occasionnerait une baisse ou une fluctuation des performances pendant l’utilisation de SQL Server.

### <a name="disk-io"></a>E/S disque

Les travaux d’apprentissage et de prédiction utilisant R Services sont par nature liés aux E/S et dépendent de la rapidité du ou des disques sur lesquels la base de données est stockée. L’utilisation de disques rapides, tels que les disques SSD, peut être utile.

Les E/S disque sont aussi affectées par les autres applications qui accèdent au disque. Tel est le cas, par exemple, des opérations de lecture dans une base de données qui sont le fait d’autres clients. Les performances d’E/S disque peuvent aussi être affectées par les paramètres du système de fichiers utilisé, notamment la taille de bloc utilisée par le système de fichiers.

Si plusieurs lecteurs sont disponibles, il est préférable de stocker les bases de données sur un lecteur différent de celui de SQL Server. De cette façon, les demandes visant le moteur de base de données n’accéderont pas au même disque que les demandes portant sur les données stockées dans la base de données.

Par ailleurs, les E/S disque peuvent avoir un impact important sur les performances quand les fonctions d’analyse RevoScaleR en cours d’exécution utilisent plusieurs itérations en phase d’apprentissage. Par exemple, les fonctions `rxLogit`, `rxDTree`, `rxDForest` et `rxBTrees` utilisent toutes plusieurs itérations. Quand SQL Server est la source de données, ces algorithmes utilisent des fichiers temporaires qui sont optimisés pour la capture de données. Ces fichiers sont automatiquement nettoyés en fin de session. En utilisant un disque hautes performances pour les opérations de lecture/écriture, il est possible d’améliorer de manière significative le temps écoulé global pour ces algorithmes.

> [!NOTE]
> Les versions antérieures de R Services ont nécessité la prise en charge des noms de fichiers 8.3 sur les systèmes d’exploitation Windows. Cette restriction a été levée après le Service Pack 1. Toutefois, vous pouvez utiliser fsutil.exe pour déterminer si un lecteur prend en charge les noms de fichiers au format 8.3 ou activer la prise en charge si ce n’est pas le cas.

### <a name="paging-file"></a>Fichier d’échange

Le système d’exploitation Windows utilise un fichier de pagination pour gérer les vidages sur incident et stocker les pages de mémoire virtuelle. Si vous constatez une pagination excessive, envisagez d’augmenter la capacité de la mémoire physique de l’ordinateur. Même si une capacité de mémoire physique supérieure n’est pas propre à éliminer la pagination, elle en réduit la nécessité.

La rapidité du disque sur lequel est stocké le fichier d’échange peut aussi affecter les performances. En stockant le fichier d’échange sur un disque SSD ou en utilisant plusieurs fichiers d’échange sur plusieurs disques SSD, il est possible d’améliorer les performances.

Pour plus d’informations sur le dimensionnement du fichier d’échange, consultez [Comment faire pour déterminer la taille de fichier d’échange appropriée pour les versions 64 bits de Windows](https://support.microsoft.com/kb/2860880).

## <a name="optimizations-at-instance-or-database-level"></a>Optimisations au niveau de l’instance ou de la base de données

L’optimisation de l’instance SQL Server est la clé d’une exécution efficace des scripts externes.

> [!NOTE]
> Les paramètres optimaux varient en fonction de la taille et du type de vos données, ainsi que du nombre de colonnes que vous utilisez pour le scoring ou l’apprentissage d’un modèle.
> 
> Vous pouvez passer en revue les résultats des optimisations spécifiques dans le dernier article : [Optimisation des performances pour R - Résultats de l’étude de cas](../../machine-learning/r/performance-case-study-r-services.md)
> 
> Pour obtenir des échantillons de scripts, consultez le [référentiel GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning) distinct.

### <a name="table-compression"></a>Compression de table

Les performances d’E/S peuvent souvent bénéficier de l’utilisation de la compression ou d’un magasin de données en colonnes. En général, les données sont souvent répétées dans plusieurs colonnes d’une même table. De ce fait, l’utilisation d’un columnstore profite de ces répétitions pendant la compression des données.

Un columnstore peut perdre de son efficacité si les insertions dans la table sont nombreuses, mais son utilisation reste un bon choix si les données sont statiques ou rarement modifiées. Si l’utilisation d’une banque de colonnes n’est pas appropriée, l’activation de la compression sur une table principale de lignes permet d’améliorer les E/S.

Pour plus d’informations, consultez les documents suivants :

+ [Compression des données](../../relational-databases/data-compression/data-compression.md)

+ [Activer la compression sur une table ou un index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Guide des index columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>Tables optimisées en mémoire

De nos jours, la mémoire n’est plus un problème pour les ordinateurs modernes. À mesure que les spécifications matérielles s’améliorent, il devient relativement facile d’acquérir de la mémoire vive à un prix correct. Toutefois, dans le même temps, les données sont produites plus rapidement que jamais, et elles doivent être traitées avec une faible latence.

Les tables à mémoire optimisée représentent une solution. En effet, elles tirent parti de la grande quantité de mémoire disponible sur les ordinateurs avancés pour résoudre le problème du Big Data. Les tables à mémoire optimisée résident principalement en mémoire, de sorte que les données sont lues à partir de la mémoire et écrites dans celle-ci. Pour des questions de durabilité, une deuxième copie de la table est conservée sur le disque et les données sont uniquement lues à partir du disque pendant la récupération de la base de données.

Si vous avez besoin de lire et d’écrire fréquemment dans vos tables, les tables à mémoire optimisée peuvent vous aider à atteindre une évolutivité élevée et une faible latence.  Dans le scénario reprise-correspondance, l’utilisation de tables à mémoire optimisée nous a permis de lire toutes les fonctionnalités de reprise à partir de la base de données et de les stocker dans la mémoire principale, pour les faire correspondre aux nouvelles ouvertures de tâches. Nous avons ainsi considérablement réduit les E/S disque.

Des gains de performances supplémentaires ont été réalisés en utilisant une table à mémoire optimisée dans le processus d’écriture de prédictions dans la base de données à partir de plusieurs lots simultanés. L’utilisation de tables à mémoire optimisée sur SQL Server a permis d’atteindre une faible latence sur les écritures et lectures dans les tables.

L’expérience était également fluide pendant le développement. Des tables à mémoire optimisée durables ont été créées en même temps que la base de données. Par conséquent, le développement a utilisé le même workflow indépendamment de l’emplacement de stockage des données.

### <a name="processor"></a>Processeur

SQL Server peut effectuer des tâches en parallèle en exploitant les cœurs disponibles sur l’ordinateur ; les performances sont proportionnelles au nombre de cœurs disponibles. Bien que l’augmentation du nombre de cœurs ne soit pas nécessairement déterminante pour les opérations liées aux E/S, les algorithmes utilisant le processeur de manière intensive tirent avantage des processeurs rapides dotés de nombreux cœurs.

Le serveur étant normalement utilisé par plusieurs utilisateurs simultanés, l’administrateur de base de données doit déterminer le nombre idéal de cœurs nécessaires à la prise en charge des calculs en période de charge de travail maximale.

### <a name="resource-governance"></a>Gouvernance des ressources

Dans les éditions qui prennent en charge Resource Governor, vous pouvez utiliser des pools de ressources pour spécifier que certaines charges de travail reçoivent un certain nombre de processeurs. Vous pouvez également gérer la quantité de mémoire allouée à des charges de travail spécifiques.

La gouvernance des ressources dans SQL Server vous permet de centraliser la surveillance et le contrôle des diverses ressources utilisées par SQL Server et R. Par exemple, vous pouvez allouer la moitié de la mémoire disponible au moteur de base de données, afin de garantir que les services principaux peuvent toujours s’exécuter en dépit de charges de travail transitoires plus lourdes.

La valeur de consommation de mémoire par défaut des scripts externes est limitée à 20 % de la mémoire totale disponible pour SQL Server. Cette limite est appliquée par défaut pour garantir que toutes les tâches qui reposent sur le serveur de base de données ne soient pas gravement affectées par les travaux R durables. Cependant, l’administrateur de base de données peut modifier ces limites. Dans de nombreux cas, la limite de 20 % n’est pas adaptée à la prise en charge des charges de travail de Machine Learning intensives.

Les options de configuration prises en charge sont **MAX_CPU_PERCENT**, **MAX_MEMORY_PERCENT** et **MAX_PROCESSES**. Pour afficher les paramètres actuels, utilisez cette instruction : `SELECT * FROM sys.resource_governor_external_resource_pools`

-  Si le serveur est surtout utilisé pour R Services, il peut être utile d’augmenter la valeur de MAX_CPU_PERCENT à 40 % ou 60 %.

-  Si de nombreuses sessions R doivent utiliser le même serveur en même temps, vous devez augmenter les trois paramètres.

Pour modifier les valeurs des ressources allouées, utilisez des instructions T-SQL.

+ Cet exemple fixe l’utilisation de la mémoire à 40 % : `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ L’instruction suivante définit les trois valeurs configurables : `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ Si vous modifiez un paramètre de mémoire, du processeur ou de processus maximal et que vous souhaitez appliquer les paramètres immédiatement, exécutez l’instruction suivante : `ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>NUMA logiciel, NUMA matériel et affinité du processeur

Lorsque vous utilisez SQL Server comme contexte de calcul, vous pouvez parfois obtenir de meilleures performances en réglant les paramètres relatifs à NUMA et à l’affinité du processeur. 

Les systèmes équipés de _matériels NUMA_ possèdent plusieurs bus système, chacun au service d’un petit ensemble de processeurs. Chaque processeur peut accéder à la mémoire associée à d’autres groupes, et ce, de façon cohérente. Chaque groupe est appelé nœud NUMA. Si vous possédez un matériel NUMA, il peut être configuré de façon à utiliser la mémoire entrelacée au lieu de l'accès NUMA. Dans ce cas, Windows et, de ce fait, SQL Server ne le reconnaissent pas comme NUMA. 

Vous pouvez exécuter la requête suivante pour trouver le nombre de nœuds mémoire disponibles pour SQL Server :

```sql
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

Si la requête retourne un seul nœud mémoire (nœud 0), soit vous ne possédez pas de matériel NUMA, soit le matériel est configuré comme entrelacé (non-NUMA). SQL Server ignore également le NUMA matériel lorsqu’il y a quatre processeurs ou moins, ou si au moins un nœud n’a qu’un seul processeur.

Si votre ordinateur possède plusieurs processeurs, mais pas de NUMA matériel, vous pouvez également utiliser le [NUMA logiciel](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) pour subdiviser les processeurs en groupes plus petits.  Dans SQL Server 2016 et SQL Server 2017, la fonctionnalité NUMA logiciel est automatiquement activée au démarrage du service SQL Server.

Lorsque le NUMA logiciel est activé, SQL Server gère automatiquement les nœuds pour vous. Toutefois, pour optimiser en fonction de charges de travail spécifiques, vous pouvez désactiver _affinité logicielle_ et configurer manuellement l’affinité du processeur pour les nœuds NUMA logiciels. Cela peut vous permettre de mieux décider quelles charges de travail sont attribuées à quels nœuds, en particulier si vous utilisez une édition de SQL Server qui prend en charge la gouvernance des ressources. En spécifiant l’affinité du processeur et en alignant les pools de ressources avec des groupes de processeurs, vous pouvez réduire la latence et vous assurer que les processus associés sont exécutés dans le même nœud NUMA.

Le processus global de configuration du NUMA logiciel et de l’affinité du processeur pour la prise en charge des charges de travail R est le suivant :

1. Activer le NUMA logiciel, si disponible
2. Définir l’affinité du processeur
3. Créer des pools de ressources pour les processus externes, à l’aide de [Resource Governor](../administration/resource-governor.md)
4. Attribuer les [groupes de charges de travail ](../../relational-databases/resource-governor/resource-governor-workload-group.md) à des groupes d’affinités spécifiques

Pour plus d’informations, y compris des échantillons de code, consultez ce didacticiel : [SQL Optimization Tips and Tricks (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services) (Trucs et astuces pour l’optimisation SQL (Ke Huang))

**Autres ressources :**

+ [NUMA logiciel dans SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Comment mapper les nœuds NUMA logiciel aux processeurs

## <a name="task-specific-optimizations"></a>Optimisations spécifiques aux tâches

Cette section résume les méthodes adoptées dans ces études de cas et dans d’autres tests pour optimiser des charges de travail de Machine Learning spécifiques. Les charges de travail courantes incluent l’apprentissage du modèle, l’extraction et l’ingénierie des caractéristiques, ainsi que divers scénarios de scoring : une seule ligne, un petit lot et un gros lot.

### <a name="feature-engineering"></a>Ingénierie des caractéristiques

L’un des points faibles de R est qu’il est généralement traité sur un processeur unique. Il s’agit d’un goulot d’étranglement majeur au niveau des performances pour de nombreuses tâches, en particulier pour l’ingénierie des caractéristiques. Dans la solution reprise-correspondance, la tâche d’ingénierie des caractéristiques a créé à elle seule 2 500 caractéristiques inter-produits qui ont dû être combinées avec les 100 caractéristiques d’origine. Cette tâche prendrait beaucoup de temps si tout devait être effectué sur un seul processeur.

Il existe plusieurs façons d’améliorer les performances de l’ingénierie des caractéristiques. Vous pouvez soit optimiser votre code R et conserver l’extraction des caractéristiques au sein du processus de modélisation, soit déplacer le processus d’ingénierie des caractéristiques dans SQL.

- Utilisation de R : vous définissez une fonction et la transmettez comme argument à [rxTransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform) pendant l’apprentissage. Si le modèle prend en charge le traitement parallèle, la tâche d’ingénierie des caractéristiques peut être traitée à l’aide de plusieurs processeurs. À l’aide de cette approche, l’équipe de science des données a constaté une amélioration des performances de 16 % au niveau de la durée de scoring. Toutefois, cette approche nécessite un modèle qui prend en charge la mise en parallèle et une requête qui peut être exécutée à l’aide d’un plan parallèle.

- Utilisation de R avec un contexte de calcul SQL : dans un environnement multiprocesseur avec des ressources isolées disponibles pour l’exécution de lots distincts, vous pouvez obtenir une plus grande efficacité en isolant les requêtes SQL utilisées pour chaque lot, pour extraire les données des tables et contraindre les données du même groupe de charge de travail. Les méthodes utilisées pour isoler les lots incluent le partitionnement et l’utilisation de PowerShell pour exécuter des requêtes distinctes en parallèle.

- Utilisation de l’exécution parallèle ad hoc : dans un contexte de calcul SQL Server, vous pouvez vous appuyer sur le moteur de base de données SQL pour appliquer une exécution parallèle, si possible, et si cette option est jugée plus efficace.

- Utilisation de T-SQL dans un processus de caractérisation distinct : le précalcul des données de caractéristique à l’aide de SQL est généralement plus rapide.

### <a name="prediction-scoring-in-parallel"></a>Prédiction (scoring) en parallèle

L’un des avantages de SQL Server est sa capacité à gérer un volume important de lignes en parallèle, ce qui est tout particulièrement utile pour le scoring. En général, le modèle n’a pas besoin d’accéder à toutes les données pour le scoring. Vous pouvez donc partitionner les données d’entrée pour que chaque groupe de charge de travail traite une tâche.

Vous pouvez également envoyer les données d’entrée sous la forme d’une requête unique, puis SQL Server analyse la requête. Si vous pouvez créer un plan de requête en parallèle pour les données d’entrée, il partitionne automatiquement les données attribuées aux nœuds et effectue également des jointures et des agrégations nécessaires en parallèle.

Si vous êtes intéressé par la manière de définir une procédure stockée pour le scoring, consultez l’exemple de projet sur [GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips-Resume-Matching/SQLR), en particulier le fichier « step5_score_for_matching.sql ». L’échantillon de script suit également les heures de début et de fin des requêtes et écrit l’heure dans la console SQL pour vous permettre d’évaluer les performances.

### <a name="concurrent-scoring-using-resource-groups"></a>Scoring simultané à l’aide de groupes de ressources

Pour faire monter en puissance le problème de scoring, il est recommandé d’adopter l’approche «MapReduce » dans laquelle des millions d’éléments sont divisés en plusieurs lots. Ensuite, plusieurs travaux de scoring sont exécutés simultanément. Dans cette infrastructure, les lots sont traités sur différents ensembles de processeurs et les résultats sont collectés et réécrits dans la base de données.

Il s’agit de l’approche utilisée dans le scénario reprise-correspondance. Toutefois, la gouvernance des ressources dans SQL Server est essentielle pour la mise en œuvre de cette approche. En configurant des groupes de charges de travail pour les travaux de script externes, vous pouvez acheminer des travaux de scoring R vers différents groupes de processeurs et obtenir un débit plus rapide.

La gouvernance des ressources permet également de répartir les ressources disponibles sur le serveur (processeur et mémoire) pour réduire la concurrence entre les charges de travail. Vous pouvez configurer des fonctions de classifieur pour distinguer les différents types de travaux R : par exemple, vous pouvez décider que le scoring appelé à partir d’une application a toujours la priorité, alors que les travaux de réapprentissage ont une priorité basse. Cette isolation des ressources peut potentiellement améliorer la durée d’exécution et fournir des performances plus prévisibles.

### <a name="concurrent-scoring-using-powershell"></a>Scoring simultané à l’aide de PowerShell

Si vous décidez de partitionner les données vous-même, vous pouvez utiliser des scripts PowerShell pour exécuter plusieurs tâches de scoring simultanées. Pour ce faire, utilisez la cmdlet Invoke-SqlCmd et lancez les tâches de scoring en parallèle.

Dans le scénario reprise-correspondance, la concurrence a été conçue comme suit :

- 20 processeurs répartis en quatre groupes de cinq processeurs chacun. Chaque groupe de processeurs se trouve sur le même nœud NUMA.

- Le nombre maximal de lots simultanés a été défini sur huit.

- Chaque groupe de charges de travail doit gérer deux tâches de scoring. Dès qu’une tâche a terminé la lecture des données et commence le scoring, l’autre tâche peut commencer à lire les données de la base de données.

Pour afficher les scripts PowerShell pour ce scénario, ouvrez le fichier experiment.ps1 dans le [projet Github](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips-Resume-Matching).

### <a name="storing-models-for-prediction"></a>Stockage des modèles pour la prédiction

Une fois l’apprentissage et l’évaluation terminés et quand vous avez sélectionné le meilleur modèle, nous vous recommandons de le stocker dans la base de données pour pouvoir l’utiliser dans les prédictions. Le chargement du modèle précalculé à partir de la base de données pour la prédiction est efficace, car le Machine Learning SQL Server utilise des algorithmes de sérialisation spéciaux pour stocker et charger des modèles lors des déplacements entre R et la base de données.

> [!TIP]
> Dans SQL Server 2017, vous pouvez utiliser la fonction PREDICT pour effectuer le scoring même si R n’est pas installé sur le serveur. Un nombre limité de types de modèles est pris en charge, à partir du package RevoScaleR.

Toutefois, selon l’algorithme que vous utilisez, certains modèles peuvent être assez volumineux, en particulier si vous les formez sur un jeu de données volumineux. Par exemple, les algorithmes tels que **lm** ou **glm** génèrent un grand nombre de données de synthèse avec des règles. Étant donné qu’il y a des limites sur la taille d’un modèle qui peut être stocké dans une colonne varbinary, nous vous recommandons d’éliminer les artefacts inutiles du modèle avant de le stocker dans la base de données pour la production.

## <a name="articles-in-this-series"></a>Articles de cette série

[Optimisation des performances pour R - Introduction](../r/sql-server-r-services-performance-tuning.md)

[Optimisation des performances pour R - Configuration de SQL Server](../r/sql-server-configuration-r-services.md)

[Optimisation des performances pour R - Code R et optimisation des données](../r/r-and-data-optimization-r-services.md)

[Optimisation des performances pour R - Résultats de l’étude de cas](../r/performance-case-study-r-services.md)
