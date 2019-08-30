---
title: Qu’est-ce qu’un cluster Big Data?
titleSuffix: SQL Server Big Data Clusters
description: En savoir [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] plus sur (version préliminaire) qui s’exécute sur Kubernetes et fournissent des options de montée en charge pour les données relationnelles et HDFS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c75005c35e743a87ff742352946c4fdde5fcf0b8
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153649"
---
# <a name="what-are-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Que sont [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

À compter de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)],vous permet de déployer des clusters évolutifs de conteneurs SQL Server, Spark et HDFS s’exécutant sur Kubernetes. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Ces composants sont exécutés côte à côte pour que vous puissiez lire, écrire et traiter du Big Data à partir de Transact-SQL ou Spark, afin de pouvoir combiner et analyser facilement vos données relationnelles de grande valeur avec du Big Data volumineux.

Pour plus d’informations sur les nouvelles fonctionnalités et les problèmes connus concernant la dernière version, consultez les [notes de publication](release-notes-big-data-cluster.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Scénarios

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]offrez de la flexibilité dans la façon dont vous interagissez avec vos Big Data. Vous pouvez interroger des sources de données externes, stocker du Big Data dans un système HDFS géré par SQL Server ou interroger des données à partir de plusieurs sources de données externes par le biais du cluster. Vous pouvez ensuite utiliser les données pour l’intelligence artificielle, le Machine Learning et d’autres tâches d’analyse. Les sections ci-dessous fournissent des informations supplémentaires sur ces scénarios.

### <a name="data-virtualization"></a>Virtualisation de données

En tirant parti de [SQL Server](../relational-databases/polybase/polybase-guide.md)Polybase [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] , peut interroger des sources de données externes sans déplacer ou copier les données. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit de nouveaux connecteurs aux sources de données.

![Virtualisation de données](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Lac de données

Un cluster Big Data SQL Server comprend un *pool de stockage* HDFS scalable. Ce dernier peut servir à stocker du Big Data, éventuellement ingéré à partir de plusieurs sources externes. Une fois le Big Data stocké dans HDFS au sein du cluster Big Data, vous pouvez analyser et interroger les données et les combiner avec vos données relationnelles.

![Lac de données](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>DataMart avec scale-out

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]fournir le calcul et le stockage avec montée en puissance parallèle pour améliorer les performances d’analyse des données. Les données provenant de diverses sources peuvent être ingérées et réparties entre les nœuds du *pool de données* en tant que cache pour une analyse plus poussée.

![DataMart](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>IA et Machine Learning intégrés

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]activez les tâches IA et Machine Learning sur les données stockées dans les pools de stockage HDFS et les pools de données. Vous pouvez utiliser Spark ainsi que des outils AI intégrés dans SQL Server, à l’aide de R, Python, Scala ou Java.

![IA et ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Gestion et surveillance

La gestion et la supervision sont fournies par le biais d’une combinaison d’outils en ligne de commande, d’API, de portails et de vues de gestion dynamique.

Vous pouvez utiliser Azure Data Studio pour effectuer diverses tâches sur le cluster Big Data. La nouvelle **extension SQL Server 2019 (préversion)** le permet. Cette extension offre :

- Des extraits de code intégrés pour les tâches de gestion courantes
- La possibilité de parcourir le système HDFS, de charger des fichiers, de prévisualiser des fichiers et de créer des répertoires
- La possibilité de créer, d’ouvrir et d’exécuter des notebooks compatibles Jupyter
- Un assistant Virtualisation des données pour simplifier la création de sources de données externes

## <a id="architecture"></a> Architecture

Un cluster Big Data SQL Server est un cluster de conteneurs Linux orchestrés par [Kubernetes](https://kubernetes.io/docs/concepts/).

### <a name="kubernetes-concepts"></a>Concepts de Kubernetes

Kubernetes est un orchestrateur de conteneurs open source, qui peut mettre à l’échelle des déploiements de conteneurs en fonction des besoins. Le tableau suivant définit certains termes importants liés à Kubernetes :

|||
|:--|:--|
| **Cluster** | Un cluster Kubernetes est un ensemble de machines, appelées nœuds. Un des nœuds, appelé nœud master, contrôle le cluster, tandis que les autres nœuds sont des nœuds Worker. Le master Kubernetes est chargé de la distribution du travail entre les Workers et de la supervision de l’intégrité du cluster. |
| **Nœud** | Un nœud exécute des applications conteneurisées. Il peut s’agir d’une machine physique ou d’une machine virtuelle. Un cluster Kubernetes peut contenir un mélange de nœuds de machine physique et de nœuds de machine virtuelle. |
| **Pod** | Un pod est l’unité de déploiement atomique de Kubernetes. Un pod regroupe, sous forme logique, un ou plusieurs conteneurs ainsi que les ressources associées nécessaires pour exécuter une application. Chaque pod s’exécute sur un nœud ; un nœud peut exécuter un ou plusieurs pod. Le master Kubernetes attribue automatiquement des pods aux nœuds du cluster. |
| &nbsp; ||

Dans [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], Kubernetes est responsable de l’état [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]de. Kubernetes crée et configure les nœuds de cluster, assigne des Pod aux nœuds et analyse l’intégrité du cluster.

### <a name="big-data-clusters-architecture"></a>Architecture des clusters Big Data

Le diagramme suivant montre les composants d’un cluster Big Data pour SQL Server.

![Vue d’ensemble de l’architecture](media/big-data-cluster-overview/architecture-diagram-overview.png)

### <a id="controlplane"></a> Contrôleur

Le contrôleur assure la gestion et la sécurité du cluster. Il contient le service de contrôle, le magasin de configuration et d’autres services de niveau cluster tels que Kibana, Grafana et Elasticsearch.

### <a id="computeplane"></a> Pool de calcul

Le pool de calcul fournit des ressources de calcul au cluster. Il contient des nœuds exécutant des pods SQL Server sur Linux. Les pods du pool de calcul sont divisés en *instances de calcul SQL* pour des tâches de traitement spécifiques. 

### <a id="dataplane"></a> Pool de données

Le pool de données est utilisé pour la persistance et la mise en cache des données. Le pool de données est constitué d’un ou plusieurs pods exécutant SQL Server sur Linux. Il est utilisé pour l’ingestion des données à partir de requêtes SQL ou de travaux Spark. Les DataMarts de cluster Big Data SQL Server sont conservés dans le pool de données. 

### <a name="storage-pool"></a>Pool de stockage

Le pool de stockage est composé de pods de pool de stockage constitués de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage d’un cluster Big Data SQL Server sont membres d’un cluster HDFS.

> [!TIP]
> Pour une présentation approfondie de l’architecture et de l’installation des clusters Big Data, consultez [Atelier : [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Architecture](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)Microsoft.

## <a name="next-steps"></a>Étapes suivantes

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]est d’abord disponible en version préliminaire publique limitée par le biais du programme d’adoption SQL Server 2019. Pour demander l’accès, inscrivez-vous [ici](https://aka.ms/eapsignup) et indiquez les raisons qui vous poussent à essayer des clusters Big Data. Microsoft triera toutes les demandes et répondra dès que possible.
