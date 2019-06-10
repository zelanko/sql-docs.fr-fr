---
title: mssqlctl cluster debug reference
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de débogage de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4eafc3838d153a2616e34e98aed041374c04292d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779402"
---
# <a name="mssqlctl-cluster-debug"></a>Débogage de cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **débogage de cluster** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl cluster debug copy-logs](#mssqlctl-cluster-debug-copy-logs) | Copier les journaux.
[mssqlctl cluster debug dump](#mssqlctl-cluster-debug-dump) | Vidage de journalisation de déclencheur.
## <a name="mssqlctl-cluster-debug-copy-logs"></a>mssqlctl cluster debug copy-logs
Copier les journaux de débogage à partir du cluster : configuration de kube est requis sur votre système.
```bash
mssqlctl cluster debug copy-logs --namespace -n 
                                 [--container -c]  
                                 [--target-folder -d]  
                                 [--pod -p]  
                                 [--timeout -t]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom du cluster, utilisé pour l’espace de noms kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--container -c`
Copier les journaux pour les conteneurs avec un nom similaire, facultatif, par défaut copie des journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier sera utilisé
#### `--target-folder -d`
Chemin du dossier cible pour copier les journaux. Facultatif, par défaut crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier sera utilisé
#### `--pod -p`
Copier les journaux pour les pods avec un nom similaire. Facultatif, par défaut, les journaux des copies pour tous les pods. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier sera utilisé
#### `--timeout -t`
Le nombre de secondes d’attente de la commande se termine. La valeur par défaut est 0 qui est un nombre illimité
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
## <a name="mssqlctl-cluster-debug-dump"></a>vidage du débogage mssqlctl cluster
Déclencher le vidage de la journalisation et le copier à partir du conteneur : configuration de kube est requis sur votre système.
```bash
mssqlctl cluster debug dump --namespace -n 
                            --container -c  
                            [--target-folder -d]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom du cluster, utilisé pour l’espace de noms kubernetes.
#### `--container -c`
Copier les journaux pour les conteneurs avec un nom similaire, facultatif, par défaut copie des journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier sera utilisé
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target-folder -d`
Chemin du dossier cible pour copier les journaux. Facultatif, par défaut crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier sera utilisé `./output/dump`
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