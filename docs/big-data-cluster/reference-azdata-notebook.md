---
title: Référence du bloc-notes azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de bloc-notes azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b96c5e06ec51f53964a28cac86f385d6b42c1dc4
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426009"
---
# <a name="azdata-notebook"></a>bloc-notes azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de **bloc-notes** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez la [référence azdata](reference-azdata.md)

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[vue du bloc-notes azdata](#azdata-notebook-view) | Afficher un bloc-notes.  Option d’arrêt à la première erreur d’exécution de la cellule.
[exécution du bloc-notes azdata](#azdata-notebook-run) | Exécuter un bloc-notes.  L’exécution s’arrête à la première erreur.
## <a name="azdata-notebook-view"></a>vue du bloc-notes azdata
Cette commande peut utiliser un fichier de bloc-notes et convertir la démarque, le code et la sortie en format terminal de couleurs.
```bash
azdata notebook view --path -p 
                     [--continue-on-error -c]
```
### <a name="examples"></a>Exemples
Afficher le bloc-notes.  Affiche toutes les cellules.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb'
```
Afficher le bloc-notes.  Cette opération affiche toutes les cellules, sauf si une cellule avec une erreur dans sa sortie est rencontrée.  Dans ce cas, la sortie s’arrête.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb' --stop-on-error
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Chemin d’accès du bloc-notes à afficher.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--continue-on-error -c`
Continue d’afficher des cellules supplémentaires en ignorant toutes les erreurs de cellule trouvées dans la sortie du bloc-notes.  Le comportement par défaut consiste à arrêter en cas d’erreur.  L’arrêt permet de voir la première cellule qui a rencontré une erreur plus facilement.
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
## <a name="azdata-notebook-run"></a>exécution du bloc-notes azdata
Cette commande crée un répertoire temporaire et l’exécute dans le bloc-notes indiqué en tant que répertoire de travail.
```bash
azdata notebook run --path -p 
                    [--output-path]  
                    [--output-html]
```
### <a name="examples"></a>Exemples
Exécuter le bloc-notes.
```bash
azdata notebook run --path '/home/me/notebooks/demo_notebook.ipynb'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Chemin d’accès du fichier au bloc-notes à exécuter.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--output-path`
Chemin d’accès du répertoire à utiliser pour la sortie du bloc-notes.  Le bloc-notes avec des données de sortie et tous les fichiers de bloc-notes générés sont générés par rapport à ce répertoire.
#### `--output-html`
Indicateur facultatif indicatingg s’il faut également convertir le bloc-notes de sortie au format HTML.  Crée un deuxième fichier de sortie.
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

Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).
