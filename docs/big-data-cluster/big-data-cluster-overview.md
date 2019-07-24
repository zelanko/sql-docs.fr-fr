---
title: Que sont les clusters Big Data?
titleSuffix: SQL Server big data clusters
description: En savoir plus sur les clusters SQL Server 2019 Big Data (version préliminaire) qui s’exécutent sur Kubernetes et fournissent des options de montée en charge pour les données relationnelles et HDFS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0beb4ea57ba6c2591e5b2c06a7775fc2d7e8b26c
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419499"
---
# <a name="what-are-sql-server-big-data-clusters"></a>Que sont les clusters de Big Data SQL Server ?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

À partir de, SQL Server Clusters Big Data vous permettent de déployer des clusters évolutifs de conteneurs SQL Server, Spark et HDFS s’exécutant sur Kubernetes. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Ces composants sont exécutés côte à côte pour vous permettre de lire, écrire et traiter des Big Data à partir de Transact-SQL ou Spark, ce qui vous permet de combiner et d’analyser facilement vos données relationnelles de grande valeur avec des Big Data de volume élevé.

Pour plus d’informations sur les nouvelles fonctionnalités et les problèmes connus pour la dernière version, consultez les [notes de publication](release-notes-big-data-cluster.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Scénarios

SQL Server les clusters Big Data offrent une certaine flexibilité dans la façon dont vous interagissez avec votre Big Data. Vous pouvez interroger des sources de données externes, stocker des Big Data dans HDFS géré par SQL Server ou interroger des données à partir de plusieurs sources de données externes via le cluster. Vous pouvez ensuite utiliser les données de l’intelligence artificielle, du Machine Learning et d’autres tâches d’analyse. Les sections suivantes fournissent plus d’informations sur ces scénarios.

### <a name="data-virtualization"></a>Virtualisation de données

En tirant parti de [SQL Server Polybase](../relational-databases/polybase/polybase-guide.md), SQL Server les clusters Big Data peuvent interroger des sources de données externes sans déplacer ou copier les données. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]introduit de nouveaux connecteurs dans les sources de données.

