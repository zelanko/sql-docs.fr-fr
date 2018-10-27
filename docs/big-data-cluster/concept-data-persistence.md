---
title: Persistance des données avec SQL Server du cluster big data sur Kubernetes | Microsoft Docs
description: En savoir plus sur le fonctionne de la persistance des données dans un cluster de données volumineux de SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 9f80f8a4e8014b6d05a2e4c6a0b5697609381a07
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050827"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Persistance des données avec un cluster volumineux de données SQL Server sur Kubernetes

[Volumes persistants](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) fournissent un modèle de plug-in de stockage dans Kubernetes, où le stockage est fourni est complété tirée de la façon dont elle est consommée. Par conséquent, vous pouvez fournir votre propre stockage hautement disponible et branchez-le sur le cluster de cluster de données volumineuses de SQL Server. Cela vous donne un contrôle total sur le type de stockage, de disponibilité et de performances dont vous avez besoin. Kubernetes prend en charge différents types de solutions de stockage, y compris les disques et les fichiers Azure, NFS, le stockage local et bien plus encore.

## <a name="configure-persistent-volumes"></a>Configurer des volumes persistants

Le cluster de données volumineux de SQL Server consomme ces volumes persistants consiste à l’aide de [Classes de stockage](https://kubernetes.io/docs/concepts/storage/storage-classes/). Vous pouvez créer des classes de stockage différents pour différents types de stockage et les spécifier au moment du déploiement de cluster big data. Vous pouvez configurer la classe de stockage à utiliser dans quel but (pool). Cluster de données volumineux de SQL Server crée [les revendications de volume persistant](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) avec le nom de classe de stockage spécifié pour chaque pod qui nécessite des volumes persistants. Ensuite, elle monte l’ou les volumes persistant correspondant dans le pod.

> [!NOTE]

> Pour CTP 2.0, uniquement `ReadWriteOnce` mode d’accès pour l’ensemble du cluster est prise en charge.

## <a name="deployment-settings"></a>Paramètres de déploiement

Pour utiliser le stockage persistant pendant le déploiement, configurez le **USE_PERSISTENT_VOLUME** et **STORAGE_CLASS_NAME** variables d’environnement avant d’exécuter `mssqlctl create cluster` commande. **USE_PERSISTENT_VOLUME** a la valeur `true` par défaut. Vous pouvez remplacer la valeur par défaut et affectez-lui la valeur `false` et, dans ce cas, le cluster de données volumineux de SQL Server utilise emptyDir montages. 

> [!WARNING]
> En cours d’exécution sans stockage persistant peut fonctionner dans un environnement de test, mais cela peut entraîner un cluster non fonctionnelles. Lors des redémarrages de pod, données de métadonnées ou pour un utilisateur de cluster seront définitivement perdues.

Si vous définissez l’indicateur sur true, vous devez également fournir **STORAGE_CLASS_NAME** en tant que paramètre au moment du déploiement.

## <a name="aks-storage-classes"></a>Classes de stockage AKS

ACS est fourni avec [deux classes de stockage intégrée](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) **par défaut** et **premium managed** , ainsi que le fournisseur dynamique pour eux. Vous pouvez spécifier des deux ou créer votre propre classe de stockage pour le déploiement de cluster de données volumineux avec le stockage persistant est activé.

## <a name="minikube-storage-class"></a>Classe de stockage Minikube

Minikube est fourni avec une classe de stockage intégré appelée **standard** ainsi que d’un fournisseur dynamique pour celui-ci. Notez que sur minikube, si `USE_PERSISTENT_VOLUME=true` (valeur par défaut), vous devez également substituer la valeur par défaut pour le **STORAGE_CLASS_NAME** variable d’environnement, car la valeur par défaut est différente. Définissez la valeur sur `standard`: 

Sur Windows, utilisez la commande suivante :

```cmd
SET STORAGE_CLASS_NAME=standard
```

Sur Linux, utilisez la commande suivante :

```cmd
export STORAGE_CLASS_NAME=standard
```

Ou bien, vous pouvez supprimer à l’aide de volumes persistants sur minikube en définissant `USE_PERSISTENT_VOLUME=false`.

## <a name="kubeadm"></a>Kubeadm

Kubeadm n’est pas fourni avec une classe de stockage intégrée. Vous pouvez choisir de créer vos propres volumes persistants et les classes de stockage à l’aide de stockage local ou votre fournisseur préféré, tel que [tour](https://github.com/rook/rook). Dans ce cas, vous devez définir le **STORAGE_CLASS_NAME** à la classe de stockage que vous avez configuré. Vous pouvez également définir `USE_PERSISTENT_VOLUME=false` dans des environnements de test, mais notez l’avertissement précédent dans le **paramètres de déploiement** section de cet article.  

## <a name="on-premises-cluster"></a>Cluster local

Clusters locaux à l’évidence ne sont pas fournies avec n’importe quelle classe de stockage intégrée, par conséquent, vous devez configurer [volumes persistants](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)/[fournisseurs pour](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/) avance, puis utilisez le correspondantes classes de stockage au cours du déploiement de cluster de données volumineuses de SQL Server.

# <a name="customize-storage-size-for-each-pool"></a>Personnaliser la taille de stockage pour chaque pool
Par défaut, la taille du volume persistant pour chacune des pods configurés dans le cluster est de 6 Go. Cela est configurable en définissant la variable d’environnement `STORAGE_SIZE` sur une autre valeur. Par exemple, vous pouvez exécuter de commande ci-dessous pour définir la valeur à 10 Go, avant d’exécuter le `mssqlctl create cluster command`.

```bash
export STORAGE_SIZE=10Gi
```

Vous pouvez également avoir différentes configurations pour les paramètres de stockage persistant de ce nom de classe de stockage et les tailles de volume persistant pour les pools différents dans le cluster. Par exemple, vous pouvez configurer les volumes persistants déployées pour le pool de stockage à utiliser une classe de stockage différent et disposer d’une capacité plus élevée par le paramètre ci-dessous les variables d’environnement avant de déployer le cluster :

```bash
export STORAGE_POOL_USE_PERSISTENT_VOLUME=true
export STORAGE_POOL_STORAGE_CLASS_NAME=managed-premium
export STORAGE_POOL_STORAGE_SIZE=100Gi
```

Voici une liste complète des variables d’environnement liées à la configuration d’un stockage persistant pour le cluster de données volumineuses de SQL Server :

| Variable d'environnement | Valeur par défaut | Description |
|---|---|---|
| **USE_PERSISTENT_VOLUME** | true | `true` Pour utiliser les revendications de Volume persistant Kubernetes pour le stockage de pod. `false` Pour utiliser le stockage éphémère hôte pour le stockage de pod. |
| **STORAGE_CLASS_NAME** | par défaut | Si `USE_PERSISTENT_VOLUME` est `true` cela indique le nom de la classe de stockage Kubernetes à utiliser. |
| **STORAGE_SIZE** | Gi 6 | Si `USE_PERSISTENT_VOLUME` est `true`, cela indique la taille de volume persistant pour chaque pod. |
| **DATA_POOL_USE_PERSISTENT_VOLUME** | USE_PERSISTENT_VOLUME | `true` Pour utiliser les revendications de Volume persistant Kubernetes pour des pods dans le pool de données. `false` utilisation du stockage de l’hôte éphémère pour pods de pool de données. |
| **DATA_POOL_STORAGE_CLASS_NAME** | STORAGE_CLASS_NAME | Indique le nom de la classe de stockage Kubernetes à utiliser pour les volumes persistants associés de pods de pool de données.|
| **DATA_POOL_STORAGE_SIZE** | STORAGE_SIZE |Indique la taille de volume persistant pour chaque pod dans le pool de données. |
| **STORAGE_POOL_USE_PERSISTENT_VOLUME** | USE_PERSISTENT_VOLUME | `true` Pour utiliser les revendications de Volume persistant Kubernetes pour des pods dans le pool de stockage. `false` utilisation du stockage de l’hôte éphémère pour pods de pool de stockage.|
| **STORAGE_POOL_STORAGE_CLASS_NAME** | STORAGE_CLASS_NAME | Le nom de la classe de stockage à utiliser pour les volumes persistants Kubernetes TIndicates associé à pods de pool de stockage. |
| **STORAGE_POOL_STORAGE_SIZE** | STORAGE_SIZE | Indique la taille de volume persistant pour chaque pod dans le pool de stockage. |

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir une documentation complète sur les volumes dans Kubernetes, consultez le [documentation Kubernetes sur les Volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Pour plus d’informations sur le déploiement de cluster de données volumineux de SQL Server, consultez [le déploiement de SQL Server du cluster big data sur Kubernetes](deployment-guidance.md).

