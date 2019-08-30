---
title: Configurer des déploiements
titleSuffix: SQL Server big data clusters
description: Découvrez comment personnaliser un déploiement de cluster Big Data avec des fichiers de configuration.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 230ec2300bff55cefbb176c69d677b4e04d6ad30
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155320"
---
# <a name="configure-deployment-settings-for-cluster-resources-and-services"></a>Configurer les paramètres de déploiement pour les services et les ressources de cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

À partir d’un ensemble prédéfini de profils de configuration intégrés à l’outil de gestion azdata, vous pouvez facilement modifier les paramètres par défaut pour mieux répondre aux besoins de votre charge de travail BDC. À partir de la version Release candidate, la structure des fichiers de configuration a été mise à jour pour vous permettre de mettre à jour de façon granulaire les paramètres pour chaque service de la ressource. 

Vous pouvez également définir des configurations au niveau des ressources ou mettre à jour les configurations de tous les services d’une ressource. Voici un résumé de la structure de **BDC. JSON**:

```json
{
    "apiVersion": "v1",
    "metadata": {
        "kind": "BigDataCluster",
        "name": "mssql-cluster"
    },
    "spec": {
        "resources": {
            "nmnode-0": {...
            },
            "sparkhead": {...
            },
            "zookeeper": {...
            },
            "gateway": {...
            },
            "appproxy": {...
            },
            "master": {...
            },
            "compute-0": {...
            },
            "data-0": {...
            },
            "storage-0": {...
        },
        "services": {
            "sql": {
                "resources": [
                    "master",
                    "compute-0",
                    "data-0",
                    "storage-0"
                ]
            },
            "hdfs": {
                "resources": [
                    "nmnode-0",
                    "zookeeper",
                    "storage-0",
                    "sparkhead"
                ],
                "settings": {...
            },
            "spark": {
                "resources": [
                    "sparkhead",
                    "storage-0"
                ],
                "settings": {...
            }
        }
    }
}
```

Pour mettre à jour les configurations au niveau des ressources comme les instances d’un pool, vous devez mettre à jour la spécification de la ressource. Par exemple, pour mettre à jour le nombre d’instances dans le pool de calcul, vous allez modifier cette section dans le fichier de configuration **BDC. JSON** :
```json
"resources": {
    ...
    "compute-0": {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Compute",
            "replicas": 4
        }
    }
    ...
}
``` 

De même, pour modifier les paramètres d’un service authentification unique dans une ressource spécifique. Par exemple, si vous souhaitez modifier les paramètres de mémoire Spark uniquement pour le composant Spark dans le pool de stockage, vous devez mettre à niveau la ressource **Storage-0** avec une section de **paramètres** pour **Spark** service dans le fichier de configuration **BDC. JSON.** .
```json
"resources":{
    ...
     "storage-0": {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Storage",
            "replicas": 2,
            "settings": {
                "spark": {
                    "driverMemory": "2g",
                    "driverCores": "1",
                    "executorInstances": "3",
                    "executorMemory": "1536m",
                    "executorCores": "1"
                }
            }
        }
    }
    ...
}
```

Si vous souhaitez appliquer les mêmes configurations pour un service associé à plusieurs ressources, vous devez mettre à jour les **paramètres** correspondants dans la section **services** . Par exemple, si vous souhaitez définir les mêmes paramètres pour Spark dans le pool de stockage et les pools Spark, vous devez mettre à jour la section des **paramètres** dans la section service **Spark** du fichier de configuration **BDC. JSON** .

```json
"services": {
    ...
    "spark": {
        "resources": [
            "sparkhead",
            "storage-0"
        ],
        "settings": {
            "driverMemory": "2g",
            "driverCores": "1",
            "executorInstances": "3",
            "executorMemory": "1536m",
            "executorCores": "1"
        }
    }
    ...
}
```


