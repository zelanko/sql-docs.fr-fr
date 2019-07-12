---
title: Haute disponibilité pour les conteneurs de SQL Server
description: Cet article présente une haute disponibilité pour les conteneurs de SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: da4c702e8ec5e8c1d645af616df53edd287eae5a
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833926"
---
# <a name="high-availability-for-sql-server-containers"></a>Haute disponibilité pour les conteneurs de SQL Server

Créez et gérez vos instances de SQL Server en mode natif dans Kubernetes.

Déployer SQL Server sur des conteneurs docker gérés par [Kubernetes](https://kubernetes.io/). Dans Kubernetes, un conteneur avec une instance de SQL Server peut récupérer automatiquement en cas d’échec d’un nœud de cluster. Pour une disponibilité plus robuste, configurer le groupe de disponibilité SQL Server Always On avec des instances de SQL Server dans des conteneurs sur un cluster Kubernetes. Cet article compare les deux solutions.

## <a name="compare-sql-server-versions-on-kubernetes"></a>Comparer les versions de SQL Server sur Kubernetes

SQL Server 2017 fournit une image Docker que vous pouvez déployer sur Kubernetes. Vous pouvez configurer l’image avec une revendication de volume persistant Kubernetes (PVC). Kubernetes surveille le processus de SQL Server dans le conteneur. Si le processus, un pod, conteneur ou nœud en panne, Kubernetes automatiquement amorce une autre instance et qu’il se reconnecte au stockage.

SQL Server 2019 (préversion) introduit une architecture plus robuste avec un Kubernetes StatefulSet. Kubernetes orchestre les instances de SQL Server dans des images de conteneur qui participent à un SQL Server groupe de disponibilité AlwaysOn. Ce modèle fournit améliorée sur l’intégrité, plus rapide, déchargement de la sauvegarde et la récupération lecture montée en charge.  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Conteneur avec l’instance de SQL Server sur Kubernetes

Kubernetes 1.6 et versions ultérieures prend en charge [ *classes de stockage*](https://kubernetes.io/docs/concepts/storage/storage-classes/), [ *les revendications de volume persistant*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)et le [  *Type de volume de disque Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

Dans cette configuration, Kubernetes joue le rôle de l’orchestrateur de conteneurs. 

![Diagramme du cluster Kubernetes SQL Server](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Dans le diagramme précédent, `mssql-server` est une instance de SQL Server (conteneur) dans un [ *pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Un [jeu de réplicas](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) garantit que le pod est automatiquement récupéré après une défaillance de nœud. Applications se connectent au service. Dans ce cas, le service représente un équilibreur de charge qui héberge une adresse IP qui reste la même après l’échec de la `mssql-server`.

Kubernetes orchestre les ressources du cluster. En cas d’échec d’un nœud qui héberge un conteneur d’instance de SQL Server, il démarre un nouveau conteneur avec une instance de SQL Server et l’attache au même stockage persistant.

SQL Server 2017 et versions ultérieures en charge les conteneurs sur Kubernetes.

Pour créer un conteneur dans Kubernetes, consultez [déployer un conteneur de SQL Server dans Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Un groupe de disponibilité SQL Server Always On sur les conteneurs de SQL Server dans Kubernetes

SQL Server 2019 prend en charge les groupes de disponibilité sur des conteneurs dans un Kubernetes. Pour les groupes de disponibilité, déployez le serveur SQL Server [Kubernetes opérateur](https://coreos.com/blog/introducing-operators.html) à votre cluster Kubernetes. L’opérateur facilite l’empaquetage, déployer et gérer des instances de SQL Server et le groupe de disponibilité dans un cluster.

![Groupe de disponibilité dans le conteneur de Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

Dans l’image ci-dessus, un cluster de quatre nœuds kubernetes héberge un groupe de disponibilité avec trois réplicas. La solution inclut les composants suivants :

* Un Kubernetes [ *déploiement*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Le déploiement inclut l’opérateur et une carte de configuration. Le déploiement décrit l’image de conteneur, les logiciels et les instructions nécessaires pour déployer des instances de SQL Server pour le groupe de disponibilité.

* Trois nœuds, chacune hébergeant un [ *StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). La ressource StatefulSet contient un pod. Chaque pod contient :
  * Un conteneur de SQL Server qui exécute une instance de SQL Server.
  * Un superviseur `mcr.microsoft.com/mssql/ha` pour gérer le groupe de disponibilité.

* Deux [ *ConfigMaps* ](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) associées au groupe de disponibilité. Les ConfigMaps fournissent des informations sur :
  * Le déploiement de l’opérateur.
  * Groupe de disponibilité.

 * Volumes persistants pour chaque instance de SQL Server fournissent le stockage pour les données et fichiers journaux.

En outre, le cluster stocke [ *secrets* ](https://kubernetes.io/docs/concepts/configuration/secret/) pour les mots de passe, les certificats, les clés et les autres informations sensibles.

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>Comparer la haute disponibilité de SQL Server sur les conteneurs avec et sans le groupe de disponibilité

Le tableau suivant compare la fonctionnalité de haute disponibilité de SQL Server dans des conteneurs sur Kubernetes avec et sans un groupe de disponibilité :

| |Avec un groupe de disponibilité | Instance de conteneur autonome<br/> Aucun groupe de disponibilité
|:------|:------|:------
|Récupérer automatiquement à partir de la défaillance de nœud | Oui | Oui
|Automatiquement récupérer après une panne de pod | Oui | Oui
|Basculement plus rapide |Oui |
|Récupérer automatiquement à partir de la défaillance d’instance de SQL Server | Oui | 
|Récupérer automatiquement à partir de l’échec de vérification d’intégrité de base de données | Oui | 
|Fournir des réplicas en lecture seule | Oui |
|Sauvegarde du réplica secondaire | Oui | 
|S’exécute comme une ressource StatefulSet | Oui | 

Une différence essentielle est que le temps de récupération (ou le basculement) est plus rapide avec un groupe de disponibilité qu’avec une seule instance de SQL Server dans un conteneur. Cette amélioration est car le groupe de disponibilité de SQL Server conserve les réplicas secondaires sur d’autres nœuds du cluster. Lors du basculement, un réplica secondaire est sélectionné et promu vers le site principal. Les applications connectées au service sont redirigées vers le nouveau réplica principal.

Sans le groupe de disponibilité, lorsque Kubernetes détecte un basculement, il a besoin créer le conteneur, de se connecter au stockage, et ensuite les applications connectées au service sont reconnectées. Le temps de basculement exacte dépend où le basculement a été, et comment il a été détecté. 

En règle générale, le temps de basculement pour un groupe de disponibilité est exprimé en secondes, tandis que le temps de basculement pour une seule instance récupérer un conteneur peut être jusqu'à 10 minutes.

## <a name="next-steps"></a>Étapes suivantes

Pour déployer des conteneurs de SQL Server dans Azure Kubernetes Service (ACS), consultez ces exemples :

* [Déployer SQL Server dans le conteneur Docker](sql-server-linux-configure-docker.md)
* [Déployer un conteneur de SQL Server dans Kubernetes](tutorial-sql-server-containers-kubernetes.md)
* [Groupes de disponibilité Always On pour les conteneurs de SQL Server](sql-server-ag-kubernetes.md)

