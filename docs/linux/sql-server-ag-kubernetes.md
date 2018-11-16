---
title: Groupes de disponibilité Always On pour les conteneurs de SQL Server
description: Cet article présente les groupes de disponibilité sur les conteneurs de SQL Server
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c74b39f4b7816221e2258bde2b1fef2b9e74d9d3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51658571"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>Groupes de disponibilité Always On pour les conteneurs de SQL Server

SQL Server 2019 prend en charge les groupes de disponibilité sur des conteneurs dans un Kubernetes. Pour les groupes de disponibilité, déployez le serveur SQL Server [Kubernetes opérateur](https://coreos.com/blog/introducing-operators.html) à votre cluster Kubernetes. L’opérateur facilite l’empaquetage, déployer et gérer le groupe de disponibilité dans un cluster.

![Groupe de disponibilité dans le conteneur de Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

Dans l’image ci-dessus, un cluster de quatre nœuds kubernetes héberge un groupe de disponibilité avec trois réplicas. La solution inclut les composants suivants :

* Un Kubernetes [ *déploiement*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). Le déploiement inclut l’opérateur et une carte de configuration. Ils fournissent l’image de conteneur, les logiciels et les instructions nécessaires pour déployer des instances de SQL Server pour le groupe de disponibilité.

* Trois nœuds, chacune hébergeant un [ *StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). La ressource StatefulSet contient un [ *pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/). Chaque pod contient :
  * Un conteneur de SQL Server qui exécute une instance de SQL Server.
  * Un agent de groupe de disponibilité. 

* Deux [ *ConfigMaps* ](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) associées au groupe de disponibilité. Les ConfigMaps fournissent des informations sur :
  * Le déploiement de l’opérateur.
  * Groupe de disponibilité.

 * [*Volumes persistants* ](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) sont des éléments de stockage. Un *revendication de volume persistant* (PVC) est une demande de stockage par un utilisateur. Chaque conteneur est affilié à un PVC pour le stockage de données et de journaux. Dans Azure Kubernetes Service (ACS), vous [créer une revendication de volume persistant](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) pour attribuer automatiquement le stockage basé sur une classe de stockage.


En outre, le cluster stocke [ *secrets* ](https://kubernetes.io/docs/concepts/configuration/secret/) pour les mots de passe, les certificats, les clés et les autres informations sensibles.

## <a name="deploy-the-availability-group-in-kubernetes"></a>Déployer le groupe de disponibilité dans Kubernetes

Pour déployer un groupe de disponibilité dans Kubernetes :

1. Création du cluster Kubernetes

   Pour un groupe de disponibilité, créez au moins trois nœuds SQL Server plus un nœud pour le masque.

1. Déployer l’opérateur

1. Configurer le stockage

1. Déployer la ressource StatefulSet

   L’opérateur est à l’écoute pour obtenir des instructions déployer la ressource StatefulSet. Automatiquement, il crée les instances de SQL Server sur trois nœuds distincts et configure le groupe de disponibilité avec un gestionnaire de cluster externe.

1. Créer les bases de données et les joindre au groupe de disponibilité

Pour des instructions détaillées, consultez [groupes de disponibilité Always On pour les conteneurs de SQL Server](sql-server-ag-kubernetes.md).

## <a name="sql-server-kubernetes-operator"></a>Opérateur de SQL Server Kubernetes

Après avoir déployé l’opérateur, il enregistre une ressource personnalisée de SQL Server. Utiliser l’opérateur pour déployer cette ressource.  Chaque ressource correspond à une instance de SQL Server et inclut des propriétés spécifiques comme `sapassword` et `monitoring policy`. L’opérateur d’analyse de la ressource et déploie un Kubernetes StatefulSet.

Le StatfulSet contient :

* conteneur MSSQL-server

* conteneur de MSSQL-ha-superviseur

Le code de l’opérateur, superviseur de haute disponibilité et SQL Server est empaqueté dans une image Docker appelée `mcr.microsoft.com/mssql/ha`. Cette image contient les fichiers binaires suivants :

* `mssql-operator`

    Ce processus est déployé comme un déploiement Kubernetes séparé. Il enregistre le [ressource personnalisée Kubernetes](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) appelé `SqlServer` (sqlservers.mssql.microsoft.com). Puis il écoute pour ces ressources est créé ou mis à jour dans le cluster Kubernetes. Pour chaque événement de ce type, il crée ou met à jour les ressources Kubernetes pour l’instance correspondante (par exemple la ressource StatefulSet, ou `mssql-server-k8s-init-sql` travail).

* `mssql-server-k8s-health-agent`

    Ce serveur web sert Kubernetes [sondes de l’activité](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) pour déterminer l’intégrité d’une instance de SQL Server. Analyse l’intégrité de l’instance de SQL Server locale en appelant `sp_server_diagnostics` et en comparant les résultats avec votre stratégie d’analyse.

* `mssql-ha-supervisor`

   Conserve le certificat de groupe de disponibilité et d’un point de terminaison. 

* `mssql-server-k8s-ag-agent`
  
    Ce processus analyse l’intégrité d’un réplica de groupe de disponibilité sur une seule instance de SQL Server et effectue des basculements.

    Il gère également l’élection du responsable.

* `mssql-server-k8s-init-sql`
  
    Cette Kubernetes [travail](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) s’applique une configuration d’état souhaité pour une instance de SQL Server. Le travail est créé par l’opérateur chaque fois qu’une ressource SQL Server est créée ou mis à jour. Elle garantit que l’instance de SQL Server cible correspondant à la ressource personnalisée a la configuration souhaitée décrite dans la ressource.

    Par exemple, si les paramètres suivants sont requis, il effectue les :
  * Mettre à jour le mot de passe SA
  * Crée la connexion SQL pour les agents
  * Crée le point de terminaison DBM

* `mssql-server-k8s-rotate-creds`
  
    Ce travail Kubernetes implémente la tâche d’informations d’identification de rotation. Créez cette tâche pour demander des mises à jour le mot de passe SA, du mot de passe de connexion de l’agent SQL, de l’entrepôt DBM cert, etc. Le mot de passe SA est spécifié en tant que les paramètres du travail. Les autres sont générés automatiquement.

* `mssql-server-k8s-failover`

   Un travail de Kubernetes qui implémente le flux de travail de basculement manuel.

### <a name="notes"></a>Remarques

Quelle que soit la configuration du groupe de disponibilité, l’opérateur déploiera le superviseur de haute disponibilité. Si la ressource SQL Server ne répertorie pas n’importe quel groupe de disponibilité, l’opérateur déploiera toujours ce conteneur.

La version de l’image de l’opérateur est identique à la version de l’image de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

> [Conteneur de SQL Server dans Kubernetes](tutorial-sql-server-containers-kubernetes.md)
