---
title: référence de configuration de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 74097057702ad32a803c440d92b0ed7c8f855880
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66779422"
---
# <a name="mssqlctl-cluster-config"></a>Configuration de cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **cluster config** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[afficher de configuration de cluster mssqlctl](#mssqlctl-cluster-config-show) | Obtient la configuration actuelle de SQL Server Big Data du Cluster.
[mssqlctl cluster config init](#mssqlctl-cluster-config-init) | Initialise de créer un profil de configuration de cluster qui peut être utilisé avec le cluster.
[mssqlctl cluster config list](#mssqlctl-cluster-config-list) | Répertorie les options de fichier de configuration disponibles.
[mssqlctl cluster config section](reference-mssqlctl-cluster-config-section.md) | Commandes pour travailler avec des sections individuelles du fichier de configuration du cluster.
## <a name="mssqlctl-cluster-config-show"></a>afficher de configuration de cluster mssqlctl
Obtient le fichier de configuration SQL Server Big Data du Cluster actuel et sort dans le fichier cible ou assez l’imprime sur la console.
```bash
mssqlctl cluster config show [--target -t] 
                             [--force -f]
```
### <a name="examples"></a>Exemples
Afficher la configuration de cluster dans votre console
```bash
mssqlctl cluster config show
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Fichier de sortie pour stocker le résultat dans. Par défaut : dirigé vers stdout.
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
## <a name="mssqlctl-cluster-config-init"></a>mssqlctl cluster config init
Initialise de créer un profil de configuration de cluster qui peut être utilisé avec le cluster. La source du profil de configuration spécifique peut être spécifiée dans les arguments à partir de 3 choix.
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]  
                             [--force -f]
```
### <a name="examples"></a>Exemples
Guider cluster config init - vous allez recevoir des invites pour les valeurs nécessaires.
```bash
mssqlctl cluster config init
```
Init config avec des arguments d’un cluster, crée un profil de configuration d’ACS-dev-test dans. / custom.json.
```bash
mssqlctl cluster config init --src aks-dev-test.json --target custom.json
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Chemin d’accès de l’emplacement où vous souhaitez le profil de configuration placées, par défaut, cwd avec personnalisé-config.JSON.
#### `--src -s`
Source du profil de configuration : [« aks-dev-test.json', ' kubeadm-dev-test.json', ' minikube-dev-test.json']
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
## <a name="mssqlctl-cluster-config-list"></a>mssqlctl cluster config list
Répertorie les options de fichier de configuration disponibles pour une utilisation dans init de configuration de cluster
```bash
mssqlctl cluster config list [--config-file -c] 
                             
```
### <a name="examples"></a>Exemples
Affiche tous les noms de profil de configuration disponibles.
```bash
mssqlctl cluster config list
```
Affiche le json d’un profil de configuration spécifique.
```bash
mssqlctl cluster config list --config-file aks-dev-test.json
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-file -c`
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