---
title: Informations de référence sur azdata app template
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata app template.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 07911616659a29df7f7fa6ce4d356a9c82789ae2
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153230"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata app template list](#azdata-app-template-list) | Récupère les modèles pris en charge.
[azdata app template pull](#azdata-app-template-pull) | Télécharge les modèles pris en charge.
## <a name="azdata-app-template-list"></a>azdata app template list
Récupère les modèles pris en charge dans le dépôt GitHub spécifié [URL].
```bash
azdata app template list 
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
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour obtenir des journaux de débogage complets.
## <a name="azdata-app-template-pull"></a>azdata app template pull
Télécharge les modèles pris en charge dans le dépôt GitHub spécifié [URL].
```bash
azdata app template pull 
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
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les autres commandes **azdata**, consultez [azdata reference](reference-azdata.md). 

- Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
