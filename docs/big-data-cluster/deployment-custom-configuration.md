---
title: Configurer les déploiements
titleSuffix: SQL Server big data clusters
description: Découvrez comment personnaliser un déploiement de cluster Big Data à l’aide de fichiers de configuration.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7559ecf9c7b17ca21c088ed531a347f88e89ee2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419437"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Configurer les paramètres de déploiement pour les clusters Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Pour personnaliser vos fichiers de configuration de déploiement de cluster, vous pouvez utiliser n’importe quel éditeur de format JSON, tel que VSCode. Pour générer un script de ces modifications à des fins d’automatisation, utilisez la commande **azdata BDC config** . Cet article explique comment configurer les déploiements de cluster Big Data en modifiant les fichiers de configuration de déploiement. Il fournit des exemples de modification de la configuration pour différents scénarios. Pour plus d’informations sur la façon dont les fichiers de configuration sont utilisés dans les déploiements, consultez le [Guide de déploiement](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Prérequis

- [Installez azdata](deploy-install-azdata.md).

- Chacun des exemples de cette section suppose que vous avez créé une copie de l’une des configurations standard. Pour plus d’informations, consultez [créer une configuration personnalisée](deployment-guidance.md#customconfig). Par exemple, la commande suivante crée un répertoire nommé `custom` qui contient deux fichiers de configuration de déploiement JSON, **cluster. JSON** et **Control. JSON**, en fonction de la configuration par défaut de **AKS-dev-test** :

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a>Modifier le nom du cluster

Le nom du cluster est à la fois le nom du cluster Big Data et l’espace de noms Kubernetes qui sera créé lors du déploiement. Elle est spécifiée dans la partie suivante du fichier de configuration du déploiement de **cluster. JSON** :

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

La commande suivante envoie une paire clé-valeur au paramètre **--JSON-** values pour modifier le nom du cluster Big Data en **test-cluster**:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Le nom de votre cluster Big Data ne doit contenir que des caractères alphanumériques en minuscules, sans espaces. Tous les artefacts Kubernetes (conteneurs, Pod, sans sets, services) du cluster sont créés dans un espace de noms portant le même nom que le nom de cluster spécifié.

## <a id="ports"></a>Mettre à jour les ports de point de terminaison

Les points de terminaison sont définis pour le contrôleur dans **Control. JSON** et pour la passerelle et SQL Server instance principale dans les sections correspondantes dans **cluster. JSON**. La partie suivante du fichier de configuration **Control. JSON** montre les définitions de point de terminaison pour le contrôleur:

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

L’exemple suivant utilise JSON Inline pour modifier le port du point de terminaison du **contrôleur** :

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a>Configurer des réplicas de pool

Les caractéristiques de chaque pool, telles que le pool de stockage, sont définies dans le fichier de configuration **cluster. JSON** . Par exemple, la partie suivante du **cluster. JSON** illustre une définition de pool de stockage:

```json
"pools": [
   {
       "metadata": {
           "kind": "Pool",
           "name": "default"
       },
       "spec": {
           "type": "Storage",
           "replicas": 2
       }
   }
]
```

Vous pouvez configurer le nombre d’instances dans un pool en modifiant la valeur  des réplicas pour chaque pool. L’exemple suivant utilise JSON Inline pour modifier ces valeurs pour les pools de stockage et `10` de `4` données sur et respectivement:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a>Configurer le stockage

Vous pouvez également modifier la classe de stockage et les caractéristiques utilisées pour chaque pool. L’exemple suivant affecte une classe de stockage personnalisée au pool de stockage et met à jour la taille de la revendication de volume persistant pour le stockage de données sur 100 Go. Commencez par créer un fichier patch. JSON comme indiqué ci-dessous, qui comprend la nouvelle section de *stockage* , en plus du *type* et des réplicas.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
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
                },
        "type":"Storage",
        "replicas":2
      }
    }
  ]
}
```

Vous pouvez ensuite utiliser la commande **azdata BDC config patch** pour mettre à jour le fichier de configuration **cluster. JSON** .
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> Un fichier de configuration basé sur **kubeadm-dev-test** n’a pas de définition de stockage pour chaque pool, mais vous pouvez utiliser le processus ci-dessus pour ajouter si nécessaire.

Pour plus d’informations sur la configuration du stockage, consultez [persistance des données avec SQL Server cluster Big Data sur Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a>Configurer un pool de stockage sans Spark

Vous pouvez également configurer les pools de stockage à exécuter sans Spark et créer un pool Spark distinct. Cela vous permet de mettre à l’échelle la puissance de calcul Spark indépendamment du stockage. Pour savoir comment configurer le pool Spark, consultez l' [exemple de fichier de correctif JSON](#jsonpatch) à la fin de cet article.



Par défaut, le paramètre **includeSpark** du pool de stockage a la valeur true. vous devez donc ajouter le champ **includeSpark** dans la configuration de stockage pour apporter des modifications. Le fichier de correctif JSON suivant montre comment ajouter ce.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
        "type":"Storage",
        "replicas":2,
        "includeSpark":false
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

## <a id="podplacement"></a>Configurer le placement de Pod à l’aide d’étiquettes Kubernetes

Vous pouvez contrôler le placement de Pod sur des nœuds Kubernetes qui ont des ressources spécifiques pour prendre en charge différents types d’exigences de charge de travail. Par exemple, vous souhaiterez peut-être vous assurer que les gousses de pool de stockage sont placées sur des nœuds avec davantage de stockage, ou SQL Server des instances principales sont placées sur des nœuds qui ont des ressources processeur et mémoire supérieures. Dans ce cas, vous allez d’abord créer un cluster Kubernetes hétérogène avec différents types de matériel, puis [affecter des étiquettes de nœud](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) en conséquence. Au moment du déploiement de Big Data cluster, vous pouvez spécifier les mêmes étiquettes au niveau du pool dans le fichier de configuration du déploiement de cluster. Kubernetes prend ensuite soin de affinage les pod sur les nœuds qui correspondent aux étiquettes spécifiées.

L’exemple suivant montre comment modifier un fichier de configuration personnalisé pour inclure un paramètre d’étiquette de nœud pour l’instance maître SQL Server. Notez qu’il n’existe aucune clé *nodeLabel* dans les configurations intégrées. vous devez donc modifier un fichier de configuration personnalisé manuellement ou créer un fichier correctif et l’appliquer au fichier de configuration personnalisé.

Créez un fichier nommé **patch. JSON** dans votre répertoire actif avec le contenu suivant:

```json
{
  "patch": [
     {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Master')].spec",
      "value": {
           "type": "Master",
         "replicas": 1,
         "hadrEnabled": false,
         "endpoints": [
            {
             "name": "Master",
             "serviceType": "NodePort",
             "port": 31433
            }
          ],
         "nodeLabel": "<yourNodeLabel>"
       }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a id="jsonpatch"></a>Fichiers de correctifs JSON

Les fichiers de correctif JSON configurent plusieurs paramètres à la fois. Pour plus d’informations sur les correctifs JSON, consultez [correctifs JSON dans python](https://github.com/stefankoegl/python-json-patch) et l' [évaluateur JSONPath Online](https://jsonpath.com/).

Le fichier **patch. JSON** suivant effectue les modifications suivantes:

- Met à jour le port d’un point de terminaison unique dans **Control. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.endpoints[?(@.name=='Controller')].port",
          "value": 30000
        }   
      ]
    }
    ```

- Met à jour tous les points de terminaison (**port** et **serviceType**) dans **Control. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.endpoints",
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
        }
      ]
    }
    ```

- Met à jour les paramètres de stockage du contrôleur dans **Control. JSON**. Ces paramètres s’appliquent à tous les composants de cluster, sauf s’ils sont remplacés au niveau du pool.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage",
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
        }   
      ]
    }
    ```

- Met à jour le nom de la classe de stockage dans **Control. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage.data.className",
          "value": "managed-premium"
        }   
      ]
    }
    ```

- Met à jour les paramètres de stockage du pool pour le pool de stockage dans **cluster. JSON**.
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

- Met à jour les paramètres Spark pour le pool de stockage dans **cluster. JSON**.
    ```json
    {
      "patch": [
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
        }   
      ]
    }
    ```

- Crée un pool Spark avec 2 instances dans **cluster. JSON**.
    ```json
    {
      "patch": [
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
> Pour plus d’informations sur la structure et les options de modification d’un fichier de configuration de déploiement, consultez [référence de fichier de configuration de déploiement pour les clusters Big Data](reference-deployment-config.md).

Utilisez les commandes de **configuration azdata BDC** pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le fichier **patch. JSON** à un fichier de configuration de déploiement cible **Custom/cluster. JSON**.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation de fichiers de configuration dans des déploiements de cluster Big Data, consultez [comment déployer des clusters Big Data SQL Server sur Kubernetes](deployment-guidance.md#configfile).
