---
title: Prise en main
titleSuffix: SQL Server big data clusters
description: Découvrez les étapes et les ressources pour le [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] déploiement (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 323394f9590551528ce9e9dfdf1fb97c7d1c2225
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653390"
---
# <a name="get-started-with-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Prise en main de[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit une vue d’ensemble de la [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md)procédure de déploiement de. Il explique les différents concepts qui sont liés à un tel déploiement et fournit un cadre permettant de comprendre les autres articles de déploiement de cette section. Les étapes de déploiement varient selon la plateforme choisie pour le client et le serveur.

> [!TIP]
> Pour obtenir rapidement un environnement avec Kubernetes et Big Data cluster déployé pour vous aider à améliorer ses capacités, utilisez l’un des exemples de scripts pointés dans [la section scripts](#scripts). Après le déploiement, pour gérer le cluster, utilisez les [outils clients](#tools) de la section suivante.

## <a id="tools"></a> Outils clients

Les clusters Big Data nécessitent un ensemble spécifique d’outils clients. Avant de déployer un cluster Big Data sur Kubernetes, vous devez installer les outils suivants :

| Tool | Description |
|---|---|
| **azdata** | Déploie et gère des clusters Big Data. |
| **kubectl** | Crée et gère le cluster Kubernetes sous-jacent. |
| **Azure Data Studio** | Interface graphique pour l’utilisation du cluster Big Data. |
| **Extension SQL Server 2019** | Extension Azure Data Studio qui permet d’utiliser les fonctionnalités des clusters Big Data. |

D’autres outils sont nécessaires pour divers scénarios. Chaque article doit expliquer les outils prérequis permettant d’effectuer différentes tâches. Pour obtenir la liste complète des outils et des liens d’installation, consultez [Installer les outils de Big Data SQL Server 2019](deploy-big-data-tools.md).

## <a name="kubernetes"></a>Kubernetes

Les clusters Big Data sont déployés sous la forme d’une série de conteneurs interdépendants qui sont gérés dans [Kubernetes](https://kubernetes.io/docs/home). Vous pouvez héberger Kubernetes de différentes façons. Même si vous disposez déjà d’un environnement Kubernetes, vous devez passer en revue les conditions requises relatives aux clusters Big Data.

- **Azure Kubernetes Service (AKS)**  : AKS vous permet de déployer un cluster Kubernetes géré dans Azure. Vous gérez uniquement les nœuds de l’agent. Avec AKS, vous n’avez pas besoin de provisionner votre matériel pour le cluster. Il est aussi facile d’utiliser un [script Python](quickstart-big-data-cluster-deploy.md) ou un [notebook de déploiement](deploy-notebooks.md) pour créer le cluster AKS et déployer le cluster Big Data en une seule étape. Pour plus d’informations sur la configuration de AKS pour un déploiement de cluster Big Data, consultez [configurer le [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] service Azure Kubernetes pour les déploiements](deploy-on-aks.md).

- **Plusieurs machines** : Vous pouvez également déployer Kubernetes sur plusieurs machines Linux, qui peuvent être des serveurs physiques ou des machines virtuelles. L’outil [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) peut être utilisé pour créer le cluster Kubernetes. Vous pouvez utiliser un [script bash](deployment-script-single-node-kubeadm.md) pour automatiser ce type de déploiement. Cette méthode fonctionne bien si vous disposez déjà d’une infrastructure existante que vous souhaitez utiliser pour votre cluster Big Data. Pour plus d’informations sur l’utilisation de déploiements **kubeadm** avec des clusters Big Data, consultez [configurer Kubernetes [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] sur plusieurs machines pour les déploiements](deploy-with-kubeadm.md).

- **Minikube** : Minikube vous permet d’exécuter Kubernetes localement sur un seul serveur. Cette option convient si vous souhaitez tester les clusters Big Data, ou si vous devez l’utiliser dans un scénario de test ou de développement. Pour plus d’informations sur l’utilisation de Minikube, consultez la [documentation Minikube](https://kubernetes.io/docs/setup/minikube/). Pour connaître la configuration nécessaire à l’utilisation de Minikube avec des clusters Big Data, consultez [Configurer Minikube pour les déploiements de clusters Big Data SQL Server 2019](deploy-on-minikube.md).

## <a name="deploy-a-big-data-cluster"></a>Déployer un cluster Big Data

Après avoir configuré Kubernetes, vous devez déployer un cluster Big Data à l’aide de la commande `azdata bdc create`. Lors du déploiement, plusieurs méthodes sont possibles.

- Si vous effectuez un déploiement sur un environnement Dev/Test, vous pouvez choisir d’utiliser l’une des [configurations par défaut](deployment-guidance.md#deploy) fournies par **azdata**.

- Pour personnaliser votre déploiement, vous pouvez créer et utiliser vos propres [fichiers de configuration de déploiement](deployment-guidance.md#configfile).

- Pour une installation totalement sans assistance, vous pouvez passer tous les autres paramètres dans des variables d’environnement. Pour plus d’informations, consultez [Déploiements sans assistance](deployment-guidance.md#unattended).


## <a id="scripts"></a>Scripts de déploiement

Les scripts de déploiement vous permettent de déployer les clusters Kubernetes et Big Data en une seule étape. Ils fournissent également souvent des valeurs par défaut pour les paramètres des clusters Big Data. Vous pouvez personnaliser n’importe quel script de déploiement de cluster Big Data.

Les scripts de déploiement actuellement disponibles sont les suivants :

- [Script Python -- Déployer un cluster Big Data SQL Server sur AKS (Azure Kubernetes Service)](quickstart-big-data-cluster-deploy.md)
- [Script bash -- Déployer un cluster Big Data sur un cluster kubeadm à nœud unique](deployment-script-single-node-kubeadm.md)

## <a name="deployment-notebooks"></a>Notebooks de déploiement

Vous pouvez également déployer un cluster Big Data en exécutant un notebook Azure Data Studio. Pour plus d’informations sur l’utilisation d’un notebook pour un déploiement sur AKS, consultez l’article suivant :

- [Déployer un cluster Big Data avec des notebooks Azure Data Studio](deploy-notebooks.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez réussi à déployer un cluster Big Data, [connectez-vous au cluster](connect-to-big-data-cluster.md) en vue de [charger des exemples de données](tutorial-load-sample-data.md) à utiliser dans le cadre de différentes procédures pas à pas.
