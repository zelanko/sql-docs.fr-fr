---
title: Configuration de SQL Server (Services R)
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/29/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: dda5d84aca714530bbc2bef79344db889e113d4f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714991"
---
# <a name="sql-server-configuration-for-use-with-r"></a>Configuration SQL Server pour une utilisation avec R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article est le deuxième d’une série qui décrit l’optimisation des performances pour R services sur la base de deux études de cas.  Cet article fournit des conseils sur la configuration matérielle et réseau de l’ordinateur utilisé pour exécuter SQL Server R Services. Elle contient également des informations sur les méthodes de configuration de l’instance SQL Server, de la base de données ou des tables utilisées dans une solution. Étant donné que l’utilisation de NUMA dans SQL Server atténue la ligne entre les optimisations matérielles et de bases de données, une troisième section décrit en détail les affinitization et la gouvernance des ressources du processeur.

> [!TIP]
> Si vous débutez avec SQL Server, nous vous recommandons vivement de consulter le Guide d’optimisation des performances d’SQL Server: [Surveiller et régler les performances](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance).

## <a name="hardware-optimization"></a>Optimisation matérielle

L’optimisation de l’ordinateur serveur est importante pour s’assurer que vous disposez des ressources nécessaires pour exécuter des scripts externes. Lorsque les ressources sont limitées, vous pouvez voir des symptômes tels que ceux-ci:

- L’exécution du travail est différée ou annulée pour hiérarchiser les autres opérations de base de données
- Erreur «quota dépassé» provoquant l’arrêt du script R sans fin
- Données chargées dans la mémoire R tronquées, pour les résultats incomplets

### <a name="memory"></a>Mémoire

La quantité de mémoire disponible sur l’ordinateur peut avoir un impact important sur les performances des algorithmes d’analyse avancés. Une mémoire insuffisante peut affecter le degré de parallélisme lors de l’utilisation du contexte de calcul SQL. Cela peut aussi affecter la taille de segment (lignes par opération de lecture) qui peut être traitée, ainsi que le nombre de sessions simultanées qui peuvent être prises en charge.

Un minimum de 32 Go est fortement recommandé. Si vous avez plus de 32 Go disponibles, vous pouvez configurer la source de données SQL pour qu’elle utilise plus de lignes dans chaque opération de lecture afin d’améliorer les performances.

Vous pouvez également gérer la mémoire utilisée par l’instance. Par défaut, SQL Server est prioritaire sur les processus de script externes lorsque la mémoire est allouée. Dans une installation par défaut de R services, seules 20% de la mémoire disponible sont allouées à R.

En règle générale, ce n’est pas suffisant pour les tâches de science des données, mais vous ne souhaitez pas que vous ne soyez privé de mémoire SQL Server. Vous devez expérimenter et ajuster l’allocation de mémoire entre le moteur de base de données, les services associés et les scripts externes, en sachant que la configuration optimale varie en fonction de la casse.

Pour le modèle de correspondance de reprise, l’utilisation de script externe était lourde et aucun autre service de moteur de base de données n’était en cours d’exécution. par conséquent, les ressources allouées aux scripts externes ont été augmentées à 70%, ce qui était la meilleure configuration pour les performances des scripts.

### <a name="power-options"></a>Options d’alimentation

Sur le système d’exploitation Windows, vous devez utiliser l’option d’alimentation **hautes performances** . L’utilisation d’un autre paramètre d’alimentation entraîne une baisse des performances ou une incohérence lors de l’utilisation de SQL Server.

### <a name="disk-io"></a>E/S disque

Les tâches de formation et de prédiction utilisant R services sont liées aux e/s par nature et dépendent de la vitesse des disques sur lesquels la base de données est stockée. Les lecteurs plus rapides, comme les disques SSD (Solid-State Drives) peuvent vous aider.

