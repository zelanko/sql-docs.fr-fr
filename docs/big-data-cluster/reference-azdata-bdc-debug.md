---
title: Référence de débogage azdata BDC
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de débogage azdata BDC.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 38c327287273ae6596326d88d9e0d67c8e014d47
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426229"
---
# <a name="azdata-bdc-debug"></a>débogage azdata BDC

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de **débogage BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[copie de débogage azdata BDC-journaux](#azdata-bdc-debug-copy-logs) | Copiez les journaux.
[vidage du débogage azdata BDC](#azdata-bdc-debug-dump) | Vidage du journal des déclencheurs.
## <a name="azdata-bdc-debug-copy-logs"></a>copie de débogage azdata BDC-journaux
Copiez les journaux de débogage à partir du cluster Big Data: la configuration de Kube est requise sur votre système.
```bash
azdata bdc debug copy-logs --namespace -n 
                           [--container -c]  
                           [--target-folder -d]  
                           [--pod -p]  
                           [--timeout -t]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom du cluster Big Data, utilisé pour l’espace de noms kubernetes.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--container -c`
Copiez les journaux des conteneurs avec un nom similaire, facultatif, par défaut, copie les journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, le dernier sera utilisé
#### `--target-folder -d`
Chemin d’accès au dossier cible dans lequel copier les journaux. Facultatif, par défaut, crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, le dernier sera utilisé
#### `--pod -p`
Copiez les journaux des Pod avec un nom similaire. Facultatif, par défaut copie les journaux de tous les pod. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, le dernier sera utilisé
#### `--timeout -t`
Nombre de secondes d’attente de la fin de la commande. La valeur par défaut est 0, ce qui est illimité
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées: JSON, jsonc, table, TSV.  Valeur par défaut: JSON.
#### `--query -q`
Chaîne de requête JMESPath. Pour [http://jmespath.org/](http://jmespath.org/]) plus d’informations et d’exemples, consultez.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="azdata-bdc-debug-dump"></a>vidage du débogage azdata BDC
Déclencher le vidage de la journalisation et le copier à partir de la configuration Container-Kube est requis sur votre système.
```bash
azdata bdc debug dump --namespace -n 
                      --container -c  
                      [--target-folder -d]
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--namespace -n`
Nom du cluster Big Data, utilisé pour l’espace de noms kubernetes.
#### `--container -c`
Copiez les journaux des conteneurs avec un nom similaire, facultatif, par défaut, copie les journaux de tous les conteneurs. Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, le dernier sera utilisé
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--target-folder -d`
Chemin d’accès au dossier cible dans lequel copier les journaux. Facultatif, par défaut, crée le résultat dans le dossier local.  Ne peut pas être spécifié plusieurs fois. S’il est spécifié plusieurs fois, le dernier sera utilisé`./output/dump`
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées: JSON, jsonc, table, TSV.  Valeur par défaut: JSON.
#### `--query -q`
Chaîne de requête JMESPath. Pour [http://jmespath.org/](http://jmespath.org/]) plus d’informations et d’exemples, consultez.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).
