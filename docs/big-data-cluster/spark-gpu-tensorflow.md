---
title: Prise en charge de GPU et TensorFlow
titleSuffix: SQL Server big data clusters
description: Déployer un cluster de données volumineuses avec prise en charge GPU et utiliser TensorFlow dans Azure Data Studio Notebooks.
author: lgongmsft
ms.author: shivprashant
ms.reviewer: jroth
manager: craigg
ms.date: 03/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 682e68ede0646b9455bd9b4b759b4e3d760223d9
ms.sourcegitcommit: e2d65828faed6f4dfe625749a3b759af9caa7d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670882"
---
# <a name="deploy-a-big-data-cluster-with-gpu-support-and-run-tensorflow"></a>Déployer un cluster de données volumineuses avec prise en charge GPU et exécuter TensorFlow

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article montre comment déployer un cluster de données volumineux sur Azure Kubernetes Service (AKS) qui prend en charge les pools de nœuds compatibles GPU pour les charges de travail de calcul intensif. Puis, vous exécutez des exemples de notebooks dans Azure Data Studio qui effectuent la classification d’images avec TensorFlow pour le GPU.

## <a name="prerequisites"></a>Prérequis

- [Outils de Big data](deploy-big-data-tools.md):
  - **mssqlctl**
  - **kubectl**
  - **Azure Data Studio**
  - **Extension de SQL Server 2019**
  - **Azure CLI**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="create-an-aks-cluster"></a>Créer un cluster AKS

Les étapes suivantes utilisent l’interface CLI Azure pour créer un cluster AKS qui prend en charge les GPU.

1. À l’invite de commandes, exécutez la commande suivante et suivez les invites pour vous connecter à votre abonnement Azure :

    ```azurecli
    az login
    ```

1. Créer un groupe de ressources avec le **az groupe créer** commande. L’exemple suivant crée un groupe de ressources nommé `sqlbigdatagroupgpu` dans le `eastus` emplacement.

   ```azurecli
   az group create --name sqlbigdatagroupgpu --location eastus
   ```

