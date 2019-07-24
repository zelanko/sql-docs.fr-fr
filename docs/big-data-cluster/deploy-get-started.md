---
title: Prise en main
titleSuffix: SQL Server big data clusters
description: Découvrez les étapes et les ressources pour le déploiement de clusters SQL Server 2019 Big Data (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 41dd39c7aa613083f8ff47824ed6238b6f3c61b9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419427"
---
# <a name="get-started-with-sql-server-big-data-clusters"></a>Prise en main des clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit une vue d’ensemble du déploiement d’un [cluster SQL Server 2019 Big Data (version préliminaire)](big-data-cluster-overview.md). Il est destiné à vous orienter vers les concepts et à fournir une infrastructure pour comprendre les autres articles sur le déploiement de cette section. Vos étapes de déploiement spécifiques varient en fonction de vos choix de plateforme pour le client et le serveur.

## <a id="tools"></a>Outils clients

Les clusters Big Data nécessitent un ensemble spécifique d’outils clients. Avant de déployer un cluster Big Data sur Kubernetes, vous devez installer les outils suivants:

| Tool | Description |
|---|---|
| **azdata** | Déploie et gère les clusters Big Data. |
| **kubectl** | Crée et gère le cluster Kubernetes sous-jacent. |
| **Azure Data Studio** | Interface graphique pour l’utilisation du cluster Big Data. |
| **SQL Server extension 2019** | Azure Data Studio extension qui active les fonctionnalités de cluster Big Data. |

D’autres outils sont requis pour différents scénarios. Chaque article doit expliquer les outils requis pour effectuer une tâche spécifique. Pour obtenir la liste complète des outils et des liens d’installation, consultez [installer SQL Server 2019 Big Data Tools](deploy-big-data-tools.md).

## <a name="kubernetes"></a>kubernetes

Les clusters Big Data sont déployés sous la forme d’une série de conteneurs interdépendants qui sont gérés dans [Kubernetes](https://kubernetes.io/docs/home). Vous pouvez héberger des Kubernetes de différentes manières. Même si vous disposez déjà d’un environnement Kubernetes, vous devez passer en revue les conditions requises pour Big Data les clusters.

- **Service Azure Kubernetes (AKS)** : AKS vous permet de déployer un cluster Kubernetes géré dans Azure. Vous gérez et gérez uniquement les nœuds de l’agent. Avec AKS, vous n’avez pas besoin d’approvisionner votre propre matériel pour le cluster. Il est également facile d’utiliser un script de [déploiement](quickstart-big-data-cluster-deploy.md) de cluster Big Data pour créer le cluster AKS et déployer le cluster Big Data en une seule étape. Pour plus d’informations sur l’utilisation de AKS avec des clusters Big Data, consultez [configurer le service Azure Kubernetes pour les déploiements de clusters SQL Server 2019 Big Data (version préliminaire)](deploy-on-aks.md).

- **Plusieurs ordinateurs**: Vous pouvez également déployer des Kubernetes sur plusieurs ordinateurs Linux, qui peuvent être des serveurs physiques ou des machines virtuelles. L’outil [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) peut être utilisé pour créer le cluster Kubernetes. Cette méthode fonctionne bien si vous disposez déjà d’une infrastructure existante que vous souhaitez utiliser pour votre cluster Big Data. Pour plus d’informations sur l’utilisation de déploiements **kubeadm** avec des clusters Big Data, consultez [configurer Kubernetes sur plusieurs machines pour les déploiements de SQL Server 2019 Big Data (version préliminaire)](deploy-with-kubeadm.md).

- **Minikube**: Minikube vous permet d’exécuter des Kubernetes localement sur un serveur unique. C’est une bonne option si vous essayez de Big Data des clusters ou si vous devez l’utiliser dans un scénario de test ou de développement. Pour plus d’informations sur l’utilisation de Minikube, consultez la [documentation de Minikube](https://kubernetes.io/docs/setup/minikube/). Pour connaître la configuration requise pour l’utilisation de Minikube avec des clusters Big Data, consultez [configurer Minikube pour SQL Server les déploiements de cluster 2019 Big Data](deploy-on-minikube.md).

## <a name="deploy-a-big-data-cluster"></a>Déployer un cluster Big Data

Après la configuration de Kubernetes, vous déployez un cluster Big Data `azdata bdc create` à l’aide de la commande. Lors du déploiement de, vous pouvez adopter plusieurs approches différentes.

- Si vous déployez dans un environnement de développement et de test, vous pouvez choisir d’utiliser l’une des [configurations par défaut](deployment-guidance.md#deploy) fournies par **azdata**.

- Pour personnaliser votre déploiement, vous pouvez créer et utiliser vos propres [fichiers de configuration de déploiement](deployment-guidance.md#configfile).

- Pour une installation totalement sans assistance, vous pouvez transmettre tous les autres paramètres dans les variables d’environnement. Pour plus d’informations, consultez [déploiements sans assistance](deployment-guidance.md#unattended).

## <a name="deployment-scripts"></a>Scripts de déploiement

Les scripts de déploiement peuvent vous aider à déployer à la fois les clusters Kubernetes et Big Data en une seule étape. Ils fournissent également souvent des valeurs par défaut pour les paramètres de cluster Big Data. Pour obtenir un exemple de script de déploiement pour Big Data cluster sur Azure Kubernetes service (AKS), consultez l’article suivant:

[Déployez un cluster SQL Server 2019 Big Data avec un script de déploiement (AKS)](quickstart-big-data-cluster-deploy.md).

Vous pouvez personnaliser n’importe quel script de déploiement en créant votre propre version qui configure les variables d’environnement de cluster Big Data différemment.

[Déployez un cluster SQL Server 2019 Big Data avec des blocs-notes Azure Data Studio](deploy-notebooks.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez réussi à déployer un cluster Big Data, [Connectez-vous au cluster](connect-to-big-data-cluster.md) et envisagez de [charger des exemples de données](tutorial-load-sample-data.md) à utiliser avec plusieurs procédures pas à pas.