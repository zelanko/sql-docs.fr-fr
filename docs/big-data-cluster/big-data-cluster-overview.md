---
title: Quelles sont les clusters de données volumineuses ?
titleSuffix: SQL Server big data clusters
description: En savoir plus sur les clusters de données volumineuses de SQL Server 2019 (version préliminaire) qui s’exécute sur Kubernetes et options de montée en puissance pour relationnelles et les données HDFS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: dd9b649dbb7bf2fc68c34ae22a1d270515756df8
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729265"
---
# <a name="what-are-sql-server-big-data-clusters"></a>Que sont les clusters de Big Data SQL Server ?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

En commençant par [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)], clusters de données volumineuses de SQL Server que vous puissiez déployer des clusters SCALABLES de SQL Server, Spark et HDFS conteneurs s’exécutant sur Kubernetes. Ces composants sont en cours d’exécution côte à côte pour vous permettre de lire, écrire et traiter le big data à partir de Transact-SQL ou Spark, qui vous permet de facilement combiner et analyser vos données relationnelles de valeur élevée avec d’importants volumes de données volumineuses.

Pour plus d’informations sur les nouvelles fonctionnalités et les problèmes connus pour la version la plus récente, consultez le [notes de version](release-notes-big-data-cluster.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Scénarios

Clusters de données volumineuses de SQL Server offrent la flexibilité dans la façon dont vous interagissez avec vos données Big Data. Vous pouvez interroger des sources de données externes, le stockage de big data dans HDFS gérés par SQL Server, ou interroger des données à partir de plusieurs sources de données externes via le cluster. Vous pouvez ensuite utiliser les données pour l’intelligence artificielle, apprentissage automatique et autres tâches d’analyse. Les sections suivantes fournissent plus d’informations sur ces scénarios.

### <a name="data-virtualization"></a>Virtualisation de données

En tirant parti de [SQL Server PolyBase](../relational-databases/polybase/polybase-guide.md), clusters de données volumineuses de SQL Server peuvent interroger les sources de données externes sans déplacement ou copie des données. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit de nouveaux connecteurs à des sources de données.

![Virtualisation de données](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Lac de données

Un cluster de données volumineux de SQL Server inclut un HDFS évolutif *pool de stockage*. Cela peut être utilisé pour stocker des données volumineuses, potentiellement provenir de plusieurs sources externes. Une fois que les données volumineuses sont stockées dans HDFS dans le cluster de données volumineux, vous pouvez analyser et interroger les données et les associer à vos données relationnelles.

![Lac de données](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>Montée en puissance Datamart

Les clusters de données volumineuses de SQL Server fournissent calcul de montée en puissance et de stockage pour améliorer les performances de l’analyse des données. Données à partir de différentes sources peuvent être ingérées et réparties sur *pool de données* nœuds en tant que cache pour une analyse plus approfondie.

![mini-Data Warehouse](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>Intelligence artificielle intégrée et l’apprentissage

Les clusters de données volumineuses de SQL Server autorisent intelligence artificielle et tâches sur les données stockées dans des pools de stockage HDFS et les pools de données d’apprentissage. Vous pouvez utiliser Spark, ainsi que des outils d’intelligence artificielle intégrés dans SQL Server, à l’aide de R, Python, Scala ou Java.

![Intelligence artificielle et ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Gestion et surveillance

Gestion et surveillance sont fournies via une combinaison d’outils de ligne de commande, les API, les portails et les vues de gestion dynamique.

Vous pouvez utiliser Azure Data Studio pour effectuer diverses tâches sur le cluster de données volumineuses. Cette option est activée par la nouvelle **2019 Extension (version préliminaire) de SQL Server**. Cette extension fournit :

- Extraits de code intégrés pour les tâches de gestion courantes.
- Possibilité de parcourir HDFS, télécharger des fichiers, afficher un aperçu des fichiers et créer des répertoires.
- Possibilité de créer, ouvrir et exécuter les blocs-notes Jupyter compatibles.
- Assistant de virtualisation des données pour simplifier la création de sources de données externes.

## <a id="architecture"></a> Architecture

Un cluster de données volumineux de SQL Server est un cluster de conteneurs Linux orchestrés par [Kubernetes](https://kubernetes.io/docs/concepts/).

### <a name="kubernetes-concepts"></a>Concepts de Kubernetes

Kubernetes est un orchestrateur de conteneur open source, ce qui peut mettre à l’échelle des déploiements de conteneurs en fonction de besoins. Le tableau suivant définit certains termes Kubernetes important :

|||
|:--|:--|
| **Cluster** | Un cluster Kubernetes est un ensemble d’ordinateurs, appelés nœuds. Un nœud de contrôle du cluster et il est le nœud principal ; les nœuds restants sont des nœuds de travail. Le maître de Kubernetes est chargé de distribuer le travail entre les workers et pour surveiller l’intégrité du cluster. |
| **Nœud** | Un nœud exécute des applications en conteneur. Il peut être un ordinateur physique ou une machine virtuelle. Un cluster Kubernetes peut contenir un mélange de nœuds de machine virtuelle et de la machine physiques. |
| **Pod** | Un pod est l’unité atomique de déploiement de Kubernetes. Un pod est un groupe logique d’un ou plusieurs conteneurs- et associé les ressources nécessaires pour exécuter une application. Chaque pod s’exécute sur un nœud ; un nœud peut exécuter une ou plusieurs pods. Le maître de Kubernetes affecte automatiquement des pods aux nœuds du cluster. |
| &nbsp; ||

Dans les clusters de données volumineuses de SQL Server, Kubernetes est responsable de l’état des clusters de données volumineuses de SQL Server ; Kubernetes génère et configure les nœuds de cluster, affecte des pods à nœuds et surveille l’intégrité du cluster.

### <a name="big-data-clusters-architecture"></a>architecture de clusters Big data

Nœuds du cluster sont organisées en trois plans logiques : le plan de contrôle, le plan de calcul et le plan de données. Chaque plan a différentes responsabilités dans le cluster. Tous les nœuds Kubernetes dans un cluster de données volumineux de SQL Server héberge pods pour les composants au moins un plan.

![Vue d’ensemble de l’architecture](media/big-data-cluster-overview/architecture-diagram-planes.png)

### <a id="controlplane"></a> Plan de contrôle

Le plan de contrôle fournit la gestion et la sécurité pour le cluster. Il contient le serveur maître de Kubernetes, le *instance principale de SQL Server*et d’autres services de niveau de cluster telles que le Metastore Hive et le pilote Spark.

### <a id="computeplane"></a> Plan de calcul

Le plan de calcul fournit des ressources de calcul au cluster. Il contient des nœuds exécutant SQL Server sur Linux pods. Le nombre de pods dans le plan de calcul est divisées en *pools de calcul* pour spécifique des tâches de traitement. Un pool de calcul peut agir comme un [PolyBase](../relational-databases/polybase/polybase-guide.md) groupe de scale-out pour les requêtes distribuées sur différentes données sources, tels que HDFS, Oracle, MongoDB ou Teradata.

### <a id="dataplane"></a> Plan de données

Le plan de données est utilisé pour la persistance des données et la mise en cache. Il contient le pool de données SQL et le pool de stockage.  Le pool de données SQL se compose d’un ou plusieurs pods exécutant SQL Server sur Linux. Il est utilisé pour recevoir les données à partir de requêtes SQL ou de travaux Spark. Données volumineuses de SQL Server cluster mini-Data Warehouses sont conservés dans le pool de données des données. Le pool de stockage se compose de pods de pool de stockage constitués de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage dans un cluster de données volumineux de SQL Server sont membres d’un cluster HDFS.

> [!TIP]
> Pour obtenir une présentation détaillée dans l’architecture de cluster big data et l’installation, consultez [atelier : Architecture de clusters de données volumineuses de Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters).

## <a name="next-steps"></a>Étapes suivantes

Clusters de données volumineuses de SQL Server est disponible en version préliminaire publique limitée par le biais du programme d’Adoption anticipée de SQL Server 2019. Pour demander l’accès, vous devez inscrire [ici](https://aka.ms/eapsignup)et spécifiez votre intérêt pour essayer les clusters de données volumineuses. Microsoft trier toutes les demandes et répondre dès que possible.
