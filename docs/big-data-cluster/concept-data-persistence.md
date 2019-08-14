---
title: Persistance des données sur Kubernetes
titleSuffix: SQL Server big data clusters
description: Découvrez plus d’informations sur le fonctionnement de la persistance des données dans un cluster Big Data SQL Server 2019.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: dcc30e8d86a1a767291b410df7cfd3aa42edf27f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68470993"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Persistance des données avec un cluster Big Data SQL Server sur Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Les [volumes persistants](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) fournissent un modèle de plug-in pour le stockage dans Kubernetes. La façon dont le stockage est fourni dépend de la façon dont il est consommé. Par conséquent, vous pouvez utiliser votre propre stockage à haute disponibilité et le connecter au cluster Big Data SQL Server. Ceci vous donne un contrôle total sur le type de stockage, sur la disponibilité et sur les performances dont vous avez besoin. Kubernetes prend en charge différents types de solutions de stockage, notamment les disques/fichiers Azure, NFS, le stockage local, etc.

## <a name="configure-persistent-volumes"></a>Configurer des volumes persistants

La façon dont un cluster Big Data SQL Server consomme ces volumes persistants consiste à utiliser des [classes de stockage](https://kubernetes.io/docs/concepts/storage/storage-classes/). Vous pouvez créer différentes classes de stockage pour différents types de stockage et les spécifier au moment du déploiement du cluster Big Data. Vous pouvez configurer la classe de stockage et la taille de revendication des volumes persistants à utiliser pour un certain objectif au niveau du pool. Un cluster Big Data SQL Server crée des [revendications de volumes persistants](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) avec le nom de la classe de stockage spécifié pour chaque composant nécessitant des volumes persistants. Il monte ensuite le ou les volumes persistants correspondants dans le pod. 

## <a name="configure-big-data-cluster-storage-settings"></a>Configurer les paramètres de stockage du cluster Big Data

À l’instar des autres personnalisations, vous pouvez spécifier des paramètres de stockage dans les fichiers de configuration du cluster au moment du déploiement pour chaque pool et pour le plan de contrôle. S’il n’y a pas de paramètre de configuration du stockage dans les spécifications du pool, les paramètres de stockage du plan de contrôle sont utilisés. Voici un exemple de la section de configuration du stockage que vous pouvez inclure dans la spécification :

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

Le déploiement du cluster Big Data utilisera un stockage persistant pour stocker les données, les métadonnées et les journaux pour différents composants. Vous pouvez personnaliser la taille des revendications de volumes persistants créées dans le cadre du déploiement. À titre de bonne pratique, nous vous recommandons d’utiliser des classes de stockage avec une [stratégie de récupération](https://kubernetes.io/docs/concepts/storage/storage-classes/#reclaim-policy) *Retain* (Conserver).

> [!NOTE]
> Dans CTP 3.2, vous ne pouvez pas modifier le paramétrage de la configuration du stockage après le déploiement. En outre, seul le mode d’accès `ReadWriteOnce` pour l’ensemble du cluster est pris en charge.

> [!WARNING]
> L’exécution sans stockage persistant peut fonctionner dans un environnement de test, mais elle peut aboutir à un cluster non fonctionnel. Après le redémarrage d’un pod, les métadonnées du cluster et/ou les données utilisateur seront définitivement perdues. Nous vous déconseillons d’utiliser cette configuration. 

La section [Configuration du stockage](#config-samples) fournit d’autres exemples de configuration des paramètres de stockage pour le déploiement de votre cluster Big Data SQL Server.

## <a name="aks-storage-classes"></a>Classes de stockage d’AKS

AKS est fourni avec [deux classes de stockage intégrées](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv), **default** et **managed-premium**, et avec un provisionneur dynamique pour celles-ci. Vous pouvez spécifier l’une ou l’autre de ces classes, ou créer votre propre classe de stockage, pour déployer un cluster Big Data avec le stockage persistant activé. Par défaut, le fichier de configuration de cluster intégré pour AKS, *aks-dev-test*, est fourni avec des configurations de stockage persistantes qui utilisent la classe de stockage **default**.

> [!WARNING]
> Les volumes persistants créés avec les classes de stockage intégrées **default** et **managed-premium** ont une stratégie de récupération *Delete* (Supprimer). Ainsi, au moment où vous supprimez le cluster Big Data SQL Server, les revendications de volumes persistants sont supprimées, puis les volumes persistants le sont à leur tour. Vous pouvez créer des classes de stockage personnalisées en utilisant le provisionneur **azure-disk** avec une stratégie de récupération *Retain* (Conserver), comme expliqué dans [cet](https://docs.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes) article.


## <a name="minikube-storage-class"></a>Classe de stockage Minikube

Minikube est fourni avec une classe de stockage intégrée appelée **standard** ainsi qu’un provisionneur dynamique pour celle-ci. Le fichier de configuration intégré pour minikube, *minikube-dev-test*, a les paramètres de configuration de stockage présents dans la spécification du plan de contrôle. Les mêmes paramètres seront appliqués à toutes les spécifications des pools. Vous pouvez aussi personnaliser une copie de ce fichier et l’utiliser pour votre déploiement de cluster Big Data sur minikube. Vous pouvez modifier manuellement le fichier personnalisé et changer la taille des revendications de volumes persistants pour des pools spécifiques afin de prendre en charge les charges de travail que vous voulez exécuter. Vous pouvez aussi consultez la section [Configurer le stockage](#config-samples) pour obtenir des exemples sur la façon d’effectuer des modifications avec des commandes *azdata*.

## <a name="kubeadm-storage-classes"></a>Classes de stockage de Kubeadm

Kubeadm n’est pas fourni avec une classe de stockage intégrée. Vous devez créer vos propres classes de stockage et vos propres volumes persistants en utilisant un stockage local ou votre provisionneur préféré, par exemple [Rook](https://github.com/rook/rook). Dans ce cas, vous définissez **className** sur la classe de stockage que vous avez configurée. 

> [!NOTE]
>  Dans le fichier de configuration du déploiement intégré pour *kubeadm kubeadm-dev-test*, aucun nom de classe de stockage n’est spécifié pour le stockage des données et des journaux. Avant le déploiement, vous devez personnaliser le fichier de configuration et définir la valeur de className, sans quoi les validations préalables au déploiement échouent. Le déploiement comporte également une étape de validation qui vérifie l’existence de la classe de stockage, mais pas pour les volumes persistants nécessaires. Vous devez vérifier que vous créez suffisamment de volumes en fonction de l’échelle de votre cluster. Dans CTP 3.1, vous devez créer au moins 23 volumes pour la taille de cluster par défaut. [Voici](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu) un exemple de création de volumes persistants avec le provisionneur local.


## <a name="customize-storage-configurations-for-each-pool"></a>Personnaliser les configurations de stockage pour chaque pool

Pour toutes les personnalisations, vous devez d’abord créer une copie du fichier de configuration intégré que vous voulez utiliser. Par exemple, la commande suivante crée une copie des fichiers de configuration de déploiement *aks-dev-test* dans un sous-répertoire nommé `custom` :

```bash
azdata bdc config init --source aks-dev-test --target custom
```

Ceci crée deux fichiers, **cluster.json** et **control.json**, qui peuvent être personnalisés en les modifiant manuellement, ou bien vous pouvez utiliser la commande **azdata bdc config**. Vous pouvez utiliser une combinaison de bibliothèques jsonpath et jsonpatch pour fournir des moyens de modifier vos fichiers de configuration.


### <a id="config-samples"></a> Configurer le nom de la classe de stockage et/ou la taille des revendications

Par défaut, la taille des revendications de volumes persistants provisionnés pour chaque pod provisionné dans le cluster est de 10 Go. Vous pouvez mettre à jour cette valeur pour prendre en charge les charges de travail que vous exécutez dans un fichier de configuration personnalisé avant le déploiement du cluster.

L’exemple suivant met à jour la taille des revendications de volumes persistants à 32 Gi dans **control.json**. Si cette valeur n’est pas remplacée au niveau du pool, ce paramètre est appliqué à tous les pools :

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.size=100Gi"
```

L’exemple suivant montre comment modifier la classe de stockage pour le fichier **control.json** :

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.className=<yourStorageClassName>"
```

Une autre option consiste à modifier manuellement le fichier de configuration personnalisé ou à utiliser le correctif json comme dans l’exemple suivant, qui modifie la classe de stockage pour le pool de stockage. Créez un fichier *patch.json* avec ce contenu :

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
        "type":"Storage",
        "replicas":2,
        "storage":{
            "data":{
                    "size": "100Gi",
                    "className": "myStorageClass",
                    "accessMode":"ReadWriteOnce"
                    },
            "logs":{
                    "size":"32Gi",
                    "className":"myStorageClass",
                    "accessMode":"ReadWriteOnce"
                    }
                }
            }
        }
    ]
}
```

Appliquez le fichier de correctif. Utilisez la commande **azdata bdc config patch** pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le fichier patch.json à un fichier de configuration de déploiement cible custom.json.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir une documentation complète sur les volumes dans Kubernetes, consultez la [documentation de Kubernetes sur les volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Pour plus d’informations sur le déploiement d’un cluster Big Data SQL Server, consultez [Guide pratique pour déployer des clusters Big Data SQL Server sur Kubernetes](deployment-guidance.md).