Les E/S disque sont aussi affectées par les autres applications qui accèdent au disque. Tel est le cas, par exemple, des opérations de lecture dans une base de données qui sont le fait d’autres clients. Les performances d’E/S disque peuvent aussi être affectées par les paramètres du système de fichiers utilisé, notamment la taille de bloc utilisée par le système de fichiers.

Si plusieurs lecteurs sont disponibles, stockez les bases de données sur un autre lecteur que SQL Server afin que les demandes pour le moteur de base de données n’atteignent pas le même disque que les demandes de données stockées dans la base de données.

Par ailleurs, les E/S disque peuvent avoir un impact important sur les performances quand les fonctions d’analyse RevoScaleR en cours d’exécution utilisent plusieurs itérations en phase d’apprentissage. Par exemple, `rxLogit` `rxDTree` `rxBTrees` ,, et utilisent plusieurs itérations. `rxDForest` Lorsque la source de données est SQL Server, ces algorithmes utilisent des fichiers temporaires qui sont optimisés pour capturer les données. Ces fichiers sont automatiquement nettoyés en fin de session. Le fait de disposer d’un disque hautes performances pour les opérations de lecture/écriture peut améliorer considérablement le temps total écoulé pour ces algorithmes.

> [!NOTE]
> Les versions antérieures de R services ont nécessité la prise en charge des noms de fichiers 8,3 sur les systèmes d’exploitation Windows. Cette restriction a été levée après Service Pack 1. Toutefois, vous pouvez utiliser fsutil. exe pour déterminer si un lecteur prend en charge les noms de fichiers 8,3 ou pour activer la prise en charge si ce n’est pas le cas.

### <a name="paging-file"></a>Fichier d’échange

Le système d’exploitation Windows utilise un fichier de pagination pour gérer les vidages sur incident et stocker les pages de mémoire virtuelle. Si vous constatez une pagination excessive, envisagez d’augmenter la capacité de la mémoire physique de l’ordinateur. Même si une capacité de mémoire physique supérieure n’est pas propre à éliminer la pagination, elle en réduit la nécessité.

La rapidité du disque sur lequel est stocké le fichier d’échange peut aussi affecter les performances. En stockant le fichier d’échange sur un disque SSD ou en utilisant plusieurs fichiers d’échange sur plusieurs disques SSD, il est possible d’améliorer les performances.

