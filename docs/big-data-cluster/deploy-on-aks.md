---
title: Configurer Azure Kubernetes Service pour les déploiements de cluster SQL Server 2019 big data | Microsoft Docs
description: Découvrez comment configurer Azure Kubernetes Service (AKS) pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/23/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: e3a73eab49c947d950981a9bdb41098ee00a9b9f
ms.sourcegitcommit: 12779bddd056a203d466d83c4a510a97348fe9d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216675"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-preview-deployments"></a>Configurer Azure Kubernetes Service pour les déploiements de SQL Server 2019 (version préliminaire)

Cet article décrit comment configurer Azure Kubernetes Service (AKS) pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data. 

AKS permet de facilement créer, configurer et gérer un cluster de machines virtuelles qui sont préconfigurées avec un cluster Kubernetes pour exécuter des applications en conteneur. Cela vous permet d’utiliser vos compétences existantes ou de faire appel à une importante et croissante de la Communauté d’experts, pour déployer et gérer des applications en conteneur sur Microsoft Azure.

Cet article décrit les étapes pour déployer Kubernetes sur AKS à l’aide d’Azure CLI. Si vous n’avez pas un abonnement Azure, créez un compte gratuit avant de commencer.

> [!TIP] 
> Pour un exemple de script python qui déploie le cluster de données volumineux AKS et SQL Server, consultez [déployer un serveur SQL Server sur Azure Kubernetes Service (ACS) de cluster de données volumineuses](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="prerequisites"></a>Prérequis

- Pour un environnement AKS, la condition minimale de la machine virtuelle au moins deux agent les machines virtuelles est (en plus de serveur maître), avec au moins 4 processeurs et 32 Go de mémoire chacune. Infrastructure Azure offre plusieurs options de taille pour les machines virtuelles, consultez [ici](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes) pour les sélections dans la région que vous voulez déployer.
  
- Cette section, vous devez être en cours d’exécution Azure CLI version 2.0.4 ou version ultérieure. Si vous avez besoin installer ou mettre à niveau, consultez [installer Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli). Exécutez `az --version` pour trouver la version, si nécessaire.

- Installer [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/). Cluster de données volumineux de SQL Server requiert toute version mineure dans la plage de 1.10 version pour Kubernetes, pour le serveur et client. Pour installer une version spécifique sur le client kubectl, consultez [installer kubectl binaire via curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Pour AKS, vous devez utiliser `--kubernetes-version` paramètre pour spécifier une version différente de celle par défaut. Notez qu’à la période de mise en production CTP2.0, AKS prend uniquement en charge les versions 1.10.7 et 1.10.8. 


> [!NOTE]
Notez que la version de client/serveur incliner qui est pris en charge est +/-1 version mineure. La documentation de Kubernetes indique que « un client doit être décalées ne plusieurs versions mineures du serveur maître, mais peut entraîner le maître par jusqu'à une version mineure. Par exemple, un serveur maître v1.3 doit fonctionner avec les nœuds v1.3 v1.1 et v1.2 et doit fonctionner avec v1.2 v1.3, clients et v1.4. » Pour plus d’informations, consultez [Kubernetes pris en charge les versions et composant de décalage](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

En outre, notez que `az aks kubernetes install-cli` installera le client kubectl avec une version inférieure qui le 1.10 requis. Suivez au-dessus des instructions pour installer la version appropriée du client kubectl.

## <a name="create-a-resource-group"></a>Créer un groupe de ressources

Un groupe de ressources Azure est un groupe logique dans Azure les ressources sont déployées et gérées. Les étapes suivantes vous connecter à Azure et créer un groupe de ressources pour le cluster AKS.

> [!TIP]
> Si vous utilisez Windows, utilisez PowerShell pour le reste des étapes.

1. À l’invite de commandes, exécutez la commande suivante et suivez les invites pour vous connecter à votre abonnement Azure :

    ```bash
    az login
    ```

1. Si vous avez plusieurs abonnements, vous pouvez afficher tous vos abonnements en exécutant la commande suivante :

   ```bash
   az account list
   ```

1. Si vous souhaitez remplacer par un autre abonnement, vous pouvez exécuter cette commande :

   ```bash
   az account set --subscription <subscription id>
   ```

1. Créer un groupe de ressources avec le **az groupe créer** commande. L’exemple suivant crée un groupe de ressources nommé `sqlbigdatagroup` dans le `westus2` emplacement.

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Créer un cluster Kubernetes

1. Créer un cluster Kubernetes dans ACS avec la [créer az aks](https://docs.microsoft.com/cli/azure/aks) commande. L’exemple suivant crée un cluster Kubernetes nommé *kubcluster* un Linux nœud maître et deux nœuds de l’agent Linux. Vérifiez que vous créez le cluster AKS dans le même groupe de ressources que vous avez utilisé dans les sections précédentes.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_E4s_v3 \
    --node-count 2 \
    --kubernetes-version 1.10.7
    ```

    Vous pouvez augmenter ou réduire le nombre d’agents par défaut en modifiant le `--node-count <n>` où `<n>` est le nombre de nœuds d’agent que vous souhaitez effectuer.

    Après quelques minutes, la commande se termine et retourne des informations formatées JSON sur le cluster.

1. Enregistrer la sortie JSON à partir de la commande précédente pour une utilisation ultérieure.

## <a name="connect-to-the-cluster"></a>Connectez-vous au cluster

1. Pour configurer kubectl pour vous connecter à votre cluster Kubernetes, exécutez le [az aks get-credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) commande. Cette étape télécharge les informations d’identification et configure l’interface CLI pour les utiliser kubectl.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Pour vérifier la connexion à votre cluster, utilisez le [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) commande pour retourner une liste des nœuds du cluster.  L’exemple ci-dessous montre la sortie si vous deviez avoir 1 master et 3 nœuds de l’agent.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Étapes suivantes

Les étapes décrites dans cet article configuré un cluster Kubernetes dans ACS. L’étape suivante consiste à déployer SQL Server 2019 des données volumineuses vers le cluster.

[Démarrage rapide : Déployer le cluster de données volumineux de SQL Server sur Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
