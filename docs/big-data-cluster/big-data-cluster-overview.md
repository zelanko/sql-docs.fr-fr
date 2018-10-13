---
title: Qu’est SQL Server 2019 des clusters de données volumineuses ? | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: overview
ms.prod: sql
ms.openlocfilehash: 3a18eeca5bd6af2fb0bb9562f126351ac4d3f1c9
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085055"
---
# <a name="what-are-sql-server-2019-big-data-clusters"></a>Quelles sont les clusters SQL Server 2019 big data ?

En commençant par [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)], clusters de données volumineuses de SQL Server que vous puissiez déployer des clusters SCALABLES de SQL Server, Spark et HDFS les conteneurs Docker s’exécutant sur Kubernetes. Ces composants sont en cours d’exécution côte à côte pour vous permettent de lire, écrire et traiter les big data à partir de Transact-SQL ou Spark. Clusters de données volumineuses de SQL Server permettent de facilement combiner et analyser vos données relationnelles de valeur élevée avec d’importants volumes de données volumineuses.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>Scénarios

Clusters de données volumineuses de SQL Server offrent la flexibilité dans la façon dont vous interagissez avec vos données Big Data. Vous pouvez interroger des sources de données externes, stocker des données volumineuses dans HDFS gérés par SQL Server, ou extraire les données à partir de plusieurs sources de données dans le cluster. Vous pouvez ensuite utiliser les données pour l’intelligence artificielle, apprentissage automatique et autres tâches d’analyse. Les sections suivantes fournissent plus d’informations sur ces scénarios.

### <a name="data-virtualization"></a>Virtualisation des données

En tirant parti de [SQL Server PolyBase](../relational-databases/polybase/polybase-guide.md), clusters de données volumineuses de SQL Server peuvent interroger les sources de données externes sans les importer. [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] introduit de nouveaux connecteurs à des sources de données.

