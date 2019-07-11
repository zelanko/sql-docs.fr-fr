---
title: mssqlctl bdc debug reference
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de débogage mssqlctl bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 20257039a40594cd592bcc4d4f6050027d8858ea
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728581"
---
# <a name="mssqlctl-bdc-debug"></a>mssqlctl bdc debug

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **CDM debug** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl bdc debug copy-logs](#mssqlctl-bdc-debug-copy-logs) | Copier les journaux.
[mssqlctl bdc debug dump](#mssqlctl-bdc-debug-dump) | Vidage de journalisation de déclencheur.
## <a name="mssqlctl-bdc-debug-copy-logs"></a>mssqlctl bdc debug copy-logs
Copier les journaux de débogage à partir du Cluster de données volumineuses : configuration de kube est requis sur votre système.
```bash
mssqlctl bdc debug copy-logs --namespace -n 
                             [--container -c]  
                             [--target-folder -d]  
                             [--pod -p]  
                             [--timeout -t]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom BDC, utilisé pour l’espace de noms kubernetes.
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
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-bdc-debug-dump"></a>mssqlctl bdc debug dump
Déclencher le vidage de la journalisation et le copier à partir du conteneur : configuration de kube est requis sur votre système.
```bash
mssqlctl bdc debug dump --namespace -n 
                        --container -c  
                        [--target-folder -d]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom BDC, utilisé pour l’espace de noms kubernetes.
#### `--container -c`
Copier les journaux pour les conteneurs avec un nom similaire, facultatif, par défaut copie des journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier sera utilisé
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target-folder -d`
Chemin du dossier cible pour copier les journaux. Facultatif, par défaut crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, dernier sera utilisé `./output/dump`
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