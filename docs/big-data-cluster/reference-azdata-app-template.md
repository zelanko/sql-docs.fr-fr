---
title: Référence du modèle d’application azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de modèle d’application azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3b257a2bacc56a7907ab0d25f492ed0ebd605543
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426329"
---
# <a name="azdata-app-template"></a>modèle d’application azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de **modèle d’application** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[Liste des modèles d’application azdata](#azdata-app-template-list) | Récupérer les modèles pris en charge.
[extraction de modèle d’application azdata](#azdata-app-template-pull) | Télécharger les modèles pris en charge.
## <a name="azdata-app-template-list"></a>Liste des modèles d’application azdata
Récupérez les modèles pris en charge sous le référentiel [URL] GitHub spécifié.
```bash
azdata app template list [--url -u] 
                         
```
### <a name="examples"></a>Exemples
Récupérez tous les modèles sous l’emplacement du référentiel de modèles par défaut.
```bash
azdata app template list
```
Récupérez tous les modèles sous un emplacement de référentiel différent.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--url -u`
Spécifiez un autre emplacement de dépôt de modèles. Valeurs https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-template-pull"></a>extraction de modèle d’application azdata
Téléchargez les modèles pris en charge sous le référentiel [URL] GitHub spécifié.
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>Exemples
Téléchargez tous les modèles sous l’emplacement du référentiel de modèles par défaut.
```bash
azdata app template pull
```
Téléchargez tous les modèles sous un emplacement de référentiel différent.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
Téléchargez un modèle individuel par son nom.
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du modèle. Pour obtenir la liste complète des modèles pris en charge namesrun`azdata app template list`
#### `--url -u`
Spécifiez un autre emplacement de dépôt de modèles. Valeurs https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Où placer le modèle de squelette d’application.
`./templates`
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