![Virtualisation de données](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Data Lake

Un cluster SQL Server Big Data comprend un pool de *stockage*HDFS évolutif. Cela peut être utilisé pour stocker des Big Data, potentiellement ingérées à partir de plusieurs sources externes. Une fois que le Big Data est stocké dans HDFS dans le cluster Big Data, vous pouvez analyser et interroger les données et les combiner avec vos données relationnelles.

![Data Lake](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>Mini-Data Warehouse avec montée en puissance parallèle

Les clusters de SQL Server Big Data fournissent un calcul et un stockage avec montée en puissance parallèle pour améliorer les performances d’analyse des données. Les données provenant de diverses sources peuvent être ingérées et réparties entre les nœuds du *pool de données* en tant que cache pour une analyse plus poussée.

![Mini-Data Warehouse](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>IA et Machine Learning intégrés

SQL Server les clusters Big Data activent les tâches AI et Machine Learning sur les données stockées dans les pools de stockage HDFS et les pools de données. Vous pouvez utiliser Spark ainsi que des outils AI intégrés dans SQL Server, à l’aide de R, Python, Scala ou Java.

![IA et ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Gestion et surveillance

La gestion et la surveillance sont fournies par le biais d’une combinaison d’outils en ligne de commande, d’API, de portails et de vues de gestion dynamique.

Vous pouvez utiliser Azure Data Studio pour effectuer diverses tâches sur le cluster Big Data. Cette option est activée par la nouvelle **Extension SQL Server 2019 (version préliminaire)** . Cette extension fournit les éléments suivants:

- Extraits de code intégrés pour les tâches de gestion courantes.
- Possibilité de parcourir les HDFS, de télécharger des fichiers, de prévisualiser des fichiers et de créer des répertoires.
- Possibilité de créer, d’ouvrir et d’exécuter des blocs-notes compatibles Jupyter.
- Assistant virtualisation des données pour simplifier la création de sources de données externes.

## <a id="architecture"></a>SOA

Un cluster SQL Server Big Data est un cluster de conteneurs Linux orchestrés par [Kubernetes](https://kubernetes.io/docs/concepts/).

### <a name="kubernetes-concepts"></a>Concepts Kubernetes

Kubernetes est un conteneur d’Orchestrator Open source, qui peut mettre à l’échelle des déploiements de conteneurs en fonction des besoins. Le tableau suivant définit une terminologie importante pour les Kubernetes:

|||
|:--|:--|
| **Cluster** | Un cluster Kubernetes est un ensemble d’ordinateurs, appelés nœuds. Un nœud contrôle le cluster et est désigné comme nœud principal; les nœuds restants sont des nœuds Worker. Le maître Kubernetes est chargé de la distribution du travail entre les Workers et de la surveillance de l’intégrité du cluster. |
| **Nœud** | Un nœud exécute des applications en conteneur. Il peut s’agir d’un ordinateur physique ou d’une machine virtuelle. Un cluster Kubernetes peut contenir un mélange d’ordinateurs physiques et de nœuds de machines virtuelles. |
| **Pod** | Une Pod est l’unité de déploiement atomique de Kubernetes. Un Pod est un groupe logique d’un ou de plusieurs conteneurs, et les ressources associées, nécessaires pour exécuter une application. Chaque POD s’exécute sur un nœud; un nœud peut exécuter un ou plusieurs pod. Le maître Kubernetes affecte automatiquement des Pod aux nœuds du cluster. |
| &nbsp; ||

Dans SQL Server Clusters Big Data, Kubernetes est responsable de l’état des clusters Big Data SQL Server. Kubernetes crée et configure les nœuds de cluster, assigne des Pod aux nœuds et analyse l’intégrité du cluster.

### <a name="big-data-clusters-architecture"></a>Architecture des clusters Big Data

Le diagramme suivant montre les composants d’un cluster Big Data pour SQL Server.

![Vue d’ensemble de l’architecture](media/big-data-cluster-overview/architecture-diagram-overview.png)

### <a id="controlplane"></a>SideWinder

Le contrôleur assure la gestion et la sécurité du cluster. Il contient le service cntrol, le magasin de configuration et d’autres services de niveau cluster tels que Kibana, Grafana et la recherche élastique.

### <a id="computeplane"></a>Pool de calcul

Le pool de calcul fournit des ressources de calcul au cluster. Il contient des nœuds exécutant des blocs de SQL Server sur Linux. Les gousses du pool de calcul sont divisées en *instances de calcul SQL* pour des tâches de traitement spécifiques. 

### <a id="dataplane"></a>Pool de données

Le pool de données est utilisé pour la persistance et la mise en cache des données. Le pool de données est constitué d’un ou plusieurs pod en cours d’exécution SQL Server sur Linux. Il est utilisé pour ingérer des données à partir de requêtes SQL ou de travaux Spark. SQL Server Big Data les mini-Data Warehouses de cluster sont conservés dans le pool de données. 

### <a name="storage-pool"></a>Pool de stockage

Le pool de stockage est constitué de modules de pool de stockage constitués de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage d’un cluster SQL Server Big Data sont membres d’un cluster HDFS.

> [!TIP]
> Pour une analyse approfondie de l’architecture et de l’installation de Big Data cluster [, consultez l’atelier: Architecture](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)des clusters de Big Data Microsoft SQL Server.

## <a name="next-steps"></a>Étapes suivantes

SQL Server Clusters Big Data est tout d’abord disponible en version préliminaire publique limitée par le biais du programme d’adoption précoce de SQL Server 2019. Pour demander l’accès, inscrivez-vous [ici](https://aka.ms/eapsignup)et spécifiez votre intérêt pour essayer Big Data clusters. Microsoft triera toutes les demandes et répondra dès que possible.
