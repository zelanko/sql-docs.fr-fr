---
title: Informations de référence sur azdata app template
description: Article de référence sur les commandes azdata app template.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: da1b98649eeb48d5ae2d6ca05e61da53f519e944
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251054"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L’article suivant fournit des références sur les commandes `app template` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[`azdata app template list`](#azdata-app-template-list) | Récupère les modèles pris en charge.
[`azdata app template pull`](#azdata-app-template-pull) | Télécharge les modèles pris en charge.
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
Spécifiez un autre emplacement du référentiel de modèles. Valeur par défaut : https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
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
Nom du modèle. Pour obtenir la liste complète des noms de modèles pris en charge, exécuter `azdata app template list`
#### `--url -u`
Spécifiez un autre emplacement du référentiel de modèles. Valeur par défaut : https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Où placer le modèle du squelette d’application.
`./templates`
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil `azdata`, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
