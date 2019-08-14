---
title: Configurer des déploiements
titleSuffix: SQL Server big data clusters
description: Découvrez comment personnaliser un déploiement de cluster Big Data avec des fichiers de configuration.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7d04df5bf881f285ab28508443fbf0ce1056fada
ms.sourcegitcommit: 316c25fe7465b35884f72928e91c11eea69984d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68969492"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Configurer les paramètres de déploiement de clusters Big Data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Pour personnaliser les fichiers de configuration de vos déploiement de clusters, vous pouvez utiliser n’importe quel éditeur pour le format JSON, comme VSCode. Pour générer un script avec ces modifications à des fins d’automatisation, utilisez la commande **azdata bdc config**. Cet article explique comment configurer des déploiements de clusters Big Data en modifiant les fichiers de configuration du déploiement. Il fournit des exemples de modification de la configuration pour différents scénarios. Pour plus d’informations sur la façon dont les fichiers de configuration sont utilisés dans les déploiements, consultez le [guide de déploiement](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Prérequis

- [Installer azdata](deploy-install-azdata.md).

- Chacun des exemples de cette section suppose que vous avez créé une copie de l’une des configurations standard. Pour plus d’informations, consultez [Créer une configuration personnalisée](deployment-guidance.md#customconfig). Par exemple, la commande suivante crée un répertoire appelé `custom`, qui contient deux fichiers de configuration de déploiement JSON, **cluster.json** et **control.json**, basés sur la configuration de **aks-dev-test** par défaut :

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Changer le nom du cluster

Le nom du cluster est à la fois le nom du cluster Big Data et celui de l’espace de noms Kubernetes qui sera créé lors du déploiement. Elle est spécifié dans la partie suivante du fichier de configuration du déploiement **cluster.json** :

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

La commande suivante envoie une paire clé-valeur au paramètre **--json-values** pour changer le nom du cluster Big Data en **test-cluster** :

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Le nom de votre cluster Big Data ne doit contenir que des caractères alphanumériques minuscules et aucun espace. Tous les artefacts Kubernetes (conteneurs, pods, ensembles avec état, services) pour le cluster sont créés dans un espace de noms portant le même nom que le nom de cluster spécifié.

## <a id="ports"></a> Mettre à jour les ports d’un point de terminaison

Les points de terminaison sont définis pour le contrôleur dans **control.json**, et pour la passerelle et l’instance principale SQL Server, dans les sections correspondantes de **cluster.json**. La partie suivante du fichier de configuration **control.json** montre les définitions de point de terminaison pour le contrôleur :

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

L’exemple suivant utilise du JSON inline pour changer le port du point de terminaison du **contrôleur** :

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Configurer des réplicas de pool

Les caractéristiques de chaque pool, comme le pool de stockage, sont définies dans le fichier de configuration **cluster.json**. Par exemple, la partie suivante de **cluster.json** montre une définition de pool de stockage :

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

Vous pouvez configurer le nombre d’instances dans un pool en modifiant la valeur de **replicas** pour chaque pool. L’exemple suivant utilise du JSON inline pour changer ces valeurs pour les pools de stockage et les pools de données respectivement en `10` et en `4` :

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a> Configurer le stockage

Vous pouvez également changer la classe et les caractéristiques du stockage utilisées pour chaque pool. L’exemple suivant affecte une classe de stockage personnalisée au pool de stockage et met à jour la taille de la revendication de volume persistant pour le stockage de données sur 100 Go. Commencez par créer un fichier patch.json comme ci-dessous, qui comprend la nouvelle section *storage*, en plus de *type* et de *replicas*.

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

Vous pouvez ensuite utiliser la commande **azdata bdc config patch** pour mettre à jour le fichier de configuration **cluster.json**.
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> Un fichier de configuration basé sur **kubeadm-dev-test** n’a pas de définition de stockage pour chaque pool, mais vous pouvez utiliser le processus ci-dessus pour l’ajouter si nécessaire.

Pour plus d’informations sur la configuration du stockage, consultez [Persistance des données avec un cluster Big Data SQL Server sur Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a> Configurer un pool de stockage sans Spark

Vous pouvez également configurer les pools de stockage pour qu’ils s’exécutent sans Spark et créer un pool Spark distinct. Ceci vous permet de mettre à l’échelle la puissance de calcul Spark indépendamment du stockage. Pour plus d’informations sur la configuration du pool Spark, consultez l’[exemple de fichier de correctif JSON](#jsonpatch) à la fin de cet article.



Par défaut, le paramètre **includeSpark** du pool de stockage est défini sur true : vous devez donc ajouter le champ **includeSpark** dans la configuration de stockage pour apporter des modifications. Le fichier de correctif JSON suivant montre comment l’ajouter.

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

## <a id="podplacement"></a> Configurer le placement des pods avec des étiquettes Kubernetes

Vous pouvez contrôler le placement des pods sur les nœuds Kubernetes qui ont des ressources spécifiques pour prendre en charge différents types d’exigences de charge de travail. Par exemple, vous pouvez vérifier que les pods des pools de stockage sont placés sur les nœuds qui ont le plus de stockage, ou que les instances principales SQL Server sont placées sur les nœuds qui ont des ressources processeur et mémoire plus importantes. Dans ce cas, vous allez d’abord créer un cluster Kubernetes hétérogène avec différents types de matériels, puis [affecter les étiquettes de nœud](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) en conséquence. Au moment du déploiement du cluster Big Data, vous pouvez spécifier les mêmes étiquettes au niveau du pool dans le fichier de configuration de déploiement du cluster. Kubernetes prend alors en compte les affinités des pods avec les nœuds qui correspondent aux étiquettes spécifiées. La clé d’étiquette spécifique qui doit être ajoutée aux nœuds du cluster kubernetes est **MSSQL-à l’ensemble du cluster**. La valeur de cette étiquette peut être n’importe quelle chaîne de votre choix.

L’exemple suivant montre comment modifier un fichier de configuration personnalisé pour inclure un paramètre d’étiquette de nœud pour l’instance principale SQL Server, le pool de calcul, le pool de données & pool de stockage. Notez qu’il n’existe pas de clé *nodeLabel* dans les configurations intégrées : vous devez donc modifier manuellement un fichier de configuration personnalisé, ou créer un fichier correctif et l’appliquer au fichier de configuration personnalisé. Le pod d’instance SQL Server Master sera déployé sur un nœud qui contient une étiquette **MSSQL-cluster-global** avec la valeur **BDC-Master**. Les modules de pool de calcul et de pool de données seront déployés sur les nœuds qui contiennent une étiquette **MSSQL-cluster-global** avec la valeur **BDC-SQL**. Les modules de pool de stockage seront déployés sur les nœuds qui contiennent une étiquette **MSSQL-cluster-global** avec la valeur **BDC-Storage**.

Créez un fichier nommé **patch.json** dans votre répertoire actif avec le contenu suivant :

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
        "nodeLabel": "bdc-master"
      }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Compute')].spec",
      "value": {
    "type": "Compute",
        "replicas": 1,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Data')].spec",
      "value": {
    "type": "Data",
        "replicas": 2,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
    "type": "Storage",
        "replicas": 3,
        "nodeLabel": "bdc-storage"
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a id="jsonpatch"></a> Fichiers de correctif JSON

Les fichiers de correctif JSON configurent plusieurs paramètres à la fois. Pour plus d’informations sur les correctifs JSON, consultez [Correctifs JSON dans Python](https://github.com/stefankoegl/python-json-patch) et l’[évaluateur en ligne JSONPath](https://jsonpath.com/).

Le fichier **patch.json** suivant effectue les modifications suivantes :

- Met à jour le port d’un point de terminaison dans **control.json**.
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

- Met à jour tous les points de terminaison (**port** et **serviceType**) dans **control.json**.
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

- Met à jour les paramètres de stockage du contrôleur dans **control.json**. Ces paramètres s’appliquent à tous les composants du cluster, sauf s’ils sont remplacés au niveau du pool.
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

- Met à jour le nom de la classe de stockage dans **control.json**.
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

- Met à jour les paramètres de stockage du pool pour le pool de stockage dans **cluster.json**.
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

- Met à jour les paramètres Spark pour le pool de stockage dans **cluster.json**.
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

- Crée un pool Spark avec 2 instances dans **cluster.json**.
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
> Pour plus d’informations sur la structure et les options de modification d’un fichier de configuration de déploiement, consultez [Informations de référence sur les fichiers de configuration de déploiement des clusters Big Data](reference-deployment-config.md).

Utilisez les commandes **azdata bdc config** pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le fichier **patch.json** à un fichier de configuration de déploiement cible **custom/cluster.json**.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation de fichiers de configuration dans le déploiement de clusters Big Data, consultez [Guide pratique pour déployer des clusters Big Data SQL Server sur Kubernetes](deployment-guidance.md#configfile).
