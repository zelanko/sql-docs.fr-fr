---
title: mssqlctl bdc config reference
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de bdc mssqlctl.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f57ba87ea7cbd770380497bd340b5eaa4d80f29c
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394161"
---
# <a name="mssqlctl-bdc-config"></a>mssqlctl bdc config

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **bdc config** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl bdc config show](#mssqlctl-bdc-config-show) | Obtient la configuration actuelle du Cluster Big Data.
[mssqlctl bdc config init](#mssqlctl-bdc-config-init) | Initialise un grand Cluster données créer de profil de configuration qui peut être utilisé avec le cluster.
[mssqlctl bdc config list](#mssqlctl-bdc-config-list) | Répertorie les options de profil de configuration disponibles.
[mssqlctl bdc config section](reference-mssqlctl-bdc-config-section.md) | Commandes pour travailler avec des sections d’un profil de configuration de Cluster de données volumineuses.
## <a name="mssqlctl-bdc-config-show"></a>mssqlctl bdc config show
Obtient le profil de configuration actuelle du Cluster Big Data et sort dans le répertoire cible ou assez l’imprime sur la console.
```bash
mssqlctl bdc config show [--target -t] 
                         [--force -f]
```
### <a name="examples"></a>Exemples
Afficher la configuration du catalogue de données métiers dans votre console
```bash
mssqlctl bdc config show
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
## <a name="mssqlctl-bdc-config-init"></a>mssqlctl bdc config init
Initialise un grand Cluster données créer de profil de configuration qui peut être utilisé avec le cluster. La source du profil de configuration spécifique peut être spécifiée dans les arguments à partir de 3 choix.
```bash
mssqlctl bdc config init [--target -t] 
                         [--source -s]  
                         [--force -f]
```
### <a name="examples"></a>Exemples
Expérience d’init interactive BDC config - vous recevrez des invites pour les valeurs nécessaires.
```bash
mssqlctl bdc config init
```
BDC config init avec des arguments, crée un profil de configuration d’ACS-dev-test dans. / personnalisé.
```bash
mssqlctl bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target -t`
Chemin d’accès de l’emplacement où vous souhaitez le profil de configuration placées, par défaut, cwd avec personnalisé-config.JSON.
#### `--source -s`
Source du profil de configuration : [« aks-dev-test », « kubeadm-dev-test », « minikube-dev-test »]
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
## <a name="mssqlctl-bdc-config-list"></a>mssqlctl bdc config list
Répertorie les options de profil de configuration disponibles pour une utilisation dans `bdc config init`
```bash
mssqlctl bdc config list [--config-profile -c] 
                         
```
### <a name="examples"></a>Exemples
Affiche tous les noms de profil de configuration disponibles.
```bash
mssqlctl bdc config list
```
Affiche le json d’un profil de configuration spécifique.
```bash
mssqlctl bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--config-profile -c`
Profil de configuration par défaut : [« aks-dev-test », « kubeadm-dev-test », « minikube-dev-test »]
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