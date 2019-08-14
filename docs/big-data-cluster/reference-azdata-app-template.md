---
title: Informations de référence sur azdata app template
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata app template.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3b257a2bacc56a7907ab0d25f492ed0ebd605543
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426329"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **app template** dans l’outil **azdata**. Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata app template list](#azdata-app-template-list) | Récupère les modèles pris en charge.
[azdata app template pull](#azdata-app-template-pull) | Télécharge les modèles pris en charge.
## <a name="azdata-app-template-list"></a>azdata app template list
Récupère les modèles pris en charge dans le dépôt GitHub spécifié [URL].
```bash
azdata app template list [--url -u] 
                         
```
### <a name="examples"></a>Exemples
Récupère tous les modèles situés dans le dépôt de modèles par défaut.
```bash
azdata app template list
```
Récupère tous les modèles situés dans un autre dépôt.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--url -u`
Spécifier un autre référentiel de modèles. Valeur par défaut : https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-template-pull"></a>azdata app template pull
Télécharge les modèles pris en charge dans le dépôt GitHub spécifié [URL].
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>Exemples
Télécharge tous les modèles situés dans le dépôt de modèles par défaut.
```bash
azdata app template pull
```
Télécharge tous les modèles situés dans un autre dépôt.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
Télécharge un modèle à l’aide de son nom.
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du modèle. Pour obtenir la liste complète des modèles pris en charge, exécutez `azdata app template list`
#### `--url -u`
Spécifier un autre référentiel de modèles. Valeur par défaut : https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Où placer le modèle du squelette d’application.
`./templates`
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
