---
title: Configuration de SQL Server (R Services) - SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 9ad4d1a23a05db35e0c4b55473903dbf7e4265da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641948"
---
# <a name="sql-server-configuration-for-use-with-r"></a>Configuration de SQL Server pour une utilisation avec R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article est le deuxième d’une série qui décrit l’optimisation des performances pour R Services selon deux études de cas.  Cet article fournit des conseils sur la configuration matérielle et réseau de l’ordinateur qui est utilisé pour exécuter SQL Server R Services. Il contient également des informations sur les façons de configurer l’instance SQL Server, base de données ou tables utilisées dans une solution. Étant donné que l’utilisation de NUMA dans SQL Server estompe les frontières entre les optimisations de matériel et de la base de données, une troisième section traite des UC affinage et gouvernance des ressources en détail.

> [!TIP]
> Si vous ne connaissez pas SQL Server, nous vous recommandons fortement de consulter également le guide de réglage de performances de SQL Server : [Surveiller et régler les performances](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance).

## <a name="hardware-optimization"></a>Optimisation du matériel

Optimisation de l’ordinateur du serveur est importante pour s’assurer que vous disposez des ressources pour exécuter des scripts externes. Lorsque les ressources sont limitées, vous pouvez voir les symptômes suivants :

- L’exécution du travail est différée ou annulée pour hiérarchiser les autres opérations de base de données
- Erreur « quota dépassé » entraînant un script R pour terminer sans saisie semi-automatique
- Données chargées en mémoire de R tronqué, des résultats incomplets

### <a name="memory"></a>Mémoire

La quantité de mémoire disponible sur l’ordinateur peut avoir un impact important sur les performances des algorithmes d’analyse avancés. Mémoire insuffisante peut affecter le degré de parallélisme lors de l’utilisation du contexte de calcul SQL. Cela peut aussi affecter la taille de segment (lignes par opération de lecture) qui peut être traitée, ainsi que le nombre de sessions simultanées qui peuvent être prises en charge.

Un minimum de 32 Go est hautement recommandé. Si vous avez plus de 32 Go de disponible, vous pouvez configurer la source de données SQL pour utiliser plus de lignes dans chaque opération de lecture pour améliorer les performances.

Vous pouvez également gérer la mémoire utilisée par l’instance. Par défaut, SQL Server est prioritaire par rapport à des processus de script externe lors de la mémoire est allouée. Dans une installation par défaut de R Services, seulement 20 % de mémoire disponible est allouée à R.

En général, cela n’est pas suffisant pour les tâches de science des données, mais ni voulez-vous vous priver de SQL server de la mémoire. Vous devez tester et ajuster l’allocation de mémoire entre le moteur de base de données, les services associés et des scripts externes, étant entendu que la configuration optimale varie selon le cas par cas.

Pour le modèle de mise en correspondance de reprise, script externe a été importante, et il n’y avait aucune autre base de données des services de moteur en cours d’exécution ; Par conséquent, les ressources allouées à des scripts externes ont été augmentées à 70 %, qui était la meilleure configuration pour les performances de script.

### <a name="power-options"></a>Options d’alimentation

Sur le système d’exploitation Windows, le **hautes performances** option d’alimentation doit être utilisée. À l’aide d’un autre paramètre d’alimentation des résultats incohérents ou une diminution des performances lors de l’utilisation de SQL Server.

### <a name="disk-io"></a>E/S disque

Apprentissage et prédiction de travaux à l’aide de R Services sont, par nature, e/s liée et dépendent de la vitesse des disques sur lesquels la base de données est stocké sur. Utilisation de disques rapides, comme les disques SSD (SSD) peut vous aider.

Les E/S disque sont aussi affectées par les autres applications qui accèdent au disque. Tel est le cas, par exemple, des opérations de lecture dans une base de données qui sont le fait d’autres clients. Les performances d’E/S disque peuvent aussi être affectées par les paramètres du système de fichiers utilisé, notamment la taille de bloc utilisée par le système de fichiers.

