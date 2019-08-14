---
title: Informations de référence sur azdata bdc debug
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc debug.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 38c327287273ae6596326d88d9e0d67c8e014d47
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426229"
---
# <a name="azdata-bdc-debug"></a>azdata bdc debug

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **bdc debug** dans l’outil **azdata**. Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc debug copy-logs](#azdata-bdc-debug-copy-logs) | Copie les journaux.
[azdata bdc debug dump](#azdata-bdc-debug-dump) | Déclenche le vidage des journaux.
## <a name="azdata-bdc-debug-copy-logs"></a>azdata bdc debug copy-logs
Copie les journaux de débogage à partir du cluster Big Data - Vous devez avoir la configuration Kube sur votre système.
```bash
azdata bdc debug copy-logs --namespace -n 
                           [--container -c]  
                           [--target-folder -d]  
                           [--pod -p]  
                           [--timeout -t]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom du cluster Big Data, utilisé pour l’espace de noms Kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--container -c`
Copier les journaux des conteneurs avec un nom similaire. Facultatif : par défaut, copie les journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, c’est le dernier qui sera utilisé.
#### `--target-folder -d`
Chemin du dossier cible dans lequel copier les journaux. Facultatif : par défaut, crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, c’est le dernier qui sera utilisé.
#### `--pod -p`
Copier les journaux des pods avec un nom similaire. Facultatif : par défaut, copie les journaux de tous les pods. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, c’est le dernier qui sera utilisé.
#### `--timeout -t`
Nombre de secondes à attendre pour l’exécution de la commande. La valeur par défaut est 0, ce qui signifie qu’elle est illimitée.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmenter le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et quitter.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmenter le niveau de détail de la journalisation. Utilisez --debug pour obtenir des journaux de débogage complets.
## <a name="azdata-bdc-debug-dump"></a>azdata bdc debug dump
Déclenche le vidage des journaux et copie le contenu du conteneur - La configuration Kube doit se trouver sur votre système.
```bash
azdata bdc debug dump --namespace -n 
                      --container -c  
                      [--target-folder -d]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom du cluster Big Data, utilisé pour l’espace de noms Kubernetes.
#### `--container -c`
Copier les journaux des conteneurs avec un nom similaire. Facultatif : par défaut, copie les journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, c’est le dernier qui sera utilisé.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target-folder -d`
Chemin du dossier cible dans lequel copier les journaux. Facultatif : par défaut, crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, c’est le dernier qui sera utilisé `./output/dump`
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmenter le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et quitter.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmenter le niveau de détail de la journalisation. Utilisez --debug pour obtenir des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
