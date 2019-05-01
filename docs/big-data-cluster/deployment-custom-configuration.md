---
title: Configurer des déploiements
titleSuffix: SQL Server big data clusters
description: Découvrez comment personnaliser un déploiement de cluster de données volumineuses avec des fichiers de configuration.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7dd774d390587d0c2c0248ab9b419ad40f8f212b
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759166"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Configurer les paramètres de déploiement pour les clusters de données volumineuses

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Pour personnaliser votre fichier de configuration de déploiement de cluster, vous pouvez utiliser n’importe quel éditeur de format json comme VSCode. Pour les scripts de ces modifications relatives aux fins d’automatisation, nous fournissons un **section de configuration de cluster mssqlctl** commande. Cet article explique comment configurer des déploiements de cluster big data en modifiant les fichiers de configuration de déploiement. Il fournit des exemples pour savoir comment modifier la configuration pour différents scénarios. Pour plus d’informations sur l’utilisation des fichiers de configuration dans les déploiements, consultez le [déploiement](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Prérequis

- [Installer mssqlctl](deploy-install-mssqlctl.md).

- Chacun des exemples dans cette section supposent que vous avez créé une copie d’un des fichiers de configuration standard. Pour plus d’informations, consultez [créer un fichier de configuration personnalisé](deployment-guidance.md#customconfig). Par exemple, la commande suivante crée un **custom.json** fichier basé sur la valeur par défaut **aks-dev-test.json** configuration :

   ```bash
   mssqlctl cluster config init --src aks-dev-test.json --target custom.json
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
mssqlctl cluster config section set -f custom.json -j ".metadata.name=test-cluster"
```

> [!IMPORTANT]
> Le nom de votre cluster doit être uniquement alphanumériques minuscules, sans espaces. Tous les artefacts de Kubernetes (conteneurs, pods, les jeux avec état, services) pour le cluster seront créées dans un espace de noms avec le même nom que le cluster de nom spécifié.

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
    },
    {
        "name": "AppServiceProxy",
        "serviceType": "LoadBalancer",
        "port": 30778
    },
    {
        "name": "Knox",
        "serviceType": "LoadBalancer",
        "port": 30443
    }
]
```

L’exemple suivant utilise inline JSON pour modifier le port pour le **contrôleur** point de terminaison :

```bash
mssqlctl cluster config section set -f custom.json -j "$.spec.controlPlane.spec.endpoints[?(@.name==""Controller"")].port=30000"
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
                "usePersistentVolume": true,
                "className": "managed-premium",
                "accessMode": "ReadWriteOnce",
                "size": "10Gi"
            }
        }
    }
]
```

Vous pouvez configurer le nombre d’instances dans un pool en modifiant le **réplicas** valeur pour chaque pool. L’exemple suivant utilise inline JSON pour modifier ces valeurs pour les pools de stockage et données `10` et `4` respectivement :

```bash
mssqlctl cluster config section set -f custom.json -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
mssqlctl cluster config section set -f custom.json -j "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4'
```

> [!IMPORTANT]
> Dans cette version, vous ne pouvez pas modifier le nombre d’instances dans le pool de calcul.

## <a id="storage"></a> Configuration du stockage

Vous pouvez également modifier la classe de stockage et les caractéristiques qui sont utilisés pour chaque pool. L’exemple suivant assigne une classe de stockage personnalisé pour le pool de stockage :

```bash
mssqlctl cluster config section set -f custom.json -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec={""replicas"": 2,""storage"": {""className"": ""newStorageClass"",""size"": ""20Gi"",""accessMode"": ""ReadWriteOnce"",""usePersistentVolume"": true},""type"": ""Storage""}"
```

L’exemple suivant met à jour uniquement la taille du pool de stockage pour `32Gi`:

```bash
mssqlctl cluster config section set -f custom.json -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.size=32Gi"
```

L’exemple suivant met à jour la taille de tous les pools de `32Gi`:

```bash
mssqlctl cluster config section set -f custom.json -j "$.spec.pools[?(@.spec.type[*])].spec.storage.size=32Gi"
```

> [!NOTE]
> Un fichier de configuration basé sur **kubeadm-dev-test.json** n’a pas une définition de stockage pour chaque pool, mais cela peut être ajouté manuellement si nécessaire.

Pour plus d’informations sur la configuration du stockage, consultez [persistance des données avec SQL Server du cluster big data sur Kubernetes](concept-data-persistence.md).

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
mssqlctl cluster config section set -f custom.json -p ./patch.json
```

## <a id="jsonpatch"></a> Fichiers du correctif JSON

Fichiers du correctif JSON configurent plusieurs paramètres à la fois. Pour plus d’informations sur les correctifs JSON, consultez [correctifs JSON dans Python](https://github.com/stefankoegl/python-json-patch) et [évaluateur en ligne JSONPath](https://jsonpath.com/).

Ce qui suit **patch.json** fichier effectue les modifications suivantes :

- Met à jour le port du point de terminaison unique.
- Met à jour tous les points de terminaison (**port** et **serviceType**).
- Met à jour le stockage de plan de contrôle.
- Met à jour le nom de classe de stockage dans le stockage de plan de contrôle.
- Mises à jour de pool de stockage, y compris les réplicas (pool de stockage).
- Met à jour les paramètres Spark pour un pool spécifique (pool de stockage).

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
        },
        {
            "serviceType": "LoadBalancer",
            "port": 30778,
            "name": "AppServiceProxy"
        },
        {
            "serviceType": "LoadBalancer",
            "port": 30443,
            "name": "Knox"
        }
      ]
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.storage",
      "value": {
        "usePersistentVolume":true,
        "accessMode":"ReadWriteMany",
        "className":"managed-premium",
        "size":"10Gi"
      }
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.storage.className",
      "value": "default"
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
        "replicas": 2,
        "type": "Storage",
        "storage": {
          "usePersistentVolume": true,
          "accessMode": "ReadWriteOnce",
          "className": "managed-premium",
          "size": "10Gi"
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
    }
  ]
}
```

> [!TIP]
> Pour plus d’informations sur la structure et les options pour modifier un fichier de configuration de déploiement, consultez [référence de fichier de configuration de déploiement pour les clusters de données volumineuses](reference-deployment-config.md).

Utilisez **ensemble de section de configuration de cluster mssqlctl** pour appliquer les modifications dans le fichier de correctif JSON. L’exemple suivant applique le **patch.json** vers un fichier de configuration de déploiement cible **custom.json**.

```bash
mssqlctl cluster config section set -f custom.json -p ./patch.json
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation de fichiers de configuration dans les déploiements de cluster big data, consultez [comment déployer des données volumineuses de SQL Server clusters sur Kubernetes](deployment-guidance.md#configfile).
