---
title: Configurer des déploiements
titleSuffix: SQL Server big data clusters
description: Découvrez comment personnaliser un déploiement de cluster de données volumineuses avec des fichiers de configuration.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 19654422bcc57f2ad00b9ab8170d163f848f188b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728885"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Configurer les paramètres de déploiement pour les clusters de données volumineuses

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Pour personnaliser votre fichier de configuration de déploiement de cluster, vous pouvez utiliser n’importe quel éditeur de format JSON, tels que VSCode. Pour les scripts de ces modifications relatives aux fins d’automatisation, utilisez le **mssqlctl bdc configuration section** commande. Cet article explique comment configurer des déploiements de cluster big data en modifiant les fichiers de configuration de déploiement. Il fournit des exemples pour savoir comment modifier la configuration pour différents scénarios. Pour plus d’informations sur l’utilisation des fichiers de configuration dans les déploiements, consultez le [déploiement](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Prérequis

- [Installer mssqlctl](deploy-install-mssqlctl.md).

- Chacun des exemples dans cette section supposent que vous avez créé une copie d’un des fichiers de configuration standard. Pour plus d’informations, consultez [créer un fichier de configuration personnalisé](deployment-guidance.md#customconfig). Par exemple, la commande suivante crée un répertoire appelé `custom` qui contient un fichier de configuration de déploiement JSON basé sur la valeur par défaut **aks-dev-test** configuration :

   ```bash
   mssqlctl bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Modifier le nom de cluster

Le nom du cluster est à la fois le nom du cluster big data et l’espace de noms Kubernetes qui va être créé sur le déploiement. Elle est spécifiée dans la partie suivante du fichier de configuration de déploiement :

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

La commande suivante envoie une paire clé-valeur à la **--json-valeurs** paramètre pour modifier le nom de cluster de données volumineuses à **test-cluster**:

```bash
mssqlctl bdc config section set --config-profile custom -j "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Le nom de votre cluster big data doit être uniquement alphanumériques minuscules, sans espaces. Tous les artefacts de Kubernetes (conteneurs, pods, les jeux avec état, services) pour le cluster seront créées dans un espace de noms avec le même nom que le cluster de nom spécifié.

## <a id="ports"></a> Ports de point de terminaison de mise à jour

Points de terminaison sont définis pour le plan de contrôle, ainsi que pour les pools individuels. La partie suivante du fichier de configuration montre des définitions de point de terminaison pour le plan de contrôle :

```json
"endpoints": [
    {
        "name": "Controller",
        "serviceType": "LoadBalancer",
        "port": 30080
    },
    {
        "name": "ServiceProxy",
        "serviceType": "LoadBalancer",
        "port": 30777
    }
]
```

L’exemple suivant utilise inline JSON pour modifier le port pour le **contrôleur** point de terminaison :

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Configurer des réplicas de pool

Les caractéristiques de chaque pool, tels que le pool de stockage, est défini dans le fichier de configuration. Par exemple, la partie suivante montre une définition de pool de stockage :

```json
"pools": [
    {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Storage",
            "replicas": 2,
            "storage": {
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
           },
        }
    }
]
```

Vous pouvez configurer le nombre d’instances dans un pool en modifiant le **réplicas** valeur pour chaque pool. L’exemple suivant utilise inline JSON pour modifier ces valeurs pour les pools de stockage et données `10` et `4` respectivement :

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a> Configuration du stockage

Vous pouvez également modifier la classe de stockage et les caractéristiques qui sont utilisés pour chaque pool. L’exemple suivant assigne une classe de stockage personnalisés pour le pool de stockage et met à jour de la taille de la revendication de volume persistant pour le stockage des données à 100 Go. Vous devez disposer de cette section du fichier de configuration pour mettre à jour les paramètres à l’aide de la *mssqlctl bdc config set* de commande, voir ci-dessous comment utiliser un fichier de correctif pour ajouter cette section :

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.className=storage-pool-class"
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.size=32Gi"
```

> [!NOTE]
> Un fichier de configuration basé sur **kubeadm-dev-test** n’a pas une définition de stockage pour chaque pool, mais cela peut être ajouté manuellement si nécessaire.

Pour plus d’informations sur la configuration du stockage, consultez [persistance des données avec SQL Server du cluster big data sur Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a> Configurer le stockage sans spark

Vous pouvez également configurer les pools de stockage pour s’exécuter sans spark et créer un pool distinct spark. Cela vous permet de mettre à l’échelle spark calcul power indépendant du stockage. Pour voir comment configurer le pool de spark, consultez le [exemple de fichier de correctif JSON](#jsonpatch) à la fin de cet article.

Vous devez disposer de cette section du fichier de configuration pour mettre à jour les paramètres à l’aide de la `mssqlctl cluster config set command`. Le fichier de correctif JSON suivant montre comment ajouter cela.

Par défaut, le **includeSpark** définition pour le pool de stockage est défini sur true, vous devez donc ajouter la **includeSpark** champ dans la configuration du stockage pour apporter des modifications :

```bash
mssqlctl cluster config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].includeSpark=false"
```

## <a id="podplacement"></a> Configurer le placement de pod à l’aide des étiquettes de Kubernetes

Vous pouvez contrôler le placement de pod sur les nœuds Kubernetes qui ont des ressources spécifiques pour prendre en charge différents types de charges de travail. Par exemple, vous pouvez souhaiter vérifier les pods de pool de stockage sont placés sur les nœuds avec plus de stockage, ou instances principales de SQL Server sont placés sur les nœuds qui ont des ressources mémoire et processeur plus. Dans ce cas, vous devez générer un cluster Kubernetes hétérogène avec différents types de matériel, puis [affecter des étiquettes de nœud](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) en conséquence. Au moment du déploiement de cluster de données volumineux, vous pouvez spécifier des étiquettes mêmes au niveau du pool dans le fichier de configuration de déploiement de cluster. Kubernetes se charge ensuite d’affinage des pods sur les nœuds qui correspondent les labels spécifiés.

L’exemple suivant montre comment modifier un fichier de configuration personnalisée pour inclure un paramètre d’étiquette de nœud pour l’instance principale de SQL Server. Notez qu’il existe aucune *NodeLabel ne* clés dans les configurations intégrées, donc vous devrez soit modifier manuellement un fichier de configuration personnalisée ou créer un fichier de correctif et l’appliquer au fichier de configuration personnalisé.

Créez un fichier nommé **patch.json** dans votre répertoire actuel avec le contenu suivant :

```json
{
  "patch": [
     {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Master')].spec",
      "value": {
      "nodeLabel": "<yourNodeLabel>"
       }
    }
  ]
}
```

```bash
mssqlctl bdc config section set --config-profile custom -p ./patch.json
```

## <a id="jsonpatch"></a> Fichiers du correctif JSON

Fichiers du correctif JSON configurent plusieurs paramètres à la fois. Pour plus d’informations sur les correctifs JSON, consultez [correctifs JSON dans Python](https://github.com/stefankoegl/python-json-patch) et [évaluateur en ligne JSONPath](https://jsonpath.com/).

Ce qui suit **patch.json** fichier effectue les modifications suivantes :

- Met à jour le port du point de terminaison unique.
- Met à jour tous les points de terminaison (**port** et **serviceType**).
- Met à jour le stockage de plan de contrôle. Ces paramètres s’appliquent à tous les composants de cluster, sauf substitution au niveau du pool.
- Met à jour le nom de classe de stockage dans le stockage de plan de contrôle.
- Met à jour les paramètres du pool de stockage pour le pool de stockage.
- Met à jour les paramètres Spark pour le pool de stockage.
- Crée un pool de spark avec 2 réplicas pour le cluster

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port",
      "value": 30000
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.endpoints",
      "value": [
        {
          "serviceType": "LoadBalancer",
          "port": 30001,
          "name": "Controller"
        },
        {
            "serviceType": "LoadBalancer",
            "port": 30778,
            "name": "ServiceProxy"
        }
      ]
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.controlPlane",
      "value": {
          "data": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.storage.data.className",
      "value": "managed-premium"
    },
    {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage",
      "value": {
          "data": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].hadoop.spark",
      "value": {
        "driverMemory": "2g",
        "driverCores": 1,
        "executorInstances": 3,
        "executorCores": 1,
        "executorMemory": "1536m"
      }
    },
    {
      "op": "add",
      "path": "spec.pools/-",
      "value":
      {
        "metadata": {
          "kind": "Pool",
          "name": "default"
        },
        "spec": {
          "type": "Spark",
          "replicas": 2
        },
        "hadoop": {
          "yarn": {
            "nodeManager": {
              "memory": 12288,
              "vcores": 6
            },
            "schedulerMax": {
              "memory": 12288,
              "vcores": 6
            },
            "capacityScheduler": {
              "maxAmPercent": 0.3
            }
          },
          "spark": {
            "driverMemory": "2g",
            "driverCores": 1,
            "executorInstances": 2,
            "executorMemory": "2g",
            "executorCores": 1
          }
        }
      }
    }   
  ]
}
```

> [!TIP]
> Pour plus d’informations sur la structure et les options pour modifier un fichier de configuration de déploiement, consultez [référence de fichier de configuration de déploiement pour les clusters de données volumineuses](reference-deployment-config.md).

Utilisez **mssqlctl bdc configuration section défini** pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le **patch.json** vers un fichier de configuration de déploiement cible **custom.json**.

```bash
mssqlctl bdc config section set --config-profile custom -p ./patch.json
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation de fichiers de configuration dans les déploiements de cluster big data, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md#configfile).