Pour personnaliser les fichiers de configuration de vos déploiement de clusters, vous pouvez utiliser n’importe quel éditeur pour le format JSON, comme VSCode. Pour générer un script avec ces modifications à des fins d’automatisation, utilisez la commande **azdata bdc config**. Cet article explique comment configurer des déploiements de clusters Big Data en modifiant les fichiers de configuration du déploiement. Il fournit des exemples de modification de la configuration pour différents scénarios. Pour plus d’informations sur la façon dont les fichiers de configuration sont utilisés dans les déploiements, consultez le [guide de déploiement](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Prérequis

- [Installer azdata](deploy-install-azdata.md).

- Chacun des exemples de cette section suppose que vous avez créé une copie de l’une des configurations standard. Pour plus d’informations, consultez [Créer une configuration personnalisée](deployment-guidance.md#customconfig). Par exemple, la commande suivante crée un répertoire nommé `custom` qui contient deux fichiers de configuration de déploiement JSON, **BDC. JSON** et **Control. JSON**, en fonction de la configuration par défaut de **AKS-dev-test** :

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Changer le nom du cluster

Le nom du cluster est à la fois le nom du cluster Big Data et celui de l’espace de noms Kubernetes qui sera créé lors du déploiement. Elle est spécifiée dans la partie suivante du fichier de configuration du déploiement **BDC. JSON** :

```json
"metadata": {
    "kind": "BigDataCluster",
    "name": "mssql-cluster"
},
```

La commande suivante envoie une paire clé-valeur au paramètre **--json-values** pour changer le nom du cluster Big Data en **test-cluster** :

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Le nom de votre cluster Big Data ne doit contenir que des caractères alphanumériques minuscules et aucun espace. Tous les artefacts Kubernetes (conteneurs, pods, ensembles avec état, services) pour le cluster sont créés dans un espace de noms portant le même nom que le nom de cluster spécifié.

## <a id="ports"></a> Mettre à jour les ports d’un point de terminaison

Les points de terminaison sont définis pour le contrôleur dans le fichier **Control. JSON** et pour la passerelle et SQL Server instance principale dans les sections correspondantes dans **BDC. JSON**. La partie suivante du fichier de configuration **control.json** montre les définitions de point de terminaison pour le contrôleur :

```json
{
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
}
```

L’exemple suivant utilise du JSON inline pour changer le port du point de terminaison du **contrôleur** :

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Configurer des réplicas de pool

Les configurations de chaque ressource, telles que le pool de stockage, sont définies dans le fichier de configuration **BDC. JSON** . Par exemple, la partie suivante du **CDM. JSON** illustre une définition de ressource **Storage-0** :

```json
"storage-0": {
    "metadata": {
        "kind": "Pool",
        "name": "default"
    },
    "spec": {
        "type": "Storage",
        "replicas": 2,
        "settings": {
            "spark": {
                "driverMemory": "2g",
                "driverCores": "1",
                "executorInstances": "3",
                "executorMemory": "1536m",
                "executorCores": "1"
            }
        }
    }
}
```

Vous pouvez configurer le nombre d’instances dans un pool en modifiant la valeur de **replicas** pour chaque pool. L’exemple suivant utilise du JSON inline pour changer ces valeurs pour les pools de stockage et les pools de données respectivement en `10` et en `4` :

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.storage-0.spec.replicas=10"
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.data-0.spec.replicas=4"
```

## <a id="storage"></a> Configurer le stockage

Vous pouvez également changer la classe et les caractéristiques du stockage utilisées pour chaque pool. L’exemple suivant affecte une classe de stockage personnalisée au pool de stockage et met à jour la taille de la revendication de volume persistant pour le stockage de données sur 100 Go. Commencez par créer un fichier patch.json comme ci-dessous, qui comprend la nouvelle section *storage*, en plus de *type* et de *replicas*.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "100Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    }
  ]
}
```

Vous pouvez ensuite utiliser la commande **azdata BDC config patch** pour mettre à jour le fichier de configuration **BDC. JSON** .
```bash
azdata bdc config patch --config-file custom/bdc.json --patch ./patch.json
```

> [!NOTE]
> Un fichier de configuration basé sur **kubeadm-dev-test** n’a pas de définition de stockage pour chaque pool, mais vous pouvez utiliser le processus ci-dessus pour l’ajouter si nécessaire.

Pour plus d’informations sur la configuration du stockage, consultez [Persistance des données avec un cluster Big Data SQL Server sur Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a> Configurer un pool de stockage sans Spark

Vous pouvez également configurer les pools de stockage pour qu’ils s’exécutent sans Spark et créer un pool Spark distinct. Ceci vous permet de mettre à l’échelle la puissance de calcul Spark indépendamment du stockage. Pour plus d’informations sur la configuration du pool Spark, consultez l’[exemple de fichier de correctif JSON](#jsonpatch) à la fin de cet article.


Par défaut, le paramètre **includeSpark** pour la ressource de pool de stockage a la valeur true. vous devez donc modifier le champ **includeSpark** dans la configuration de stockage afin d’apporter des modifications. La commande suivante montre comment modifier cette valeur à l’aide de JSON Inline.

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.storage-0.spec.settings.spark.includeSpark=false"
```

## <a id="podplacement"></a> Configurer le placement des pods avec des étiquettes Kubernetes

Vous pouvez contrôler le placement des pods sur les nœuds Kubernetes qui ont des ressources spécifiques pour prendre en charge différents types d’exigences de charge de travail. Par exemple, vous souhaiterez peut-être vous assurer que les gousses de ressources du pool de stockage sont placées sur des nœuds avec davantage de stockage, ou SQL Server des instances principales sont placées sur des nœuds qui ont des ressources processeur et mémoire supérieures. Dans ce cas, vous allez d’abord créer un cluster Kubernetes hétérogène avec différents types de matériels, puis [affecter les étiquettes de nœud](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) en conséquence. Au moment du déploiement du cluster Big Data, vous pouvez spécifier les mêmes étiquettes au niveau du pool dans le fichier de configuration de déploiement du cluster. Kubernetes prend alors en compte les affinités des pods avec les nœuds qui correspondent aux étiquettes spécifiées. La clé d’étiquette spécifique qui doit être ajoutée aux nœuds du cluster kubernetes est **MSSQL-à l’ensemble du cluster**. La valeur de cette étiquette peut être n’importe quelle chaîne de votre choix.

L’exemple suivant montre comment modifier un fichier de configuration personnalisé pour inclure un paramètre d’étiquette de nœud pour l’instance principale SQL Server, le pool de calcul, le pool de données & pool de stockage. Notez qu’il n’existe pas de clé *nodeLabel* dans les configurations intégrées : vous devez donc modifier manuellement un fichier de configuration personnalisé, ou créer un fichier correctif et l’appliquer au fichier de configuration personnalisé. Le pod d’instance SQL Server Master sera déployé sur un nœud qui contient une étiquette **MSSQL-cluster-global** avec la valeur **BDC-Master**. Les modules de pool de calcul et de pool de données seront déployés sur les nœuds qui contiennent une étiquette **MSSQL-cluster-global** avec la valeur **BDC-SQL**. Les modules de pool de stockage seront déployés sur les nœuds qui contiennent une étiquette **MSSQL-cluster-global** avec la valeur **BDC-Storage**.

Créez un fichier nommé **patch.json** dans votre répertoire actif avec le contenu suivant :

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.master.spec",
      "value": {
        "type": "Master",
        "replicas": 1,
        "endpoints": [
          {
            "name": "Master",
            "serviceType": "NodePort",
            "port": 31433
          }
        ],
        "settings": {
          "sql": {
            "hadr.enabled": "false"
          }
        },
        "nodeLabel": "bdc-master"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.compute-0.spec",
      "value": {
        "type": "Compute",
        "replicas": 1,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.data-0.spec",
      "value": {
        "type": "Data",
        "replicas": 2,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 3,
        "nodeLabel": "bdc-storage",
        "settings": {
          "spark": {
            "includeSpark": "true"
          }
        }
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
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

- Met à jour les paramètres de stockage du pool pour le pool de stockage dans **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "100Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    }
  ]
}
```

- Met à jour les paramètres Spark pour le pool de stockage dans **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.services.spark.settings",
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

- Crée un pool Spark avec 2 instances dans **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "add",
      "path": "spec.resources.spark-0",
      "value": {
        "metadata": {
          "kind": "Pool",
          "name": "default"
        },
        "spec": {
          "type": "Spark",
          "replicas": 2
        }
      }
    },
    {
      "op": "add",
      "path": "spec.services.spark.resources/-",
      "value": "spark-0"
    },
    {
      "op": "add",
      "path": "spec.services.hdfs.resources/-",
      "value": "spark-0"
    },
    {
      "op": "add",
      "path": "spec.services.spark.settings",
      "value": {
        "DriverMemory": "2g",
        "DriverCores": "1",
        "ExecutorInstances": "2",
        "ExecutorMemory": "2g",
        "ExecutorCores": "1"
      }
    }
  ]
}
```

> [!TIP]
> Pour plus d’informations sur la structure et les options de modification d’un fichier de configuration de déploiement, consultez [Informations de référence sur les fichiers de configuration de déploiement des clusters Big Data](reference-deployment-config.md).

Utilisez les commandes **azdata bdc config** pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le fichier **patch. JSON** à un fichier de configuration de déploiement cible **Custom/BDC. JSON**.

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
```

## <a name="disable-elasticsearch-to-run-in-privileged-mode"></a>Désactiver ElasticSearch pour qu’il s’exécute en mode privilégié
Par défaut, le conteneur ElasticSearch s’exécute en mode privilège dans Big Data cluster. Cela permet de s’assurer qu’au moment de l’initialisation du conteneur, le conteneur dispose des autorisations suffisantes pour mettre à jour un paramètre sur l’ordinateur hôte, lorsque ElasticSearch traite une quantité plus importante de journaux. Vous trouverez plus d’informations sur cette rubrique dans [cet article](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html). 

Pour désactiver le conteneur qui exécute ElasticSearch pour qu’il s’exécute en mode privilégié, vous devez mettre à jour la section des **paramètres** dans **Control. JSON** et spécifier la valeur de **VM. Max _map_count** à **-1**. Voici un exemple de la façon dont cette section doit ressembler à ce qui suit:
```json
"settings": {
    "ElasticSearch": {
        "vm.max_map_count": "-1"
      }
}
```

Vous pouvez modifier le fichier **Control. JSON** et ajouter la section ci-dessus à la **spécification**, ou vous pouvez créer un fichier correctif **elasticsearch-patch. JSON** comme ci-dessous et utiliser **azdata** CLI pour corriger le fichier **config. JSON** :

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec",
      "value": {
        "docker": {
            "registry": "mcr.microsoft.com",
            "repository": "mssql/bdc",
            "imageTag": "2019-RC1-ubuntu",
            "imagePullPolicy": "Always"
        },
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
        ],
        "settings": {
            "ElasticSearch": {
                "vm.max_map_count": "-1"
             }
        }
       }
    }
  ]
}
```

Exécutez cette commande pour corriger le fichier de configuration:
```
azdata bdc config patch --config-file control.json --patch-file elasticsearch-patch.json
```

> [!IMPORTANT]
> Nous vous recommandons de mettre à jour manuellement le paramètre **max_map_count** manuellement sur chaque ordinateur hôte dans le cluster Kubernetes, en suivant les instructions de [cet article](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html).
## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation des fichiers de configuration dans Big Data les déploiements de cluster, voir [How to deploy [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] on Kubernetes](deployment-guidance.md#configfile).