Pour plus d’informations sur le dimensionnement du fichier d’échange, consultez [Comment déterminer la taille de fichier d’échange appropriée pour les versions 64 bits de Windows](https://support.microsoft.com/kb/2860880).

## <a name="optimizations-at-instance-or-database-level"></a>Optimisations au niveau de l’instance ou de la base de données

L’optimisation de l’instance de SQL Server est la clé de l’efficacité de l’exécution des scripts externes.

> [!NOTE]
> Les paramètres optimaux varient en fonction de la taille et du type de vos données, du nombre de colonnes que vous utilisez pour la notation ou de l’apprentissage d’un modèle.
> 
> Vous pouvez passer en revue les résultats des optimisations spécifiques dans le dernier article: [Réglage des performances-résultats de l’étude de cas](../../advanced-analytics/r/performance-case-study-r-services.md)
> 
> Pour obtenir des exemples de scripts, consultez le [référentiel GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)distinct.

### <a name="table-compression"></a>Compression de table

Les performances d’e/s peuvent souvent être améliorées à l’aide de la compression ou d’un magasin de données en colonnes. En règle générale, les données sont souvent répétées dans plusieurs colonnes d’une table, de sorte que l’utilisation d’un ColumnStore tire parti de ces répétitions lors de la compression des données.

Un ColumnStore peut ne pas être aussi efficace s’il existe de nombreuses insertions dans la table, mais est un bon choix si les données sont statiques ou uniquement modifiées rarement. Si l’utilisation d’une banque de colonnes n’est pas appropriée, l’activation de la compression sur une table principale de lignes permet d’améliorer les E/S.

Pour plus d’informations, consultez les documents suivants :

+ [Compression des données](../../relational-databases/data-compression/data-compression.md)

+ [Activer la compression sur une table ou un index](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [Guide des index columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>Tables optimisées en mémoire

De nos jours, la mémoire n’est plus un problème pour les ordinateurs modernes. À mesure que les spécifications matérielles continuent de s’améliorer, il est relativement facile d’acquérir de la mémoire vive à des valeurs correctes. Toutefois, dans le même temps, les données sont produites plus rapidement que jamais, et les données doivent être traitées avec une faible latence.

Les tables mémoire optimisées représentent une solution, en ce qu’elles tirent parti de la grande quantité de mémoire disponible sur les ordinateurs avancés pour résoudre le problème de Big Data. Les tables optimisées en mémoire résident principalement en mémoire, de sorte que les données sont lues et écrites dans la mémoire. Pour durabilité, une deuxième copie de la table est conservée sur le disque et les données sont uniquement lues à partir du disque pendant la récupération de la base de données.

Si vous avez besoin de lire et d’écrire fréquemment dans les tables, les tables optimisées en mémoire peuvent être utiles avec une évolutivité élevée et une faible latence.  Dans le scénario de reprise, l’utilisation de tables optimisées en mémoire nous permettait de lire toutes les fonctionnalités de reprise à partir de la base de données et de les stocker dans la mémoire principale, pour les faire correspondre aux nouvelles ouvertures de travail. Cela réduit considérablement les e/s disque.

Des gains de performances supplémentaires ont été réalisés en utilisant une table mémoire optimisée dans le processus d’écriture de prédictions dans la base de données à partir de plusieurs lots simultanés. L’utilisation de tables optimisées en mémoire sur SQL Server activé une faible latence sur les écritures et les lectures de table.

L’expérience était également transparente pendant le développement. Les tables optimisées en mémoire durables ont été créées au moment de la création de la base de données. Par conséquent, le développement a utilisé le même Workflow indépendamment de l’emplacement de stockage des données.

### <a name="processor"></a>Processeur

SQL Server pouvez effectuer des tâches en parallèle à l’aide des cœurs disponibles sur la machine. plus le nombre de cœurs disponibles est grand, plus les performances sont élevées. Bien qu’augmenter le nombre de cœurs peut ne pas être utile pour les opérations de liaison d’e/s, les algorithmes liés aux PROCESSEURs bénéficient d’UC plus rapides avec de nombreux cœurs.

Étant donné que le serveur est normalement utilisé par plusieurs utilisateurs simultanément, l’administrateur de base de données doit déterminer le nombre idéal de cœurs nécessaires pour prendre en charge les calculs de charge de travail de pointe.

### <a name="resource-governance"></a>Gouvernance des ressources

Dans les éditions qui prennent en charge Resource Governor, vous pouvez utiliser des pools de ressources pour spécifier que certaines charges de travail sont allouées à un certain nombre de processeurs. Vous pouvez également gérer la quantité de mémoire allouée à des charges de travail spécifiques.

La gouvernance des ressources dans SQL Server vous permet de centraliser la surveillance et le contrôle des diverses ressources utilisées par SQL Server et par R. Par exemple, vous pouvez allouer la moitié de la mémoire disponible pour le moteur de base de données, afin de garantir que les services principaux peuvent toujours s’exécuter en dépit de charges de travail plus lourdes transitoires.

La valeur par défaut de la consommation de mémoire par les scripts externes est limitée à 20% de la mémoire totale disponible pour SQL Server elle-même. Cette limite est appliquée par défaut pour s’assurer que toutes les tâches qui reposent sur le serveur de base de données ne sont pas gravement affectées par les travaux R de longue durée. Cependant, l’administrateur de base de données peut modifier ces limites. Dans de nombreux cas, la limite de 20% n’est pas suffisante pour prendre en charge des charges de travail de Machine Learning graves.

Les options de configuration prises en charge sont **MAX_CPU_PERCENT**, **MAX_MEMORY_PERCENT**et **MAX_PROCESSES**. Pour afficher les paramètres actuels, utilisez l’instruction suivante:`SELECT * FROM sys.resource_governor_external_resource_pools`

-  Si le serveur est principalement utilisé pour R services, il peut être utile d’augmenter la valeur de MAX_CPU_PERCENT à 40% ou 60%.

-  Si de nombreuses sessions R doivent utiliser le même serveur en même temps, les trois paramètres doivent être augmentés.

Pour modifier les valeurs de ressource allouées, utilisez des instructions T-SQL.

+ Cette instruction définit l’utilisation de la mémoire à 40%:`ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ Cette instruction définit les trois valeurs configurables:`ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ Si vous modifiez un paramètre de mémoire, de processeur ou de processus maximal et que vous souhaitez appliquer les paramètres immédiatement, exécutez l’instruction suivante:`ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>Soft-NUMA, NUMA matériel et affinité du processeur

Lorsque vous utilisez SQL Server comme contexte de calcul, vous pouvez parfois obtenir de meilleures performances en réglant les paramètres relatifs à NUMA et à l’affinité du processeur. 

Les systèmes dotés de la technologie _NUMA matérielle_ possèdent plus d’un bus système, chacun desservant un petit ensemble de processeurs. Chaque UC peut accéder à la mémoire associée à d’autres groupes de manière cohérente. Chaque groupe est appelé nœud NUMA. Si vous possédez un matériel NUMA, il peut être configuré de façon à utiliser la mémoire entrelacée au lieu de l'accès NUMA. Dans ce cas, Windows et par conséquent SQL Server ne le reconnaît pas comme NUMA. 

Vous pouvez exécuter la requête suivante pour rechercher le nombre de nœuds de mémoire disponibles pour SQL Server:

```sql
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

Si la requête retourne un seul nœud de mémoire (nœud 0), soit vous n’avez pas de matériel NUMA, soit le matériel est configuré comme entrelacé (non-NUMA). SQL Server ignore également le NUMA matériel lorsqu’il y a quatre processeurs ou moins, ou si au moins un nœud n’a qu’un seul processeur.

Si votre ordinateur possède plusieurs processeurs, mais pas le matériel-NUMA, vous pouvez également utiliser [soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) pour subdiviser les UC en groupes plus petits.  Dans SQL Server 2016 et SQL Server 2017, la fonctionnalité soft-NUMA est automatiquement activée au démarrage du service SQL Server.

Lorsque soft-NUMA est activé, SQL Server gère automatiquement les nœuds pour vous; Toutefois, pour optimiser des charges de travail spécifiques, vous pouvez désactiver l' _affinité logicielle_ et configurer manuellement l’affinité du processeur pour les nœuds NUMA conditionnels. Cela peut vous permettre de mieux contrôler les charges de travail qui sont affectées aux nœuds, en particulier si vous utilisez une édition de SQL Server qui prend en charge la gouvernance des ressources. En spécifiant l’affinité du processeur et en alignant les pools de ressources avec des groupes de processeurs, vous pouvez réduire la latence et vous assurer que les processus associés sont exécutés dans le même nœud NUMA.

Le processus global de configuration de l’affinité soft-NUMA et de l’UC pour la prise en charge des charges de travail R est le suivant:

1. Activer soft-NUMA, le cas échéant
2. Définir l’affinité du processeur
3. Créer des pools de ressources pour les processus externes, à l’aide de [Resource Governor](../r/resource-governance-for-r-services.md)
4. Affecter les [groupes de charge de travail](../../relational-databases/resource-governor/resource-governor-workload-group.md) à des groupes d’affinités spécifiques

Pour plus d’informations, y compris des exemples de code, consultez ce didacticiel: [Trucs et astuces pour l’optimisation SQL (ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Autres ressources:**

+ [Soft-NUMA dans SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Comment mapper des nœuds soft-NUMA à des processeurs

## <a name="task-specific-optimizations"></a>Optimisations spécifiques aux tâches

Cette section résume les méthodes adoptées dans ces études de cas et dans d’autres tests pour optimiser des charges de travail Machine Learning spécifiques. Les charges de travail courantes incluent la formation du modèle, l’extraction des fonctionnalités et l’ingénierie des caractéristiques, ainsi que divers scénarios de notation: une seule ligne, un petit lot et un grand lot.

### <a name="feature-engineering"></a>Ingénierie des caractéristiques

L’un des points faibles de R est qu’il est généralement traité sur un processeur unique. Il s’agit d’un goulot d’étranglement des performances majeur pour de nombreuses tâches, en particulier pour l’ingénierie des fonctionnalités. Dans la solution de reprise correspondante, la tâche d’ingénierie des caractéristiques a créé 2 500 fonctionnalités inter-produits qui devaient être combinées avec les fonctionnalités 100 d’origine. Cette tâche prend beaucoup de temps si tout a été effectué sur une seule UC.

Il existe plusieurs façons d’améliorer les performances de l’ingénierie des fonctionnalités. Vous pouvez optimiser votre code R et conserver l’extraction des fonctionnalités au sein du processus de modélisation ou déplacer le processus d’ingénierie des fonctionnalités dans SQL.

- À l’aide de R. Vous définissez une fonction et la transmettez comme argument à [rxTransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform) pendant l’apprentissage. Si le modèle prend en charge le traitement parallèle, la tâche d’ingénierie des fonctionnalités peut être traitée à l’aide de plusieurs processeurs. À l’aide de cette approche, l’équipe de science des données a constaté une amélioration des performances de 16% en termes de temps de score. Toutefois, cette approche nécessite un modèle qui prend en charge la parallélisation et une requête qui peut être exécutée à l’aide d’un plan parallèle.

- Utilisez R avec un contexte de calcul SQL. Dans un environnement multiprocesseur avec des ressources isolées disponibles pour l’exécution de lots distincts, vous pouvez obtenir une plus grande efficacité en isolant les requêtes SQL utilisées pour chaque lot, en extrayant les données des tables et en contraignant les données sur le même groupe de charge de travail. Les méthodes utilisées pour isoler les lots incluent le partitionnement et l’utilisation de PowerShell pour exécuter des requêtes distinctes en parallèle.

- Exécution en parallèle ad hoc: Dans un contexte de calcul SQL Server, vous pouvez vous appuyer sur le moteur de base de données SQL pour appliquer une exécution parallèle si possible, et si cette option est jugée plus efficace.

- Utilisez T-SQL dans un processus caractérisation distinct. Le précalcul des données de fonctionnalités à l’aide de SQL est généralement plus rapide.

### <a name="prediction-scoring-in-parallel"></a>Prédiction (notation) en parallèle

L’un des avantages de SQL Server est sa capacité à gérer un volume important de lignes en parallèle. L’un de ces avantages n’est pas le même que celui des notations. En général, le modèle n’a pas besoin d’accéder à toutes les données pour la notation. vous pouvez donc partitionner les données d’entrée, chaque groupe de charge de travail traitant une tâche.

Vous pouvez également envoyer les données d’entrée sous la forme d’une requête unique, puis SQL Server analyse la requête. Si vous pouvez créer un plan de requête parallèle pour les données d’entrée, il partitionne automatiquement les données affectées aux nœuds et effectue également des jointures et des agrégations nécessaires en parallèle.

Si vous êtes intéressé par les détails de la définition d’une procédure stockée pour une utilisation dans le calcul de score, consultez l’exemple de projet sur [GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips/SQLR) et recherchez le fichier «step5_score_for_matching. Sql». L’exemple de script suit également les heures de début et de fin des requêtes et écrit l’heure dans la console SQL pour vous permettre d’évaluer les performances.

### <a name="concurrent-scoring-using-resource-groups"></a>Évaluation simultanée à l’aide de groupes de ressources

Pour faire évoluer le problème de notation, il est recommandé d’adopter l’approche «Map-Reduce» dans laquelle des millions d’éléments sont divisés en plusieurs lots. Ensuite, plusieurs travaux de notation sont exécutés simultanément. Dans ce cadre, les lots sont traités sur différents PROCESSEURs, et les résultats sont collectés et réécrits dans la base de données.

Il s’agit de l’approche utilisée dans le scénario de reprise de correspondance; Toutefois, la gouvernance des ressources dans SQL Server est essentielle pour l’implémentation de cette approche. En configurant des groupes de charges de travail pour les tâches de script externes, vous pouvez acheminer des tâches de score R vers différents groupes de processeurs et obtenir un débit plus rapide.

La gouvernance des ressources permet également d’allouer la répartition des ressources disponibles sur le serveur (processeur et mémoire) pour réduire la concurrence des charges de travail. Vous pouvez configurer des fonctions classifieur pour faire la distinction entre les différents types de travaux R: par exemple, vous pouvez décider que la notation appelée à partir d’une application prend toujours la priorité, alors que les travaux de reformation ont une priorité basse. Cette isolation des ressources peut potentiellement améliorer la durée d’exécution et fournir des performances plus prévisibles.

### <a name="concurrent-scoring-using-powershell"></a>Évaluation simultanée à l’aide de PowerShell

Si vous décidez de partitionner les données vous-même, vous pouvez utiliser des scripts PowerShell pour exécuter plusieurs tâches de notation simultanées. Pour ce faire, utilisez l’applet de commande Invoke-SqlCmd et lancez les tâches de notation en parallèle.

Dans le scénario de reprise de correspondance, la concurrence a été conçue comme suit:

- 20 processeurs répartis en quatre groupes de cinq UC chacun. Chaque groupe de processeurs se trouve sur le même nœud NUMA.

- Le nombre maximal de lots simultanés a été défini à huit.

- Chaque groupe de charges de travail doit gérer deux tâches de notation. Dès qu’une tâche a terminé la lecture des données et commence le calcul de score, l’autre tâche peut commencer à lire les données de la base de données.

Pour afficher les scripts PowerShell pour ce scénario, ouvrez le fichier expériment. ps1 dans le [projet GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips).

### <a name="storing-models-for-prediction"></a>Stockage des modèles pour la prédiction

Lorsque l’apprentissage et l’évaluation se terminent et que vous avez sélectionné un modèle optimal, nous vous recommandons de stocker le modèle dans la base de données afin qu’il soit disponible pour les prédictions. Le chargement du modèle précalculé à partir de la base de données pour la prédiction est efficace, car SQL Server Machine Learning utilise des algorithmes de sérialisation spéciaux pour stocker et charger des modèles lors du déplacement entre R et la base de données.

> [!TIP]
> Dans SQL Server 2017, vous pouvez utiliser la fonction PREDICT pour effectuer un calcul de score même si R n’est pas installé sur le serveur. Les types de modèles limités sont pris en charge, à partir du package RevoScaleR.

Toutefois, selon l’algorithme que vous utilisez, certains modèles peuvent être assez volumineux, en particulier lors de l’apprentissage sur un jeu de données volumineux. Par exemple, les algorithmes tels que **LM** ou **GLM** génèrent beaucoup de données de synthèse ainsi que des règles. Comme il existe des limites sur la taille d’un modèle qui peut être stocké dans une colonne varbinary, nous vous recommandons d’éliminer les artefacts inutiles du modèle avant de stocker le modèle dans la base de données en vue de la production.

## <a name="articles-in-this-series"></a>Articles de cette série

[Réglage des performances pour R-introduction](../r/sql-server-r-services-performance-tuning.md)

[Réglage des performances pour la configuration de R-SQL Server](../r/sql-server-configuration-r-services.md)

[Réglage des performances pour le code R-R et l’optimisation des données](../r/r-and-data-optimization-r-services.md)

[Réglage des performances-résultats de l’étude de cas](../r/performance-case-study-r-services.md)
