---
title: Configurer Azure Kubernetes Service
titleSuffix: SQL Server big data clusters
description: Découvrez comment configurer Azure Kubernetes Service (AKS) pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: b70b5672bff38c8c82dd9bfd837e267328bf6aa9
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860160"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-big-data-cluster-deployments"></a>Configurer Azure Kubernetes Service pour les déploiements de cluster SQL Server big data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment configurer Azure Kubernetes Service (AKS) pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data.

AKS permet de facilement créer, configurer et gérer un cluster de machines virtuelles qui sont préconfigurées avec un cluster Kubernetes pour exécuter des applications en conteneur. Cela vous permet d’utiliser vos compétences existantes ou de faire appel à une importante et croissante de la Communauté d’experts, pour déployer et gérer des applications en conteneur sur Microsoft Azure.

Cet article décrit les étapes pour déployer Kubernetes sur AKS à l’aide d’Azure CLI. Si vous n’avez pas un abonnement Azure, créez un compte gratuit avant de commencer.

> [!TIP] 
> Pour un exemple de script python qui déploie le cluster de données volumineux AKS et SQL Server, consultez [Guide de démarrage rapide : Déployer SQL Server sur Azure Kubernetes Service (ACS) de cluster de données volumineuses](quickstart-big-data-cluster-deploy.md).

## <a name="prerequisites"></a>Prérequis

- [Déployer les outils de données volumineuses de SQL Server 2019](deploy-big-data-tools.md):
   - **Kubectl**
   - **Azure Data Studio**
   - **Extension de SQL Server 2019**
   - **Azure CLI**

- Version minimum 1.10 pour serveur de Kubernetes. Pour AKS, vous devez utiliser `--kubernetes-version` paramètre pour spécifier une version différente de la valeur par défaut.

- Pour une expérience optimale lors de la validation des scénarios de base sur AKS, utilisez :
   - 8 processeurs virtuels sur tous les nœuds
   - 32 Go de mémoire par machine virtuelle
   - 24 ou plus attachés les disques sur tous les nœuds

   > [!TIP]
   > Infrastructure Azure offre plusieurs options de taille pour les machines virtuelles, consultez [ici](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) pour les sélections dans la région que vous voulez déployer.

## <a name="create-a-resource-group"></a>Créer un groupe de ressources

Un groupe de ressources Azure est un groupe logique dans Azure les ressources sont déployées et gérées. Les étapes suivantes vous connecter à Azure et créer un groupe de ressources pour le cluster AKS.

1. À l’invite de commandes, exécutez la commande suivante et suivez les invites pour vous connecter à votre abonnement Azure :

    ```azurecli
    az login
    ```

1. Si vous avez plusieurs abonnements, vous pouvez afficher tous vos abonnements en exécutant la commande suivante :

   ```azurecli
   az account list
   ```

1. Si vous souhaitez remplacer par un autre abonnement, vous pouvez exécuter cette commande :

   ```azurecli
   az account set --subscription <subscription id>
   ```

1. Créer un groupe de ressources avec le **az groupe créer** commande. L’exemple suivant crée un groupe de ressources nommé `sqlbigdatagroup` dans le `westus2` emplacement.

   ```azurecli
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Créer un cluster Kubernetes

1. Créer un cluster Kubernetes dans ACS avec la [créer az aks](https://docs.microsoft.com/cli/azure/aks) commande. L’exemple suivant crée un cluster Kubernetes nommé *kubcluster* avec un nœud de l’agent Linux de taille **Standard_L8s**. Vérifiez que vous créez le cluster AKS dans le même groupe de ressources que vous avez utilisé dans les sections précédentes.

    ```azurecli
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_L8s \
    --node-count 1 \
    --kubernetes-version 1.10.9
    ```

   Vous pouvez augmenter ou diminuer le nombre de nœuds d’agent Kubernetes en modifiant le `--node-count <n>` où `<n>` est le nombre de nœuds d’agent à utiliser. Cela n’inclut pas le nœud principal Kubernetes, qui est géré en arrière-plan par AKS. L’exemple précédent utilise uniquement un seul nœud à des fins d’évaluation.

   Après quelques minutes, la commande se termine et retourne des informations formatées JSON sur le cluster.

1. Enregistrer la sortie JSON à partir de la commande précédente pour une utilisation ultérieure.

## <a name="connect-to-the-cluster"></a>Connectez-vous au cluster

1. Pour configurer kubectl pour vous connecter à votre cluster Kubernetes, exécutez le [az aks get-credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) commande. Cette étape télécharge les informations d’identification et configure l’interface CLI pour les utiliser kubectl.

   ```azurecli
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Pour vérifier la connexion à votre cluster, utilisez le [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) commande pour retourner une liste des nœuds du cluster.  L’exemple ci-dessous montre la sortie si vous deviez avoir 1 master et 3 nœuds de l’agent.

   ```
   kubectl get nodes
   ```

## <a name="next-steps"></a>Étapes suivantes

Les étapes décrites dans cet article configuré un cluster Kubernetes dans ACS. L’étape suivante consiste à déployer SQL Server 2019 des données volumineuses vers le cluster. Pour plus d’informations sur la façon de déployer des clusters de données volumineuses, consultez l’article suivant :

[Comment déployer des clusters de données volumineuses de SQL Server sur Kubernetes](deployment-guidance.md)
