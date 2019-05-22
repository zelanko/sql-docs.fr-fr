---
title: Persistance des données sur Kubernetes
titleSuffix: SQL Server big data clusters
description: En savoir plus sur le fonctionne de la persistance des données dans un cluster de données volumineux de SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d08d3607a2670a441cdd300ca25b95ad760e0ab5
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994068"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Persistance des données avec un cluster volumineux de données SQL Server sur Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Volumes persistants](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) fournissent un modèle de plug-in pour le stockage dans Kubernetes. Comment le stockage est fourni est abstrait à partir de la façon dont elle est consommée. Par conséquent, vous pouvez fournir votre propre stockage hautement disponible et branchez-le sur le cluster de données volumineux de SQL Server. Cela vous donne un contrôle total sur le type de stockage, de disponibilité et de performances dont vous avez besoin. Kubernetes prend en charge différents types de solutions de stockage, y compris les disques et les fichiers Azure, NFS, le stockage local et bien plus encore.

## <a name="configure-persistent-volumes"></a>Configurer des volumes persistants

Le cluster de données volumineux un SQL Server consomme ces volumes persistants consiste à l’aide de [Classes de stockage](https://kubernetes.io/docs/concepts/storage/storage-classes/). Vous pouvez créer des classes de stockage différents pour différents types de stockage et les spécifier au moment du déploiement de cluster big data. Vous pouvez configurer la classe de stockage et de la taille de revendication de volume persistant à utiliser dans quel but au niveau du pool. Crée un cluster de données volumineux de SQL Server [les revendications de volume persistant](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) avec le nom de classe de stockage spécifié pour chaque composant qui nécessite des volumes persistants. Ensuite, elle monte l’ou les volumes persistant correspondant dans le pod. 

## <a name="configure-big-data-cluster-storage-settings"></a>Configurer les paramètres de stockage de cluster de données volumineuses

Similaire aux autres personnalisations, vous pouvez spécifier les paramètres de stockage dans les fichiers de configuration de cluster au moment du déploiement pour chaque pool et le plan de contrôle. S’il n’existe aucun paramètre de configuration de stockage dans les spécifications de pool, les paramètres de stockage de plan de contrôle seront utilisée. Il s’agit d’un exemple de la section de configuration de stockage que vous pouvez inclure dans la spécification :

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

Déploiement de cluster big data utilisent le stockage persistant pour stocker des données, les métadonnées et les journaux pour les différents composants. Vous pouvez personnaliser la taille des revendications de volume persistant créé dans le cadre du déploiement. En tant que meilleure pratique, nous vous recommandons d’utiliser les classes de stockage avec un *conserver* [récupérer de la stratégie](https://kubernetes.io/docs/concepts/storage/storage-classes/#reclaim-policy).

> [!NOTE]
> Dans CTP 3.0, vous ne pouvez pas modifier le déploiement paramètre post de la configuration de stockage. En outre, seuls `ReadWriteOnce` mode d’accès pour l’ensemble du cluster est prise en charge.

> [!WARNING]
> En cours d’exécution sans stockage persistant peut fonctionner dans un environnement de test, mais cela peut entraîner un cluster non fonctionnelles. Lors des redémarrages de pod, données de métadonnées ou pour un utilisateur de cluster seront définitivement perdues. Nous déconseillons d’exécuter dans cette configuration. 

[Configurer le stockage](#config-samples) section fournit des exemples supplémentaires sur la façon de configurer les paramètres de stockage pour votre déploiement de cluster de données volumineuses de SQL Server.

## <a name="aks-storage-classes"></a>Classes de stockage AKS

ACS est fourni avec [deux classes de stockage intégrée](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) **par défaut** et **premium managed** , ainsi que le fournisseur dynamique pour eux. Vous pouvez spécifier des deux ou créer votre propre classe de stockage pour le déploiement de cluster de données volumineux avec le stockage persistant est activé. Par défaut, généré dans le fichier de configuration de cluster pour aks *aks-dev-test.json* est fourni avec des configurations de stockage persistant à utiliser **par défaut** classe de stockage.

> [!WARNING]
> Volumes persistants créés avec les classes de stockage intégrée **par défaut** et **premium managed** ont une stratégie de demande de récupération de *supprimer*. Au moment où vous supprimer le cluster de données volumineux de SQL Server, les revendications de volume persistant obtient également les volumes supprimés et puis persistants. Vous pouvez créer des classes de stockage personnalisés à l’aide de **azure-disque** privioner avec un *conserver* récupérer la stratégie comme indiqué dans [cela](https://docs.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes) article.


## <a name="minikube-storage-class"></a>Classe de stockage Minikube

Minikube est fourni avec une classe de stockage intégré appelée **standard** ainsi que d’un fournisseur dynamique pour celui-ci. La configuration intégrée dans fichier minikube *minikube-dev-test.json* a les paramètres de configuration de stockage dans la spécification de plan de contrôle. Les mêmes paramètres s’appliqueront à toutes les spécifications de pools. Vous pouvez également personnaliser une copie de ce fichier et l’utiliser pour votre déploiement de cluster de données volumineuses sur minikube. Vous pouvez modifier le fichier personnalisé et modifier la taille des revendications volumes persistants pour les pools spécifiques prendre en charge les charges de travail à exécuter manuellement. Vous pouvez aussi consulter [configurer le stockage](#config-samples) modifie de section pour obtenir des exemples sur la procédure à suivre à l’aide de *mssqlctl* commandes.

## <a name="kubeadm-storage-classes"></a>Classes de stockage Kubeadm

Kubeadm n’est pas fourni avec une classe de stockage intégrée. Vous devez créer vos propres classes de stockage et les volumes persistants à l’aide de stockage local ou votre fournisseur préféré, tel que [tour](https://github.com/rook/rook). Dans ce cas, vous devez définir le **className** à la classe de stockage que vous avez configuré. 

> [!NOTE]
>  Dans le texte généré dans le fichier de configuration de déploiement pour *kubeadm kubeadm-dev-test.json* aucun nom de classe de stockage spécifié pour le stockage des journaux et des données. Avant le déploiement, vous devez personnaliser le fichier de configuration et définir la valeur de className sinon que les validations avant le déploiement échoue. Déploiement a également une étape de validation qui vérifie l’existence de la classe de stockage, mais pas pour les volumes persistants nécessaires. Vous devez vous assurer de que vous créez suffisamment volumes en fonction de l’échelle de votre cluster. Dans CTP 3.0, pour la taille de cluster par défaut, vous devez créer au moins 23 volumes. [Ici](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu) est un exemple sur la façon de créer des volumes persistants à l’aide du fournisseur local.


## <a name="customize-storage-configurations-for-each-pool"></a>Personnaliser les configurations de stockage pour chaque pool

Pour toutes les personnalisations, vous devez d’abord créer une copie de la génération dans le fichier de configuration que vous souhaitez utiliser. Par exemple, la commande suivante crée une copie de la *aks-dev-test.json* fichier de configuration de déploiement dans le répertoire actif :

```bash
mssqlctl cluster config init --src aks-dev-test.json --target custom.json
```

Ensuite, vous pouvez personnaliser votre fichier de configuration en le modifiant manuellement, ou vous pouvez utiliser *ensemble de section de configuration de cluster mssqlctl* commande. Cette commande set utilise une combinaison des bibliothèques jsonpath et jsonpatch pour offrir des moyens de modifier votre fichier de configuration.

### <a name="configure-size"></a>Configurer la taille

Par défaut, la taille des revendications de volume persistant pour chacune des pods configurés dans le cluster est de 10 Go. Vous pouvez mettre à jour cette valeur pour prendre en compte les charges de travail en cours d’exécution dans un fichier de configuration personnalisées avant le déploiement de cluster.

L’exemple suivant met à jour uniquement la taille de volume persistant des revendications pour les données stockées dans le pool de stockage à Gi 100. Notez que la section de stockage doit exister dans le fichier de configuration pour le pool de stockage avant d’exécuter cette commande :

```bash
mssqlctl cluster config section set -c custom.json -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.size=100Gi"
```

L’exemple suivant met à jour la taille de volume persistant des revendications pour tous les pools à Gi 32 :

```bash
mssqlctl cluster config section set -c custom.json -j "$.spec.controlPlane.spec.storage.data.size=32Gi"
```

### <a id="config-samples"></a> Configurer la classe de stockage

Exemple suivant montre comment modifier la classe de stockage pour le plan de contrôle :

```bash
mssqlctl cluster config section set -c custom.json -j "$.spec.controlPlane.spec.storage.data.className=<yourStorageClassName>"
```

Une autre option consiste à modifier manuellement le fichier de configuration personnalisée ou utiliser jsonpatch comme dans l’exemple suivant qui modifie la classe de stockage pour le pool de stockage. Créer un *patch.json* fichier avec ce contenu :

```json
{
  "patch": [
    {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage",
      "value": {
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

Appliquer le fichier de correctif. Utilisez *ensemble de section de configuration de cluster mssqlctl* commande pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le fichier patch.json à un custom.json de fichier de configuration de déploiement cible.

```bash
mssqlctl cluster config section set -c custom.json -p ./patch.json
```

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir une documentation complète sur les volumes dans Kubernetes, consultez le [documentation Kubernetes sur les Volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Pour plus d’informations sur le déploiement d’un cluster de données volumineux de SQL Server, consultez [le déploiement de SQL Server du cluster big data sur Kubernetes](deployment-guidance.md).

