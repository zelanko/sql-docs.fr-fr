---
title: Persistance des données sur Kubernetes
titleSuffix: SQL Server big data clusters
description: En savoir plus sur le fonctionnement de la persistance des données dans un cluster SQL Server 2019 Big Data.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9142836032acc5e302c947e1619d17b07faff683
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419473"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Persistance des données avec SQL Server Cluster Big Data sur Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Les [volumes persistants](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) fournissent un modèle de plug-in pour le stockage dans Kubernetes. Le mode de stockage fourni est soustrait de la manière dont il est consommé. Par conséquent, vous pouvez mettre votre propre stockage à haute disponibilité et le connecter au cluster SQL Server Big Data. Vous bénéficiez ainsi d’un contrôle total sur le type de stockage, la disponibilité et les performances dont vous avez besoin. Kubernetes prend en charge différents types de solutions de stockage, notamment les disques/fichiers Azure, NFS, le stockage local, etc.

## <a name="configure-persistent-volumes"></a>Configurer des volumes persistants

La façon dont un cluster SQL Server Big Data consomme ces volumes persistants consiste à utiliser des [classes de stockage](https://kubernetes.io/docs/concepts/storage/storage-classes/). Vous pouvez créer des classes de stockage différentes pour différents types de stockage et les spécifier au moment du déploiement du cluster Big Data. Vous pouvez configurer la classe de stockage et la taille de revendication de volume persistant à utiliser au niveau du pool. Un cluster SQL Server Big Data crée des [revendications de volume persistantes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) avec le nom de classe de stockage spécifié pour chaque composant nécessitant des volumes persistants. Il monte ensuite le ou les volumes persistants correspondants dans le POD. 

## <a name="configure-big-data-cluster-storage-settings"></a>Configurer Big Data paramètres de stockage du cluster

À l’instar des autres personnalisations, vous pouvez spécifier des paramètres de stockage dans les fichiers de configuration du cluster au moment du déploiement pour chaque pool et le plan de contrôle. S’il n’existe aucun paramètre de configuration de stockage dans les spécifications du pool, les paramètres de stockage du plan de contrôle sont utilisés. Voici un exemple de la section Configuration du stockage que vous pouvez inclure dans la spécification:

```json
    "storage": 
    {
      "data": {
        "className": "default",
        "accessMode": "ReadWriteOnce",
        "size": "15Gi"
      },
      "logs": {
        "className": "default",
        "accessMode": "ReadWriteOnce",
        "size": "10Gi"
    }
```

Le déploiement de Big Data cluster utilisera un stockage persistant pour stocker des données, des métadonnées et des journaux pour différents composants. Vous pouvez personnaliser la taille des revendications de volume persistant créées dans le cadre du déploiement. Nous vous recommandons d’utiliser des classes de stockage avec une stratégie *conserver* la [récupération](https://kubernetes.io/docs/concepts/storage/storage-classes/#reclaim-policy).

> [!NOTE]
> Dans CTP 3,2, vous ne pouvez pas modifier le paramètre de configuration de stockage après le déploiement. En outre, `ReadWriteOnce` seul le mode d’accès pour l’ensemble du cluster est pris en charge.

> [!WARNING]
> L’exécution sans stockage persistant peut fonctionner dans un environnement de test, mais elle peut entraîner un cluster non fonctionnel. En cas de redémarrage de Pod, les métadonnées de cluster et/ou les données utilisateur seront définitivement perdues. Nous déconseillons l’exécution de cette configuration. 

La section [configuration du stockage](#config-samples) fournit des exemples supplémentaires sur la configuration des paramètres de stockage pour votre SQL Server Big Data déploiement de cluster.

## <a name="aks-storage-classes"></a>Classes de stockage AKS

AKS est fourni avec [deux classes de stockage intégrées](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) **default** et **Managed-Premium** , ainsi que le provisionnement dynamique pour eux. Vous pouvez spécifier l’une ou l’autre de ces ou créer votre propre classe de stockage pour le déploiement de Big Data cluster sur lequel le stockage persistant est activé. Par défaut, le fichier de configuration de cluster intégré pour AKS *AKS-dev-test* est fourni avec des configurations de stockage persistantes pour utiliser la classe de stockage **par défaut** .

> [!WARNING]
> Les volumes persistants créés avec les classes de stockage intégrées **default** et Managed **-Premium** ont une stratégie de récupération de *suppression*. Ainsi, au moment où vous supprimez le SQL Server Big Data cluster, les revendications de volume persistant sont également supprimées, puis les volumes persistants. Vous pouvez créer des classes de stockage personnalisées à l’aide d' **Azure-Disk** privioner avec une stratégie de récupération de *réserve* , comme indiqué dans [cet](https://docs.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes) article.


## <a name="minikube-storage-class"></a>Classe de stockage Minikube

Minikube est fourni avec une classe de stockage intégrée appelée **standard** , ainsi qu’un provisionneur dynamique pour celui-ci. Le fichier de configuration intégré pour minikube *minikube-dev-test* a les paramètres de configuration de stockage dans la spécification du plan de contrôle. Les mêmes paramètres seront appliqués à toutes les spécifications de pools. Vous pouvez également personnaliser une copie de ce fichier et l’utiliser pour votre déploiement de cluster Big Data sur minikube. Vous pouvez modifier manuellement le fichier personnalisé et modifier la taille des revendications de volumes persistants pour des pools spécifiques afin de prendre en charge les charges de travail que vous souhaitez exécuter. Ou consultez la section [configurer le stockage](#config-samples) pour obtenir des exemples sur la façon d’effectuer des modifications à l’aide des commandes *azdata* .

## <a name="kubeadm-storage-classes"></a>Classes de stockage Kubeadm

Kubeadm n’est pas fourni avec une classe de stockage intégrée. Vous devez créer vos propres classes de stockage et volumes persistants à l’aide du stockage local ou de votre approvisionnement préféré, par exemple [tour.](https://github.com/rook/rook) Dans ce cas, vous définissez le **className** sur la classe de stockage que vous avez configurée. 

> [!NOTE]
>  Dans le fichier de configuration du déploiement intégré pour *kubeadm kubeadm-dev-test* , aucun nom de classe de stockage n’est spécifié pour le stockage des données et du journal. Avant le déploiement, vous devez personnaliser le fichier de configuration et définir la valeur de className, sans quoi les validations de prédéploiement échoueront. Le déploiement comporte également une étape de validation qui vérifie l’existence de la classe de stockage, mais pas pour les volumes persistants nécessaires. Vous devez vous assurer que vous créez suffisamment de volumes en fonction de l’échelle de votre cluster. Dans la version CTP 3,1, vous devez créer au moins 23 volumes pour la taille de cluster par défaut. [Voici](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu) un exemple de création de volumes persistants à l’aide du service d’approvisionnement local.


## <a name="customize-storage-configurations-for-each-pool"></a>Personnaliser les configurations de stockage pour chaque pool

Pour toutes les personnalisations, vous devez d’abord créer une copie du fichier de configuration intégré que vous souhaitez utiliser. Par exemple, la commande suivante crée une copie des fichiers de configuration de déploiement *AKS-dev-test* dans un sous-répertoire `custom`nommé:

```bash
azdata bdc config init --source aks-dev-test --target custom
```

Cela crée deux fichiers, **cluster. JSON** et **Control. JSON** qui peuvent être personnalisés en les modifiant manuellement, ou vous pouvez utiliser la commande de **configuration azdata BDC** . Vous pouvez utiliser une combinaison de bibliothèques jsonpath et jsonpatch pour fournir des moyens de modifier vos fichiers de configuration.


### <a id="config-samples"></a>Configurer le nom de la classe de stockage et/ou la taille des revendications

Par défaut, la taille des revendications de volume persistantes approvisionnées pour chaque Pod approvisionnée dans le cluster est de 10 Go. Vous pouvez mettre à jour cette valeur pour prendre en charge les charges de travail que vous exécutez dans un fichier de configuration personnalisé avant le déploiement du cluster.

L’exemple suivant met à jour la taille des revendications de volume persistantes en 32Gi dans **Control. jsaon**. Si cette valeur n’est pas remplacée au niveau du pool, ce paramètre est appliqué à tous les pools:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.size=100Gi"
```

L’exemple suivant montre comment modifier la classe de stockage pour le fichier **Control. JSON** :

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.className=<yourStorageClassName>"
```

Une autre option consiste à modifier manuellement le fichier de configuration personnalisé ou à utiliser le correctif JSON, comme dans l’exemple suivant, qui modifie la classe de stockage pour le pool de stockage. Créez un fichier *patch. JSON* avec ce contenu:

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage"
      "value": {
          "type":"Storage",
          "replicas":2,
          "data": {
            "className": "default",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "default",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
      }
  ]
}
```

Appliquez le fichier correctif. Utilisez la commande **azdata BDC config patch** pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le fichier patch. JSON à un fichier de configuration de déploiement cible Custom. JSON.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir une documentation complète sur les volumes dans Kubernetes, consultez la [documentation Kubernetes sur les volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Pour plus d’informations sur le déploiement d’un cluster SQL Server Big Data, consultez [comment déployer SQL Server cluster Big Data sur Kubernetes](deployment-guidance.md).

