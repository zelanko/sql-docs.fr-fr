---
title: Prise en main
titleSuffix: SQL Server big data clusters
description: Découvrez les étapes et les ressources pour le déploiement des clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8583610606e5d554f039a69688af3ddff8dc8bb3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958532"
---
# <a name="get-started-with-sql-server-big-data-clusters"></a>Bien démarrer avec les clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit une vue d’ensemble de la façon de déployer un [cluster de données volumineux de SQL Server 2019 (version préliminaire)](big-data-cluster-overview.md). Il est destiné à vous orienter vers les concepts et de fournir une infrastructure permettant de comprendre les autres articles sur les déploiement dans cette section. Vos étapes de déploiement spécifiques varient en fonction de vos choix de la plateforme pour le client et le serveur.

## <a id="tools"></a> outils clients

Les clusters de données volumineuses nécessitent un ensemble spécifique d’outils clients. Avant de déployer un cluster de données volumineux sur Kubernetes, vous devez installer les outils suivants :

| Tool | Description |
|---|---|
| **mssqlctl** | Déploie et gère les clusters de données volumineuses. |
| **kubectl** | Crée et gère le cluster Kubernetes sous-jacente. |
| **Azure Data Studio** | Interface graphique pour l’utilisation du cluster de données volumineuses. |
| **Extension de SQL Server 2019** | Extension Data Studio Azure qui active les fonctionnalités de cluster de données volumineuses. |

Autres outils sont nécessaires pour différents scénarios. Chaque article doit expliquer les outils requis pour effectuer une tâche spécifique. Pour obtenir une liste complète des outils et des liens d’installation, consultez [outils de big data d’installer SQL Server 2019](deploy-big-data-tools.md).

## <a name="kubernetes"></a>kubernetes

Les clusters de données volumineuses sont déployés comme une série de conteneurs reliés entre eux qui sont gérés dans [Kubernetes](https://kubernetes.io/docs/home). Vous pouvez héberger Kubernetes de plusieurs façons. Même si vous disposez déjà d’un environnement Kubernetes existant, vous devez examiner les spécifications connexes pour les clusters de données volumineuses.

- **Azure Kubernetes Service (AKS)** : AKS permet de déployer un cluster Kubernetes géré dans Azure. Vous uniquement gérez et tenir à jour les nœuds d’agent. Avec AKS, vous n’êtes pas obligé de configurer votre propre matériel pour le cluster. Il est également facile d’utiliser un cluster de données volumineux [script de déploiement](quickstart-big-data-cluster-deploy.md) pour créer le cluster AKS et de déployer le cluster de données volumineux en une seule étape. Pour plus d’informations sur l’utilisation d’ACS avec les clusters de données volumineuses, consultez [configurer le Service Azure Kubernetes pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data](deploy-on-aks.md).

- **Plusieurs machines**: Vous pouvez également déployer Kubernetes sur plusieurs machines Linux, ce qui pourrait être des serveurs physiques ou virtuels. Le [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) outil peut être utilisé pour créer le cluster Kubernetes. Cette méthode fonctionne bien si vous disposez déjà d’une infrastructure existante que vous souhaitez utiliser pour votre cluster big data. Pour plus d’informations sur l’utilisation de **kubeadm** déploiements avec les clusters de données volumineuses, consultez [Kubernetes de configuration sur plusieurs ordinateurs pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data](deploy-with-kubeadm.md).

- **Minikube**: Minikube vous autorise à exécuter Kubernetes localement sur un seul serveur. Il est une bonne option si vous testez des clusters de données volumineuses ou que vous devrez l’utiliser dans un scénario de test ou de développement. Pour plus d’informations sur l’utilisation de Minikube, consultez le [Minikube documentation](https://kubernetes.io/docs/setup/minikube/). Pour connaître les exigences spécifiques pour l’utilisation de Minikube avec les clusters de données volumineuses, consultez [configurer minikube pour les déploiements de cluster SQL Server 2019 big data](deploy-on-minikube.md).

## <a name="deploy-a-big-data-cluster"></a>Déployer un cluster Big Data

Après avoir configuré Kubernetes, vous déployez un cluster de données volumineuses avec la `mssqlctl bdc create` commande. Lors du déploiement, vous pouvez tirer plusieurs approches différentes.

- Si vous déployez dans un environnement de développement et de test, vous pouvez choisir d’utiliser une de la [configurations par défaut](deployment-guidance.md#deploy) fourni par **mssqlctl**.

- Pour personnaliser votre déploiement, vous pouvez créer et utiliser votre propre [les fichiers de configuration de déploiement](deployment-guidance.md#configfile).

- Pour une installation entièrement sans assistance, vous pouvez transmettre tous les autres paramètres dans les variables d’environnement. Pour plus d’informations, consultez [des déploiements sans assistance](deployment-guidance.md#unattended).

## <a name="deployment-scripts"></a>Scripts de déploiement

Scripts de déploiement peuvent aider à déployer Kubernetes et les clusters de données volumineuses en une seule étape. Ils fournissent également souvent des valeurs par défaut pour les paramètres de cluster de données volumineuses. Pour obtenir un exemple d’un script de déploiement pour le cluster de données volumineux sur Azure Kubernetes Service (AKS), consultez l’article suivant :

[Déployer un 2019 de serveur SQL du cluster big data avec un script de déploiement (AKS)](quickstart-big-data-cluster-deploy.md).

Vous pouvez personnaliser n’importe quel script de déploiement en créant votre propre version qui configure les variables d’environnement de cluster big data différemment.

## <a name="next-steps"></a>Étapes suivantes

Après avoir déployé avec succès un cluster de données volumineux, [se connecter au cluster](connect-to-big-data-cluster.md) et envisagez [le chargement des données d’exemple](tutorial-load-sample-data.md) pour une utilisation avec plusieurs procédures pas à pas.