1. Créer un cluster Kubernetes dans ACS avec la [créer az aks](https://docs.microsoft.com/cli/azure/aks) commande. L’exemple suivant crée un cluster Kubernetes nommé `gpucluster` dans le `sqlbigdatagroupgpu` groupe de ressources.

   ```azurecli
   az aks create --name gpucluster --resource-group sqlbigdatagroupgpu --generate-ssh-keys --node-vm-size Standard_NC6 --node-count 3 --node-osdisk-size 50 --kubernetes-version 1.11.9 --location eastus
   ```

   > [!NOTE]
   > Ce cluster utilise le **Standard_NC6** [taille de machine de virtuelle GPU optimisé](https://docs.microsoft.com/azure/virtual-machines/linux/sizes-gpu), qui est une des machines virtuelles spécialisées disponibles avec un ou plusieurs GPU NVIDIA. Pour plus d’informations, consultez [GPU d’utilisation pour les charges de travail de calcul intensif sur Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/gpu-cluster).

1. Pour configurer kubectl pour vous connecter à votre cluster Kubernetes, exécutez le [az aks get-credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) commande.

   ```azurecli
   az aks get-credentials --overwrite-existing --resource-group=sqlbigdatagroupgpu --name gpucluster
   ```

## <a name="apply-yaml-manifest"></a>Appliquer le manifeste YAML

1. Utilisez **kubectl** pour créer un espace de noms Kubernetes nommé `gpu-resources`.

   ```
   kubectl create namespace gpu-resources
   ```

1. Enregistrer le contenu du fichier YAML suivant dans un fichier nommé **nvidia-device-plug-in-ds.yaml**. Enregistrez-les dans le répertoire de travail sur votre ordinateur que vous exécutez **kubectl** à partir de.

   Mise à jour le `image: nvidia/k8s-device-plugin:1.11` moitié le manifeste qui corresponde à votre version de Kubernetes. Par exemple, si votre cluster AKS s’exécute Kubernetes version 1.12, mettre à jour la balise à `image: nvidia/k8s-device-plugin:1.12`.

   ```yaml
   apiVersion: extensions/v1beta1
   kind: DaemonSet
   metadata:
     labels:
       kubernetes.io/cluster-service: "true"
     name: nvidia-device-plugin
     namespace: gpu-resources
   spec:
     template:
       metadata:
         # Mark this pod as a critical add-on; when enabled, the critical add-on scheduler
         # reserves resources for critical add-on pods so that they can be rescheduled after
         # a failure.  This annotation works in tandem with the toleration below.
         annotations:
           scheduler.alpha.kubernetes.io/critical-pod: ""
         labels:
           name: nvidia-device-plugin-ds
       spec:
         tolerations:
         # Allow this pod to be rescheduled while the node is in "critical add-ons only" mode.
         # This, along with the annotation above marks this pod as a critical add-on.
         - key: CriticalAddonsOnly
           operator: Exists
         containers:
         - image: nvidia/k8s-device-plugin:1.11 # Update this tag to match your Kubernetes version
           name: nvidia-device-plugin-ctr
           securityContext:
             allowPrivilegeEscalation: false
             capabilities:
               drop: ["ALL"]
           volumeMounts:
             - name: device-plugin
               mountPath: /var/lib/kubelet/device-plugins
         volumes:
           - name: device-plugin
             hostPath:
               path: /var/lib/kubelet/device-plugins
         nodeSelector:
           beta.kubernetes.io/os: linux
           accelerator: nvidia
   ```

1. Maintenant, utilisez le kubectl appliquer la commande pour créer le DaemonSet. **NVIDIA-device-plug-in-ds.yaml** doit être dans le répertoire de travail lorsque vous exécutez la commande suivante :

   ```
   kubectl apply -f nvidia-device-plugin-ds.yaml
   ```

## <a name="deploy-the-big-data-cluster"></a>Déployer le cluster de données volumineuses

Pour déployer un cluster de données volumineuses de SQL Server 2019 (version préliminaire) qui prend en charge les GPU, vous devez déployer à partir d’un Registre docker spécifique et un référentiel. Plus précisément, vous utilisez des valeurs différentes pour **DOCKER_REGISTRY**, **DOCKER_REPOSITORY**, **DOCKER_USERNAME**, **DOCKER_PASSWORD**, et **DOCKER_EMAIL**. Les sections suivantes fournissent des exemples montrant comment définir les variables d’environnement. Utilisez les sections de la Windows ou Linux selon la plateforme du client que vous utilisez pour déployer le cluster de données volumineuses.

### <a name="windows"></a>Windows

   1. À l’aide d’une fenêtre CMD (pas PowerShell), configurer les variables d’environnement suivantes. N’utilisez pas les valeurs entre guillemets.

      ```cmd
      SET ACCEPT_EULA=yes
      SET CLUSTER_PLATFORM=aks

      SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
      SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
      SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
      SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

      SET DOCKER_REGISTRY=marinchcreus3.azurecr.io
      SET DOCKER_REPOSITORY=ctp24-8-0-61-gpu
      SET DOCKER_USERNAME=<your username, gpu-specific credentials provided by Microsoft>
      SET DOCKER_PASSWORD=<your password, gpu-specific credentials provided by Microsoft>
      SET DOCKER_EMAIL=<your email address>
      SET DOCKER_PRIVATE_REGISTRY=1
      SET STORAGE_SIZE=10Gi
      ```

   1. Déployer le cluster de données volumineuses :

      ```cmd
      mssqlctl cluster create --name gpubigdatacluster
      ```

### <a name="linux"></a>Linux

   1. Initialiser les variables d’environnement suivantes. Dans l’interpréteur de commandes, vous pouvez utiliser des guillemets autour de chaque valeur.

      ```bash
      export ACCEPT_EULA=yes
      export CLUSTER_PLATFORM="aks"

      export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
      export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
      export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
      export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

      export DOCKER_REGISTRY="marinchcreus3.azurecr.io"
      export DOCKER_REPOSITORY="ctp24-8-0-61-gpu"
      export DOCKER_USERNAME="<your username, gpu-specific credentials provided by Microsoft>"
      export DOCKER_PASSWORD="<your password, gpu-specific credentials provided by Microsoft>"
      export DOCKER_EMAIL="<your email address>"
      export DOCKER_PRIVATE_REGISTRY="1"
      export STORAGE_SIZE="10Gi"
      ```

   1. Déployer le cluster de données volumineuses :

      ```bash
      mssqlctl cluster create --name gpubigdatacluster
      ```

## <a name="run-the-tensorflow-example"></a>Exécutez l’exemple TensorFlow

Les blocs-notes deux exemples suivants montrent deux image classification modèles d’apprentissage sur un seul nœud du cluster Spark à l’aide de TensorFlow pour le GPU.

| Téléchargement du bloc-notes | Description |
|---|---|
| [**tf-cuda8.ipynb**](https://aka.ms/AA4jdgd) | Utilise CUDA 8, CUDNN 6 et TensorFlow 1.4.0.  |
| [**tf-cuda9.ipynb**](https://aka.ms/AA4ixzr) | Utilise TensorFlow 1.12.0 CUDA 9 et CUDNN 7. |

Placez le fichier de bloc-notes approprié sur votre ordinateur local, puis ouvrir et exécuter dans Azure Data Studio, l’utilisation du noyau PySpark3. Sauf si vous avez un besoin spécifique pour une version antérieure de CUDA ou TensorFlow, choisissez CUDA 9/CUDNN 7/TensorFlow 1.12.0. Pour plus d’informations sur l’utilisation des blocs-notes avec les clusters de données volumineuses, consultez [comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md).

> [!NOTE]
> Notez que les blocs-notes installer des logiciels dans les emplacements du système. Cela est possible, car les ordinateurs portables exécutent actuellement avec des privilèges root dans CTP 2.4.

Après avoir installé les bibliothèques de GPU NVIDIA et TensorFlow pour le GPU, les blocs-notes liste périphériques GPU disponibles. Ensuite, ils ajusteront et évaluent un modèle TensorFlow afin qu’il reconnaisse les chiffres manuscrits à l’aide de l’ensemble de données MNIST. Après avoir vérifié l’espace disque disponible, ils téléchargent et exécuter l’exemple de classification d’images CIFAR 10 à partir de [ https://github.com/tensorflow/models.git ](https://github.com/tensorflow/models.git). En exécutant l’exemple CIFAR 10 sur des clusters ayant différents GPU, vous pouvez observer l’augmentation de vitesse offertes par chaque génération de GPU disponible dans Azure.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Pour supprimer le cluster de données volumineux, utilisez la commande suivante :

```
mssqlctl cluster delete --name gpubigdatacluster
```

La commande précédente ne supprime pas le cluster AKS. Pour supprimer le cluster AKS et les ressources associées, utilisez la commande suivante :

```azurecli
az group delete -n sqlbigdatagroupgpu
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses de SQL Server 2019 (version préliminaire), consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
