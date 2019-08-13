---
title: Groupes de disponibilité Always On pour les conteneurs exécutant Linux
titleSuffix: SQL Server
description: Cet article présente les groupes de disponibilité sur les conteneurs SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3910c74be803b7fc63c8bf560fc637387e06ee15
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67910470"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>Groupes de disponibilité Always On pour les conteneurs SQL Server

SQL Server 2019 prend en charge les groupes de disponibilité sur les conteneurs dans un cluster Kubernetes. Pour les groupes de disponibilité, déployez l'[opérateur Kubernetes](https://coreos.com/blog/introducing-operators.html) SQL Server sur votre cluster Kubernetes. L'opérateur aide à regrouper, déployer et gérer le groupe de disponibilité dans un cluster.

![Groupe de disponibilité dans un conteneur Kubernetes](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

Dans l'image ci-dessus, un cluster Kubernetes à quatre nœuds héberge un groupe de disponibilité avec trois réplicas. La solution inclut les composants suivants :

* Un [*déploiement*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) Kubernetes. Le déploiement comprend l'opérateur et une table de configuration. Ces éléments fournissent l'image du conteneur, le logiciel et les instructions nécessaires au déploiement des instances SQL Server pour le groupe de disponibilité.

* Trois nœuds, chacun hébergeant une ressource [*StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). La ressource StatefulSet contient un [*pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/). Chaque pod contient :
  * Un conteneur SQL Server exécutant une instance SQL Server.
  * Un agent de groupe de disponibilité. 

* Deux ressources [*ConfigMaps*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/) liées au groupe de disponibilité. Les ressources ConfigMaps fournissent des informations concernant :
  * Le déploiement pour l’opérateur.
  * Groupe de disponibilité.

 * [*Les volumes persistants*](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) sont des éléments de stockage. Une *revendication de volume persistante* (PVC) est une requête de stockage effectuée par un utilisateur. Chaque conteneur est associé à une PVC pour le stockage des données et des journaux. Dans Azure Kubernetes Service (AKS), vous [créez une revendication de volume persistant](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) pour provisionner automatiquement le stockage basé sur une classe de stockage.


En outre, le cluster stocke des [*secrets*](https://kubernetes.io/docs/concepts/configuration/secret/) pour les mots de passe, certificats, clés et autres informations sensibles.

## <a name="deploy-the-availability-group-in-kubernetes"></a>Déployer le groupe de disponibilité dans Kubernetes

Pour déployer un groupe de disponibilité dans Kubernetes :

1. Créer le cluster Kubernetes

   Pour un groupe de disponibilités, créez au moins trois nœuds pour SQL Server plus un nœud pour le maître.

1. Déployer l’opérateur

1. Configurer le stockage

1. Déployer la ressource StatefulSet

   L'opérateur écoute les instructions pour déployer la ressource StatefulSet. Il crée automatiquement les instances SQL Server sur trois nœuds séparés et configure le groupe de disponibilité avec un gestionnaire de cluster externe.

1. Créer les bases de données et les joindre au groupe de disponibilité

Pour obtenir des étapes détaillées, consultez [Groupes de disponibilité Always On pour conteneurs SQL Server](sql-server-ag-kubernetes.md).

## <a name="sql-server-kubernetes-operator"></a>Opérateur Kubernetes SQL Server

Une fois déployé, l'opérateur enregistre une ressource SQL Server personnalisée. Utilisez l'opérateur pour déployer cette ressource.  Chaque ressource correspond à une instance SQL Server et inclut des propriétés spécifiques comme `sapassword` et `monitoring policy`. L'opérateur analyse la ressource et déploie une ressource StatefulSet Kubernetes.

La ressource StatfulSet contient les éléments suivants :

* un conteneur mssql-server

* un conteneur mssql-ha-supervisor

Le code pour l’opérateur, le superviseur HA et SQL Server est empaqueté dans une image Docker appelée `mcr.microsoft.com/mssql/ha`. Cette image contient les binaires suivants :

* `mssql-operator`

    Ce processus est déployé comme un déploiement Kubernetes distinct. Il enregistre la [ressource Kubernetes personnalisée](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) appelée `SqlServer` (sqlservers.mssql.microsoft.com). Ensuite, il écoute les ressources créées ou mises à jour dans le cluster Kubernetes. Pour chaque événement de ce type, il crée ou met à jour les ressources Kubernetes pour l'instance correspondante (par exemple la ressource StatefulSet, ou le travail `mssql-server-k8s-init-sql`).

* `mssql-server-k8s-health-agent`

    Ce serveur web permet aux [sondes d’activité](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) Kubernetes de déterminer l'intégrité d'une instance SQL Server. Surveille l’intégrité de l'instance SQL Server locale en appelant `sp_server_diagnostics` et en comparant les résultats avec votre stratégie de surveillance.

* `mssql-ha-supervisor`

   Maintient le certificat du groupe de disponibilité et le point de terminaison. 

* `mssql-server-k8s-ag-agent`
  
    Ce processus surveille l’intégrité d’un réplica de groupe de disponibilité sur une seule instance SQL Server et effectue des basculements.

    Il maintient également l'élection du leader.

* `mssql-server-k8s-init-sql`
  
    Ce [travail](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) Kubernetes applique une configuration d'état souhaitée à une instance SQL Server. Le travail est créé par l'opérateur chaque fois qu'une ressource SqlServer est créée ou mise à jour. Il s'assure que l'instance SQL Server cible correspondant à la ressource personnalisée possède la configuration souhaitée décrite dans la ressource.

    Par exemple, si l'un des paramètres suivants est requis, il le complète :
  * Mettre à jour le mot de passe AS
  * Crée la connexion SQL pour les agents
  * Crée le point de terminaison DBM

* `mssql-server-k8s-rotate-creds`
  
    Ce travail Kubernetes implémente la tâche de rotation des informations d'identification. Créez ce travail pour demander des mises à jour du mot de passe AS, du mot de passe de connexion de l’agent SQL, du certificat DBM, etc. Le mot de passe AS est spécifié comme paramètres du travail. Les autres paramètres sont automatiquement générés.

* `mssql-server-k8s-failover`

   Un travail Kubernetes qui implémente le workflow de basculement manuel.

### <a name="notes"></a>Remarques

Quelle que soit la configuration du groupe de disponibilité, l'opérateur déploie toujours le superviseur HA. Si la ressource SqlServer ne contient aucun groupe de disponibilité, l'opérateur déploie quand même ce conteneur.

La version pour l'image de l'opérateur est identique à la version pour l'image SQL Server.

## <a name="next-steps"></a>Étapes suivantes

> [Conteneur SQL Server dans Kubernetes](tutorial-sql-server-containers-kubernetes.md)
