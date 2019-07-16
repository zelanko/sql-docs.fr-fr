---
title: référence de section de configuration de bdc mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de section config mssqlctl bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3f3ba7854b4df63495926e4cc207de7cbe6a9378
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958190"
---
# <a name="mssqlctl-bdc-config-section"></a>mssqlctl bdc config section

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **section de configuration bdc** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[afficher de section config mssqlctl bdc](#mssqlctl-bdc-config-section-show) | Obtient une section d’un profil de configuration.
[section de configuration mssqlctl bdc défini](#mssqlctl-bdc-config-section-set) | Définit une section pour un profil de configuration.
## <a name="mssqlctl-bdc-config-section-show"></a>afficher de section config mssqlctl bdc
Obtient la section spécifiée à partir du profil de configuration sélectionné selon le chemin d’accès json donnée.
```bash
mssqlctl bdc config section show --json-path -j 
                                 --config-profile -c  
                                 [--target -t]  
                                 [--force -f]
```
### <a name="examples"></a>Exemples
Obtient une valeur à la fin d’un chemin de clé json simple.
```bash
mssqlctl bdc config section show --config-profile custom-config --json-path 'metadata.name' --target section.json
```
Obtient une valeur à la fin d’un chemin de clé json avec un conditionnel
```bash
mssqlctl bdc config section show --config-profile custom-config  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--json-path -j`
Le chemin de clé json qui mène à la section ou la valeur à partir du fichier de cluster.json du profil de configuration, par exemple, key1.key2.key3. Utilise le langage de requête jsonpath, https://github.com/h2non/jsonpath-ng, par exemple : -j ' $. spec.pools [ ? () @.spec.type == « Master »)]... points de terminaison
#### `--config-profile -c`
Chemin d’accès du profil de configuration BDC.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Chemin d’accès de l’emplacement où vous souhaitez la section du fichier placé. Par défaut : dirigé vers stdout.
#### `--force -f`
Forcer le remplacement du fichier cible.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-bdc-config-section-set"></a>section de configuration mssqlctl bdc défini
Définit la section spécifiée dans le profil de configuration sélectionné selon le chemin d’accès json donnée.  Tous les examplesbelow sont indiqués dans Bash.  Si vous utilisez une autre ligne de commande, sachez que vous devrez peut-être escapequotations en conséquence.  Vous pouvez également utiliser la fonctionnalité fichiers de correctifs.
```bash
mssqlctl bdc config section set --config-profile -c 
                                [--json-values -j]  
                                [--patch-file -p]
```
### <a name="examples"></a>Exemples
Par exemple, 1 (inline) - définir le port d’un point de terminaison unique (point de terminaison du contrôleur).
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values '$.spec.controlPlane.spec.endpoints[?(@.name=="Controller")].port=30080'
```
Par exemple, 1 (patch) - définir le port d’un point de terminaison unique (point de terminaison du contrôleur) avec le fichier correctif.
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
Par exemple, 2 (inline) - stockage de plan de contrôle de jeu.
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values 'spec.controlPlane.spec.storage=spec.controlPlane.spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
Par exemple, 2 (patch) - stockage de plan de contrôle de jeu avec le fichier correctif.
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"spec.controlPlane.spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Ex 3(inline) - définir un stockage de pool, y compris les réplicas (Pool de stockage).
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
Ex 3 (patch) - définir un stockage de pool, y compris les réplicas (Pool de stockage) avec le fichier correctif.
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--config-profile -c`
Chemin du profil de configuration de la configuration que vous souhaitez définir BDC
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--json-values -j`
Une liste de paires de valeur de clé des chemins d’accès json aux valeurs : key1.subkey1=value1,key2.subkey2=value2. Vous pouvez fournir inline valeurs json tel que : clé ='{« kind » : « cluster », « name » : « test-cluster »}' ou fournissez un chemin d’accès de fichier, telles que key=./values.json. Si vous souhaitez définir une valeur qui nécessite un conditionnel, utilisez la notation jsonpath par au début de votre chemin d’accès par le symbole $. Ainsi, vous permettent d’effectuer un conditionnel telles que j-$. key1.key2 [ ? () @.key3== 'someValue'] .key4 = value. Vous pouvez voir les exemples ci-dessous. Pour plus d’aide, consultez : https://jsonpath.com/
#### `--patch-file -p`
Chemin d’accès à un fichier json de correctif qui est basée sur la bibliothèque jsonpatch : http://jsonpatch.com/. Vous devez démarrer votre fichier json de correctif avec une clé appelée « patch », dont la valeur est un tableau d’opérations de correction destinées. Pour le chemin d’accès d’une opération de correctif logiciel, vous pouvez utiliser la notation à points, tels que key1.key2 pour la plupart des opérations. Si vous souhaitez effectuer une opération de remplacement, et que vous remplacez une valeur dans un tableau qui requiert un conditionnel, utilisez la notation jsonpath par au début de votre chemin d’accès par le symbole $. Ainsi, vous permettent d’effectuer un conditionnel telles que $. key1.key2 [ ? () @.key3== 'someValue'] .key4. Consultez les exemples ci-dessous. Pour plus d’aide, consultez : https://jsonpath.com/.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).