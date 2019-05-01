---
title: référence de section de configuration de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de section de configuration de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d5a793e7d0fcaf782a09a4981491ef0a8d90ab5a
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759136"
---
# <a name="mssqlctl-cluster-config-section"></a>Section de la configuration de cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **section de configuration de cluster** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[obtenir de la section de configuration de cluster mssqlctl](#mssqlctl-cluster-config-section-get) | Obtient une section à partir d’un fichier de configuration.
[mssqlctl cluster config section set](#mssqlctl-cluster-config-section-set) | Définit une section d’un fichier de configuration.
## <a name="mssqlctl-cluster-config-section-get"></a>obtenir de la section de configuration de cluster mssqlctl
Obtient la section spécifiée à partir du fichier de configuration sélectionné selon le chemin d’accès json donnée.
```bash
mssqlctl cluster config section get --json-path -j 
                                    --config-file -f  
                                    [--target -t]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--json-path -j`
Le chemin de clé json qui mène à la section ou la valeur du fichier de configuration, par exemple, key1.key2.key3. Utilise le langage de requête jsonpath, https://github.com/h2non/jsonpath-ng, par exemple : -j ' $. spec.pools [ ? () @.spec.type == « Master »)]... points de terminaison
#### `--config-file -f`
Chemin d’accès du fichier de configuration de cluster.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Chemin d’accès de l’emplacement où vous souhaitez la section du fichier placé.
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
Définit la section spécifiée dans le fichier de configuration sélectionné en fonction du chemin d’accès json donnée.
```bash
mssqlctl cluster config section set --config-file -f 
                                    [--json-values -j]  
                                    [--patch-file -p]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--config-file -f`
Chemin de fichier de configuration de cluster de la configuration que vous souhaitez définir
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--json-values -j`
Une liste de paires de valeur de clé des chemins d’accès json aux valeurs : key1.subkey1=value1,key2.subkey2=value2. Vous pouvez fournir inline valeurs json tel que : clé ='{« kind » : « cluster », « name » : « test-cluster »}' ou fournissez un chemin d’accès de fichier, telles que key=./values.json
#### `--patch-file -p`
Chemin d’accès à un fichier json de correctif qui est basée sur la bibliothèque de jsonpatch et jsonpath : https://github.com/stefankoegl/python-json-patch , https://github.com/h2non/jsonpath-ng -un exemple simple : {« patch » : [{« op » : « ajouter », « path » : « metadata.name », « value » : « test »}, {« op » : « ajouter », « path » : « metadata.array », « value » : [1, 2, 3]}]} Veuillez inclure la clé « patch » et que la valeur à un tableau des correctifs que vous projetez de faire.  Elle est exécutée en tant que tel. Un exemple plus complexe : {« patch » : [{« op » : « remplacer », « path » : « $. spec.pools [ ? () @.spec.type == 'Master')]... points de terminaison », « value » : {« name » : « Nouveau point de terminaison «}}]}
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