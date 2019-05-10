---
title: référence de configuration de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3a4693c5ffb68ad555d97d02f983fadf4e6bbd9a
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774666"
---
# <a name="mssqlctl-cluster-config"></a>Configuration de cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **cluster config** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl cluster config get](#mssqlctl-cluster-config-get) | Obtenir la configuration de cluster - kube config est requis sur votre système.
[mssqlctl cluster config init](#mssqlctl-cluster-config-init) | Initialise une configuration de cluster.
[mssqlctl cluster config list](#mssqlctl-cluster-config-list) | Répertorie les options de fichier de configuration disponibles.
[mssqlctl cluster config section](reference-mssqlctl-cluster-config-section.md) | Commandes pour travailler avec des sections individuelles du fichier de configuration.
## <a name="mssqlctl-cluster-config-get"></a>mssqlctl cluster config get
Obtient le fichier de configuration SQL Server Big Data du Cluster actuel.
```bash
mssqlctl cluster config get --name -n 
                            [--output-file -f]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du cluster, utilisé pour l’espace de noms kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--output-file -f`
Fichier de sortie pour stocker le résultat dans. Par défaut : dirigé vers stdout.
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
## <a name="mssqlctl-cluster-config-init"></a>mssqlctl cluster config init
Initialise un fichier de configuration de cluster pour l’utilisateur en fonction du type spécifié par défaut.
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Chemin d’accès de l’endroit où vous souhaitez que le fichier de configuration placées, par défaut, cwd avec personnalisé-config.JSON.
#### `--src -s`
Source de configuration : [« aks-dev-test.json', ' kubeadm-dev-test.json', ' minikube-dev-test.json']
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
## <a name="mssqlctl-cluster-config-list"></a>mssqlctl cluster config list
Répertorie les options de fichier de configuration disponibles pour une utilisation dans init de configuration de cluster
```bash
mssqlctl cluster config list [--config-file -f] 
                             
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-file -f`
Fichier de configuration par défaut : [« aks-dev-test.json', ' kubeadm-dev-test.json', ' minikube-dev-test.json']
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