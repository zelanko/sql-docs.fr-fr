---
title: Haute disponibilité des conteneurs SQL Server
description: Cet article présente la haute disponibilité sur les conteneurs SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: aa54849c16ea9dfb821404b553b1e9183b61d66a
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68077469"
---
# <a name="high-availability-for-sql-server-containers"></a>Haute disponibilité des conteneurs SQL Server

Créer et gérer vos instances SQL Server en mode natif dans Kubernetes.

Déployez SQL Server sur des conteneurs Docker managés par [Kubernetes](https://kubernetes.io/). Dans Kubernetes, un conteneur avec une instance de SQL Server peut être récupéré automatiquement en cas de défaillance d’un nœud de cluster. Pour une disponibilité plus robuste, configurez le groupe de disponibilité SQL Server Always On avec des instances SQL Server dans des conteneurs sur un cluster Kubernetes. Cet article compare les deux solutions.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Comparer les versions de SQL Server sur Kubernetes

SQL Server 2017 fournit une image Docker qui peut être déployée sur Kubernetes. Vous pouvez configurer l’image avec une revendication de volume persistant Kubernetes (PVC). Kubernetes surveille le processus de SQL Server dans le conteneur. En cas d’échec du processus, du pod, du conteneur ou du nœud, Kubernetes démarre automatiquement une autre instance et se reconnecte au stockage.

SQL Server 2019 (préversion) introduit une architecture plus robuste avec un StatefulSet Kubernetes. Kubernetes orchestre les instances de SQL Server dans les images conteneur qui participent à un groupe de disponibilité Always On SQL Server. Ce modèle fournit une analyse d’intégrité améliorée, une récupération plus rapide, une sauvegarde de déchargement et une échelle en lecture.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Conteneur avec instance SQL Server sur Kubernetes

Kubernetes 1.6 et versions ultérieures prend en charge les [*classes de stockage*](https://kubernetes.io/docs/concepts/storage/storage-classes/), les [*revendications de volume persistant*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims) et le [*type de volume de disque Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

Dans cette configuration, Kubernetes joue le rôle de l’orchestrateur de conteneur. 

![Diagramme de la batterie de serveurs SQL Server Kubernetes](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Dans le diagramme précédent, `mssql-server` est une instance SQL Server (conteneur) dans un [*pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Un [jeu de réplicas](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) garantit que le pod est automatiquement récupéré après une défaillance de nœud. Les applications se connectent au service. Dans ce cas, le service représente un équilibreur de charge qui héberge une adresse IP restant la même après la défaillance de `mssql-server`.

Kubernetes orchestre les ressources dans le cluster. Lorsqu’un nœud hébergeant un conteneur d’instance SQL Server échoue, il fait démarrer un nouveau conteneur avec une instance SQL Server et l’attache au même stockage persistant.

SQL Server 2017 et versions ultérieures prennent en charge les conteneurs sur Kubernetes.

Pour créer un conteneur dans Kubernetes, consultez [Déployer un conteneur SQL Server dans Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Un groupe de disponibilité Always On SQL Server sur des conteneurs SQL Server dans Kubernetes

SQL Server 2019 prend en charge les groupes de disponibilité sur les conteneurs dans Kubernetes. Pour les groupes de disponibilité, déployez l'[opérateur Kubernetes](https://coreos.com/blog/introducing-operators.html) SQL Server sur votre cluster Kubernetes. L'opérateur aide à regrouper, déployer et gérer les instances SQL Server et le groupe de disponibilité dans un cluster.

![Groupe de disponibilité dans un conteneur Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

Dans l'image ci-dessus, un cluster Kubernetes à quatre nœuds héberge un groupe de disponibilité avec trois réplicas. La solution inclut les composants suivants :

* Un [*déploiement*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) Kubernetes. Le déploiement comprend l'opérateur et une table de configuration. Le déploiement décrit l'image du conteneur, le logiciel et les instructions nécessaires au déploiement des instances SQL Server pour le groupe de disponibilité.

* Trois nœuds, chacun hébergeant une ressource [*StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). La ressource StatefulSet contient un pod. Chaque pod contient :
  * Un conteneur SQL Server exécutant une instance SQL Server.
  * Un superviseur `mcr.microsoft.com/mssql/ha` pour gérer le groupe de disponibilité.

* Deux ressources [*ConfigMaps*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) liées au groupe de disponibilité. Les ressources ConfigMaps fournissent des informations concernant :
  * Le déploiement pour l’opérateur.
  * Groupe de disponibilité.

 * Les volumes persistants pour chaque instance de SQL Server fournissent le stockage pour les fichiers de données et les fichiers journaux.

En outre, le cluster stocke des [*secrets*](https://kubernetes.io/docs/concepts/configuration/secret/) pour les mots de passe, certificats, clés et autres informations sensibles.

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>Comparer la haute disponibilité SQL Server sur des conteneurs avec et sans le groupe de disponibilité

Le tableau suivant compare la fonctionnalité de haute disponibilité SQL Server dans des conteneurs sur Kubernetes, avec et sans groupe de disponibilité :

| |Avec un groupe de disponibilité | Instance de conteneur autonome<br/> Pas de groupe de disponibilité
|:------|:------|:------
|Récupérer automatiquement à partir d’une défaillance de nœud | Oui | Oui
|Récupérer automatiquement à partir d’une défaillance de pod | Oui | Oui
|Basculement plus rapide |Oui |
|Récupération automatique suite à l’échec d’une instance SQL Server | Oui | 
|Récupération automatique à partir d’un échec de contrôle d’intégrité de la base de données | Oui | 
|Fournir des réplicas en lecture seule | Oui |
|Sauvegarde de réplica secondaire | Oui | 
|S’exécute en tant que StatefulSet | Oui | 

L’une des principales différences réside dans le fait que le temps de récupération (ou de basculement) est plus rapide avec un groupe de disponibilité qu’avec une seule instance de SQL Server dans un conteneur. Cette amélioration est due au fait que le groupe de disponibilité SQL Server conserve les réplicas secondaires sur d’autres nœuds du cluster. Lors du basculement, un réplica secondaire est sélectionné et promu serveur principal. Les applications connectées au service sont redirigées vers le nouveau réplica principal.

Sans le groupe de disponibilité, lorsque Kubernetes détecte un basculement, il doit créer le conteneur, le connecter au stockage, puis les applications connectées au service sont reconnectées. Le temps de basculement exact dépend de l’emplacement du basculement et de la façon dont il a été détecté. 

En règle générale, le temps de basculement d’un groupe de disponibilité est mesuré en secondes, tandis que le temps de basculement d’une instance unique pour récupérer un conteneur peut atteindre 10 minutes.

## <a name="next-steps"></a>Étapes suivantes

Pour déployer des conteneurs SQL Server dans Azure Kubernetes service (AKS), consultez les exemples suivants :

* [Déployer SQL Server dans le conteneur Docker](sql-server-linux-configure-docker.md)
* [Déployer un conteneur SQL Server dans Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Groupes de disponibilité Always On pour les conteneurs SQL Server](sql-server-ag-kubernetes.md)