![Virtualisation des données](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Lac de données

Un cluster de données volumineux de SQL Server inclut un HDFS évolutif *pool de stockage*. Cela peut servir à stocker directement des données volumineuses, potentiellement provenir de plusieurs sources externes. Une fois dans le cluster de données volumineux, analyse et interroger les données et associez-le à vos données relationnelles de valeur élevée.

![Lac de données](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>Montée en puissance Datamart

Les clusters de données volumineuses de SQL Server fournissent calcul de montée en puissance et de stockage pour améliorer les performances de l’analyse des données. Données à partir de différentes sources peuvent être ingérées et réparties sur *pool de données* nœuds pour une analyse plus approfondie.

![mini-Data Warehouse](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>Intelligence artificielle intégrée et l’apprentissage

Les clusters de données volumineuses de SQL Server autorisent intelligence artificielle et tâches sur les données stockées dans des pools de stockage HDFS de données et les pools de données d’apprentissage. Vous pouvez utiliser Spark, ainsi que des outils d’intelligence artificielle intégrés dans SQL Server, à l’aide de R, Python ou Java.

![Intelligence artificielle et ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>Gestion et surveillance

Gestion et surveillance sont fournies via une combinaison de composants open source, les outils SQL Server et les vues de gestion dynamique.

Le [portail d’administration de Cluster](cluster-admin-portal.md) est une interface web qui affiche l’état et l’intégrité des blocs dans le cluster. Il fournit également des liens vers d’autres tableaux de bord fournis par Grafana et Kibana.

Vous pouvez utiliser Azure Data Studio pour effectuer diverses tâches sur le cluster de données volumineuses. Cette option est activée par la nouvelle **2019 Extension (version préliminaire) de SQL Server**. Cette extension fournit :

- Extraits de code intégrés pour les tâches de gestion courantes.
- Rapports sur le nombre de pools de calcul et de l’état des travaux en cours d’exécution.
- Rapports sur l’état des travaux de HDFS et Spark.
- Possibilité de parcourir HDFS, télécharger des fichiers, afficher un aperçu des fichiers et créer des répertoires.
- Possibilité de créer, ouvrir et exécuter les blocs-notes Jupyter compatibles.
- Assistant de virtualisation des données pour simplifier la création de sources de données externes.

## <a id="architecture"></a> Architecture

Un cluster de données volumineux de SQL Server est un cluster de nœuds Linux orchestré par [Kubernetes](https://kubernetes.io/docs/concepts/).

### <a name="kubernetes-concepts"></a>Concepts de Kubernetes

Kubernetes est un orchestrateur de conteneur open source, ce qui peut mettre à l’échelle des déploiements de conteneurs en fonction de besoins. Le tableau suivant définit certains termes Kubernetes important :

|||
|--|--|
| **Cluster** | Un cluster Kubernetes est un ensemble d’ordinateurs, appelés nœuds. Un nœud de contrôle du cluster et il est le nœud principal ; les nœuds restants sont des nœuds de travail. Le maître de Kubernetes est chargé de distribuer le travail entre les workers et pour surveiller l’intégrité du cluster. |
| **Nœud** | Un nœud exécute des applications en conteneur. Il peut être un ordinateur physique ou une machine virtuelle. Un cluster Kubernetes peut contenir un mélange de nœuds de machine virtuelle et de la machine physiques. |
| **POD** | Un pod est l’unité atomique de Kubernetes. Un pod est un groupe logique d’un ou plusieurs conteneurs et des ressources associées, nécessaires pour exécuter une application. Chaque pod s’exécute sur un nœud ; un nœud peut exécuter une ou plusieurs pods. Le maître de Kubernetes affecte automatiquement des pods aux nœuds du cluster. |

Dans les clusters de données volumineuses de SQL Server, Kubernetes est responsable de l’état des clusters de données volumineuses de SQL Server ; Kubernetes génère et configure les nœuds de cluster, affecte des pods à nœuds et surveille l’intégrité du cluster.

### <a name="big-data-clusters-architecture"></a>architecture de clusters Big data

Nœuds du cluster sont organisées en trois plans logiques : le plan de contrôle, le volet de calcul et le plan de données. Chaque plan a différentes responsabilités dans le cluster. Tous les nœuds Kubernetes dans un cluster de données volumineux de SQL Server sont membre au moins un plan.

![Vue d’ensemble de l’architecture](media/big-data-cluster-overview/architecture-diagram-planes.png)

### <a id="controlplane"></a> Plan de contrôle

Le plan de contrôle fournit la gestion et la sécurité pour le cluster. Il contient le serveur maître de Kubernetes, le *instance principale de SQL Server*et d’autres services de niveau de cluster telles que le Metastore Hive et le pilote Spark.

### <a id="computeplane"></a> Plan de calcul

Le plan de calcul fournit des ressources de calcul au cluster. Il contient des nœuds exécutant SQL Server sur Linux pods. Le nombre de pods dans le plan de calcul est divisées en *pools de calcul* pour spécifique des tâches de traitement. Un pool de calcul peut agir comme un [PolyBase](../relational-databases/polybase/polybase-guide.md) groupe de scale-out pour les requêtes distribuées sur différentes sources de données, comme HDFS, Oracle, MongoDB ou Teradata.

### <a id="dataplane"></a> Plan de données

Le plan de données est utilisé pour la persistance des données et la mise en cache. Il contient le pool de données SQL et les nœuds de stockage.  Le pool de données SQL se compose d’un ou plusieurs nœuds exécutant SQL Server sur Linux. Il est utilisé pour recevoir les données à partir de requêtes SQL ou de travaux Spark. Données volumineuses de SQL Server cluster mini-Data Warehouses sont conservés dans le pool de données des données. Le pool de stockage se compose de stockage composés de nœuds de SQL Server sur Linux, Spark et HDFS. Tous les nœuds de stockage dans un cluster de données volumineux de SQL Server sont membres d’un cluster HDFS.

## <a name="next-steps"></a>Étapes suivantes

Clusters de données volumineuses de SQL Server est disponible en version préliminaire publique limitée par le biais du programme d’Adoption anticipée de SQL Server 2019. Pour demander l’accès, vous devez inscrire [ici](https://aka.ms/eapsignup)et spécifiez votre intérêt pour essayer les clusters de données volumineuses. Microsoft trier toutes les demandes et répondre dès que possible.