Si plusieurs lecteurs sont disponibles, magasin de bases de données sur un lecteur autre que SQL Server afin que les demandes pour le moteur de base de données n’atteignent pas le même disque que demande des données stockées dans la base de données.

Par ailleurs, les E/S disque peuvent avoir un impact important sur les performances quand les fonctions d’analyse RevoScaleR en cours d’exécution utilisent plusieurs itérations en phase d’apprentissage. Par exemple, `rxLogit`, `rxDTree`, `rxDForest`, et `rxBTrees` utilisent toutes plusieurs itérations. Lorsque la source de données est SQL Server, ces algorithmes utilisent des fichiers temporaires qui sont optimisés pour capturer les données. Ces fichiers sont automatiquement nettoyés en fin de session. N’utilisant qu’un disque hautes performances pour les opérations de lecture/écriture peut améliorer considérablement le temps écoulé global pour ces algorithmes.

> [!NOTE]
> Premières versions de R Services nécessitaient à la prise en charge de nom de fichier au format 8.3 sur les systèmes d’exploitation Windows. Cette restriction a été levée après le Service Pack 1. Toutefois, vous pouvez utiliser fsutil.exe pour déterminer si un lecteur prend en charge les noms de 8.3 fichiers ou activer la prise en charge si elle n’est pas le cas.

### <a name="paging-file"></a>Fichier d’échange

Le système d’exploitation Windows utilise un fichier de pagination pour gérer les vidages sur incident et stocker les pages de mémoire virtuelle. Si vous constatez une pagination excessive, envisagez d’augmenter la capacité de la mémoire physique de l’ordinateur. Même si une capacité de mémoire physique supérieure n’est pas propre à éliminer la pagination, elle en réduit la nécessité.

La rapidité du disque sur lequel est stocké le fichier d’échange peut aussi affecter les performances. En stockant le fichier d’échange sur un disque SSD ou en utilisant plusieurs fichiers d’échange sur plusieurs disques SSD, il est possible d’améliorer les performances.

