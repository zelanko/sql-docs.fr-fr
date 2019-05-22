---
title: référence de section de configuration de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de section de configuration de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8239367b45ac327abde919910ccc1336ebb8f5b1
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993350"
---
# <a name="mssqlctl-cluster-config-section"></a>Section de la configuration de cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **section de configuration de cluster** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[afficher de section de configuration de cluster mssqlctl](#mssqlctl-cluster-config-section-show) | Obtient une section à partir d’un fichier de configuration.
[mssqlctl cluster config section set](#mssqlctl-cluster-config-section-set) | Définit une section d’un fichier de configuration.
## <a name="mssqlctl-cluster-config-section-show"></a>afficher de section de configuration de cluster mssqlctl
Obtient la section spécifiée à partir du fichier de configuration sélectionné selon le chemin d’accès json donnée.
```bash
mssqlctl cluster config section show --json-path -j 
                                     --config-file -c  
                                     [--target -t]  
                                     [--force -f]
```
### <a name="examples"></a>Exemples
Obtient une valeur à la fin d’un chemin de clé json simple.
```bash
mssqlctl cluster config section show --config-file custom-config.json --json-path 'metadata.name' --target section.json
```
Obtient une valeur à la fin d’un chemin de clé json avec un conditionnel
```bash
mssqlctl cluster config section show --config-file custom-config.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--json-path -j`
Le chemin de clé json qui mène à la section ou la valeur du fichier de configuration, par exemple, key1.key2.key3. Utilise le langage de requête jsonpath, https://github.com/h2non/jsonpath-ng, par exemple : -j ' $. spec.pools [ ? () @.spec.type == « Master »)]... points de terminaison
#### `--config-file -c`
Chemin d’accès du fichier de configuration de cluster.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Chemin d’accès de l’emplacement où vous souhaitez la section du fichier placé. Par défaut : dirigé vers stdout.
#### `--force -f`
Forcer le remplacement du fichier cible.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.
## <a name="mssqlctl-cluster-config-section-set"></a>ensemble de section de configuration de cluster mssqlctl
Définit la section spécifiée dans le fichier de configuration sélectionné en fonction du chemin d’accès json donnée.  Tous les examplesbelow sont indiqués dans Bash.  Si vous utilisez une autre ligne de commande, sachez que vous devrez peut-être escapequotations en conséquence.  Vous pouvez également utiliser la fonctionnalité fichiers de correctifs.
```bash
mssqlctl cluster config section set --config-file -c 
                                    [--json-values -j]  
                                    [--patch-file -p]
```
### <a name="examples"></a>Exemples
Par exemple, 1 (inline) - définir le port d’un point de terminaison unique (point de terminaison du contrôleur).
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values '$.spec.controlPlane.spec.endpoints[?(@.name=="Controller")].port=30080'
```
Par exemple, 1 (patch) - définir le port d’un point de terminaison unique (point de terminaison du contrôleur) avec le fichier correctif.
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
Par exemple, 2 (inline) - stockage de plan de contrôle de jeu.
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values 'spec.controlPlane.spec.storage=spec.controlPlane.spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
Par exemple, 2 (patch) - stockage de plan de contrôle de jeu avec le fichier correctif.
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"spec.controlPlane.spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Ex 3(inline) - définir un stockage de pool, y compris les réplicas (Pool de stockage).
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
Ex 3 (patch) - définir un stockage de pool, y compris les réplicas (Pool de stockage) avec le fichier correctif.
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--config-file -c`
Chemin de fichier de configuration de cluster de la configuration que vous souhaitez définir
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--json-values -j`
Une liste de paires de valeur de clé des chemins d’accès json aux valeurs : key1.subkey1=value1,key2.subkey2=value2. Vous pouvez fournir inline valeurs json tel que : clé ='{« kind » : « cluster », « name » : « test-cluster »}' ou fournissez un chemin d’accès de fichier, telles que key=./values.json. Si vous souhaitez définir une valeur qui nécessite un conditionnel, utilisez la notation jsonpath par au début de votre chemin d’accès par le symbole $. Ainsi, vous permettent d’effectuer un conditionnel telles que j-$. key1.key2 [ ? () @.key3== 'someValue'] .key4 = value. Vous pouvez voir les exemples ci-dessous. Pour plus d’aide, consultez : https://jsonpath.com/
#### `--patch-file -p`
Chemin d’accès à un fichier json de correctif qui est basée sur la bibliothèque jsonpatch : http://jsonpatch.com/. Vous devez démarrer votre fichier json de correctif avec une clé appelée « patch », dont la valeur est un tableau d’opérations de correction destinées. Pour le chemin d’accès d’une opération de correctif logiciel, vous pouvez utiliser la notation à points, tels que key1.key2 pour la plupart des opérations. Si vous souhaitez effectuer une opération de remplacement, et que vous remplacez une valeur dans un tableau qui requiert un conditionnel, utilisez la notation jsonpath par au début de votre chemin d’accès par le symbole $. Ainsi, vous permettent d’effectuer un conditionnel telles que $. key1.key2 [ ? () @.key3== 'someValue'] .key4. Consultez les exemples ci-dessous. Pour plus d’aide, consultez : https://jsonpath.com/.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).