Pour plus d’informations sur le fichier d’échange de dimensionnement, consultez [comment déterminer la taille de fichier d’échange appropriée pour les versions 64 bits de Windows](https://support.microsoft.com/kb/2860880).

## <a name="optimizations-at-instance-or-database-level"></a>Optimisations au niveau instance ou de la base de données

Optimisation de l’instance de SQL Server est la clé pour une exécution efficace des scripts externes.

> [!NOTE]
> Les paramètres optimaux diffèrent selon la taille et le type de données, le nombre de colonnes que vous utilisez pour calculer les scores ou d’apprentissage d’un modèle.
> 
> Vous pouvez examiner les résultats des optimisations spécifiques dans l’article final : [Paramétrage des performances - résultats de l’étude de cas](../../advanced-analytics/r/performance-case-study-r-services.md)
> 
> Pour les exemples de scripts, consultez le distinct [référentiel GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning).

### <a name="table-compression"></a>Compression de table

Les performances d’e/s peuvent souvent être améliorées en utilisant la compression ou un magasin de données en colonnes. En règle générale, les données sont souvent répétées dans plusieurs colonnes d’une table, donc à l’aide d’un index columnstore profite de ces répétitions lors de la compression des données.

Un index columnstore ne peut pas être aussi efficace s’il existe de nombreuses insertions dans la table, mais constitue un bon choix si les données sont statiques ou rarement modifiées. Si l’utilisation d’une banque de colonnes n’est pas appropriée, l’activation de la compression sur une table principale de lignes permet d’améliorer les E/S.

Pour plus d’informations, consultez les documents suivants :

+ [Compression de données](../../relational-databases/data-compression/data-compression.md)

+ [Activer la compression sur une table ou un index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Guide des index columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>Tables optimisées en mémoire

Aujourd'hui, mémoire n’est plus un problème pour les ordinateurs modernes. Comme les spécifications matérielles continuent à améliorer, il est très facile d’ajouter de RAM sur les bonnes valeurs. Toutefois, en même temps, données en cours de production plus rapidement qu’auparavant, et les données doivent être traitées avec une faible latence.

Tables mémoire optimisées représentent une solution, dans la mesure elles tirent parti de la grande mémoire disponible dans ordinateurs avancées de résoudre le problème des données volumineuses. Tables mémoire optimisées résident principalement dans la mémoire, afin que les données sont lues et écrites dans la mémoire. Pour une durabilité, une deuxième copie de la table est conservée sur le disque et les données sont uniquement lues à partir du disque lors de la récupération de base de données.

Si vous avez besoin lire et écrire dans des tables fréquemment, les tables mémoire optimisées peuvent aider à évolutivité élevée et une faible latence.  Dans le scénario de mise en correspondance de reprise, l’utilisation de tables optimisées en mémoire a permis à lire toutes les fonctionnalités de reprise à partir de la base de données et les stocker dans la mémoire principale, à faire correspondre avec les nouvelles ouvertures de travail. Cela réduit considérablement les e/s disque.

Gains de performances supplémentaires ont été obtenus à l’aide de la table optimisée en mémoire en cours de la réécriture des prédictions sur la base de données à partir de plusieurs lots simultanés. L’utilisation de tables mémoire optimisées sur SQL Server activée à faible latence sur table lectures et écritures.

L’expérience a été également transparente au cours du développement. Les tables durables optimisées en mémoire ont été créés en même temps que la base de données a été créé. Par conséquent, le développement utilisé le même flux de travail, quel que soit le stockage de données.

### <a name="processor"></a>Processeur

SQL Server peut exécuter des tâches en parallèle en utilisant les cœurs disponibles sur l’ordinateur ; davantage de cœurs est disponibles, meilleures sont les performances. Alors que l’augmentation du nombre de cœurs peut aider à pas pour les opérations d’e/s liée, processeur algorithmes avantage des processeurs rapides dotés de nombreux cœurs.

Étant donné que le serveur est normalement utilisé par plusieurs utilisateurs simultanément, l’administrateur de base de données doit déterminer le nombre idéal de cœurs qui sont nécessaires pour prendre en charge des calculs de charge de travail de pointe.

### <a name="resource-governance"></a>Gouvernance des ressources

Dans les éditions qui prennent en charge le gouverneur de ressources, vous pouvez utiliser des pools de ressources pour spécifier que certaines charges de travail sont allouées à un nombre d’unités centrales. Vous pouvez également gérer la quantité de mémoire allouée aux charges de travail spécifiques.

Gouvernance des ressources dans SQL Server vous permet de centraliser la surveillance et le contrôle des diverses ressources utilisés par SQL Server et R. Par exemple, vous pourrez allouer de la moitié de la mémoire disponible pour le moteur de base de données, pour vous assurer qu’un cœur services peuvent toujours s’exécuter en dépit des charges de travail plus lourdes temporaires.

La valeur par défaut pour la consommation de mémoire par les scripts externes est limitée à 20 % de la mémoire totale disponible pour SQL Server lui-même. Cette limite est appliquée par défaut pour vous assurer que toutes les tâches qui s’appuient sur le serveur de base de données ne sont pas gravement affectés par les travaux R à long terme. Cependant, l’administrateur de base de données peut modifier ces limites. Dans de nombreux cas, la limite de 20 % n’est pas suffisante pour supporter des charges de travail d’apprentissage sérieux.

Les options de configuration pris en charge sont **MAX_CPU_PERCENT**, **MAX_MEMORY_PERCENT**, et **MAX_PROCESSES**. Pour afficher les paramètres actuels, utilisez cette instruction : `SELECT * FROM sys.resource_governor_external_resource_pools`

-  Si le serveur est principalement utilisé pour R Services, il serait utile d’augmenter de MAX_CPU_PERCENT à 40 % ou 60 %.

-  Si le nombre de sessions R doit utiliser le même serveur en même temps, tous les trois paramètres doivent être augmentés.

Pour modifier les valeurs des ressources allouées, utilisez les instructions T-SQL.

+ Cette instruction définit l’utilisation de la mémoire à 40 % : `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ Cette instruction définit les trois valeurs configurables : `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ Si vous modifiez une mémoire, UC ou paramètre de nombre maximum de processus et que vous souhaitez appliquer les paramètres immédiatement, exécutez cette instruction : `ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>Affinité Soft-NUMA, le matériel NUMA et du processeur

Lorsque vous utilisez SQL Server comme contexte de calcul, vous pouvez parfois obtenir de meilleures performances en ajustant les paramètres liés à l’affinité du processeur et de NUMA. 

Systèmes avec _matériel NUMA_ ont plusieurs bus système, chacun au service d’un petit ensemble de processeurs. Chaque UC peut accéder à la mémoire associée aux autres groupes de manière cohérente. Chaque groupe est appelé nœud NUMA. Si vous possédez un matériel NUMA, il peut être configuré de façon à utiliser la mémoire entrelacée au lieu de l'accès NUMA. Dans ce cas, Windows et, par conséquent, SQL Server ne reconnaîtront pas cela comme NUMA. 

Vous pouvez exécuter la requête suivante pour rechercher le nombre de nœuds de mémoire disponibles pour SQL Server :

```sql
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

Si la requête retourne un seul nœud mémoire (nœud 0), vous ne disposez pas de matériel NUMA, soit le matériel est configuré comme entrelacé (non-NUMA). SQL Server ignore également le matériel NUMA lorsque les processeurs quatre ou moins il y a, ou si au moins un nœud n’a qu’un seul processeur.

Si votre ordinateur dispose de plusieurs processeurs, mais n’a pas de matériel NUMA, vous pouvez également utiliser [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) à subdiviser les processeurs en groupes plus petits.  Dans SQL Server 2016 et SQL Server 2017, la fonctionnalité Soft-NUMA est automatiquement activée au démarrage du service SQL Server.

Lorsque Soft-NUMA est activée, SQL Server gère automatiquement les nœuds ; Toutefois, pour optimiser les charges de travail spécifiques, vous pouvez désactiver _affinité logicielle_ et configurer manuellement l’affinité du processeur pour les nœuds NUMA logicielles. Cela peut vous donner plus de contrôle sur lequel les charges de travail sont assignées à quels nœuds, en particulier si vous utilisez une édition de SQL Server qui prend en charge la gouvernance des ressources. En spécifiant l’affinité du processeur et en alignant les pools de ressources avec des groupes de processeurs, vous pouvez réduire la latence et assurez-vous que les processus connexes sont exécutées dans le même nœud NUMA.

Le processus global pour la configuration soft-NUMA et l’affinité du processeur pour prendre en charge les charges de travail R est comme suit :

1. Activer le soft-NUMA, s’il est disponible
2. Définir l’affinité du processeur
3. Créer des pools de ressources pour les processus externes, à l’aide de [du gouverneur de ressources](../r/resource-governance-for-r-services.md)
4. Affecter le [groupes de charges de travail](../../relational-databases/resource-governor/resource-governor-workload-group.md) à des groupes d’affinités spécifiques

Pour plus d’informations, y compris des exemples de code, consultez ce didacticiel : [Optimisation des conseils et astuces SQL (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Autres ressources :**

+ [Soft-NUMA dans SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Comment mapper des nœuds soft-NUMA aux UC

## <a name="task-specific-optimizations"></a>Optimisations spécifiques aux tâches

Cette section résume les méthodes adoptés dans ces études de cas et dans d’autres tests, pour optimiser les charges de travail d’apprentissage spécifique. Charges de travail courantes incluent l’apprentissage du modèle, l’extraction de la fonctionnalité et l’ingénierie et divers scénarios pour calculer les scores : seule ligne, les lots de petite et lot volumineux.

### <a name="feature-engineering"></a>Ingénierie des caractéristiques

Un problème de R est qu’il est généralement traité sur un processeur unique. Il s’agit d’un goulot d’étranglement de performances pour de nombreuses tâches, en particulier de conception de fonctionnalités. Dans la solution correspondant à la reprise, la fonctionnalité engineering task force autonome créé des fonctionnalités de produit croisé 2 500 qui ont dû être combinés avec les fonctionnalités de 100 d’origine. Cette tâche prendrait beaucoup de temps si toutes les opérations effectuées sur une seule UC.

Il existe plusieurs moyens d’améliorer les performances de l’ingénierie. Vous pouvez optimiser votre code R et conserver l’extraction des caractéristiques à l’intérieur du processus de modélisation ou déplacer le processus d’ingénierie de fonctionnalité dans SQL.

- À l’aide de R. Vous définissez une fonction et puis passez-le comme argument de [rxTransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform) pendant la formation. Si le modèle prend en charge le traitement parallèle, la tâche d’ingénierie de fonctionnalité peut être traitée à l’aide de plusieurs processeurs. À l’aide de cette approche, l’équipe de science des données observé une amélioration des performances de 16 % en termes de temps de calcul de score. Toutefois, cette approche nécessite un modèle qui prend en charge de la parallélisation et une requête qui peut être exécutée à l’aide d’un plan parallèle.

- Contexte de calcul utilisent R avec SQL. Dans un environnement multiprocesseur avec les ressources isolés disponibles pour l’exécution de lots distincts, vous pouvez obtenir une plus grande efficacité en isolant les requêtes SQL utilisées pour chaque lot, pour extraire des données de tables et de limiter les données sur le même groupe de charge de travail. Méthodes utilisées pour isoler les lots incluent le partitionnement et sert de PowerShell pour exécuter des requêtes distinctes en parallèle.

- Exécution en parallèle ad hoc : Dans un contexte de calcul SQL Server, vous pouvez compter sur le moteur de base de données SQL pour appliquer l’exécution en parallèle si possible et si cette option s’avère plus efficace.

- Utiliser T-SQL dans un processus distinct de caractérisation. Precomputing les données de fonctionnalité à l’aide de SQL est généralement plus rapide.

### <a name="prediction-scoring-in-parallel"></a>Prédiction (score) en parallèle

Un des avantages de SQL Server est sa capacité à gérer un grand nombre de lignes en parallèle. Nulle part est cet avantage marqué comme dans le calcul de score. En règle générale le modèle n’a pas besoin accès à toutes les données pour calculer les scores, vous pouvez partitionner les données d’entrée, avec chaque groupe de charge de travail une tâche de traitement.

Vous pouvez également envoyer les données d’entrée comme une seule requête, et SQL Server analyse ensuite la requête. Si un plan de requête parallèle peut être créé pour les données d’entrée, il automatiquement partitionne les données affectées aux nœuds et réalise des jointures nécessaires et les agrégations en parallèle ainsi.

Si vous êtes intéressé par les détails de la définition d’une procédure stockée pour une utilisation dans le calcul de score, consultez l’exemple de projet sur [GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips/SQLR) et recherchez le fichier « step5_score_for_matching.sql ». L’exemple de script également début de requête effectue le suivi et les heures de fin et les écritures le temps de la console SQL afin que vous puissiez évaluer les performances.

### <a name="concurrent-scoring-using-resource-groups"></a>Calcul de score simultanées à l’aide de groupes de ressources

Pour faire évoluer le problème de calcul de score, une bonne pratique est d’adopter l’approche Map/reduce dans lequel des millions d’éléments sont divisées en plusieurs lots. Ensuite, plusieurs travaux de calcul de score sont exécutées simultanément. Dans ce cadre, les lots sont traitées sur différents ensembles de processeur, ainsi que les résultats sont collectés et mis à jour dans la base de données.

C’est l’approche utilisée dans le scénario de mise en correspondance de reprendre ; Toutefois, la gouvernance des ressources dans SQL Server sont essentielle pour implémenter cette approche. En définissant des groupes de charges de travail pour les tâches de script externe, vous pouvez acheminer R évaluation des travaux à différents groupes de processeurs et obtenir un débit plus rapide.

Gouvernance des ressources peuvent également aider à allouer de répartir les ressources disponibles sur le serveur (processeur et mémoire) pour réduire la concurrence de la charge de travail. Vous pouvez configurer des fonctions classifieur pour faire la distinction entre les différents types de travaux R : par exemple, vous pouvez décider que notation appelée à partir d’une application est toujours prioritaire, tandis que les travaux de REFORMATION ont une priorité basse. Cette isolation des ressources peut potentiellement améliorer les temps d’exécution et fournir des performances plus prévisibles.

### <a name="concurrent-scoring-using-powershell"></a>Calcul de score simultanées à l’aide de PowerShell

Si vous décidez de partitionner les données vous-même, vous pouvez utiliser des scripts PowerShell pour exécuter plusieurs tâches de calcul de score simultanées. Pour ce faire, utilisez l’applet de commande Invoke-SqlCmd et lancer les tâches de calcul de score en parallèle.

Dans le scénario de mise en correspondance de reprise, l’accès concurrentiel a été conçu comme suit :

- 20 processeurs divisé en quatre groupes de cinq processeurs. Chaque groupe d’unités centrales se trouve sur le même nœud NUMA.

- Nombre maximal de lots simultanés a été définie sur huit.

- Chaque groupe de charge de travail doit gérer deux tâches de calcul de score. Dès qu’une tâche a fini de lire les données et démarre de score, l’autre tâche peut commencer à lecture des données à partir de la base de données.

Pour afficher les scripts PowerShell pour ce scénario, ouvrez le fichier experiment.ps1 dans le [projet Github](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips).

### <a name="storing-models-for-prediction"></a>Stockage des modèles pour la prédiction

Lors de la formation et d’évaluation terminée et que vous avez sélectionné un meilleur modèle, nous vous recommandons de stocker le modèle dans la base de données afin qu’il soit disponible pour les prédictions. Le chargement du modèle précalculé à partir de la base de données pour la prédiction est efficace, car SQL Server machine learning utilise des algorithmes de sérialisation spéciale pour stocker et charger des modèles lors du déplacement entre R et la base de données.

> [!TIP]
> Dans SQL Server 2017, vous pouvez utiliser la fonction PREDICT pour effectuer l’évaluation même si R n’est pas installé sur le serveur. Types de modèles limitée sont pris en charge, à partir du package RevoScaleR.

Toutefois, selon l’algorithme que vous utilisez, certains modèles peuvent être très volumineux, en particulier lorsque formé sur un jeu de données volumineux. Par exemple, les algorithmes tels que **lm** ou **glm** générer un grand nombre de données de synthèse et des règles. Car il existe des limites sur la taille d’un modèle qui peut être stockée dans une colonne varbinary, nous vous recommandons d’éliminer les artefacts inutiles à partir du modèle avant de stocker le modèle dans la base de données pour la production.

## <a name="articles-in-this-series"></a>Articles de cette série

[Performances optimisation pour R - introduction](../r/sql-server-r-services-performance-tuning.md)

[Optimisation des performances pour R - configuration de SQL Server](../r/sql-server-configuration-r-services.md)

[Optimisation des performances pour R - R l’optimisation de code et des données](../r/r-and-data-optimization-r-services.md)

[Paramétrage des performances - résultats de l’étude de cas](../r/performance-case-study-r-services.md)
