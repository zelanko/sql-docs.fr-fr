---
title: Informations de référence sur le notebook azdata
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata notebook.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 97b8cbae68e16dbdde6e9662b18e37f222a1af80
ms.sourcegitcommit: b016c01c47bc08351d093a59448d895cc170f8c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118153"
---
# <a name="azdata-notebook"></a>azdata notebook

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata notebook view](#azdata-notebook-view) | Afficher un notebook.  Option pour arrêter à la première erreur d’exécution d’une cellule.
[azdata notebook run](#azdata-notebook-run) | Exécuter un notebook.  L’exécution s’arrête à la première erreur.
## <a name="azdata-notebook-view"></a>azdata notebook view
Cette commande peut prendre un fichier de notebook et convertir le markdown, le code et la sortie en un format de terminal couleur.
```bash
azdata notebook view --path -p 
                     [--continue-on-error -c]
```
### <a name="examples"></a>Exemples
Afficher un notebook.  Ceci montre toutes les cellules.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb'
```
Afficher un notebook.  Ceci montre toutes les cellules, sauf si une cellule avec une erreur dans sa sortie est rencontrée.  Dans ce cas, la sortie s’arrête.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb' --stop-on-error
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Chemin du notebook à afficher.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--continue-on-error -c`
Continuer d’afficher d’autres cellules en ignorant les erreurs de cellule trouvées dans la sortie du notebook.  Le comportement par défaut est d’arrêter en cas d’erreur.  L’arrêt permet de voir plus facilement la première cellule qui a rencontré une erreur.
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-notebook-run"></a>azdata notebook run
Cette commande crée un répertoire temporaire et y exécute le notebook spécifié comme répertoire de travail.

>[!NOTE]
>Vérifié par rapport à azdata v 15.0.1900 : exécuter la commande prise en charge uniquement pour les blocs-notes python 3.

```bash
azdata notebook run --path -p 
                    [--output-path]  
                    [--output-html]  
                    [--arguments -a]  
                    [--interactive -i]  
                    [--clear -c]
```
### <a name="examples"></a>Exemples
Exécuter un notebook.
```bash
azdata notebook run --path '/home/me/notebooks/demo_notebook.ipynb'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--path -p`
Chemin du fichier du notebook à exécuter.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--output-path`
Chemin du répertoire à utiliser pour la sortie du notebook.  Le notebook avec des données de sortie et les fichiers générés par le notebook sont générés relativement à ce répertoire.
#### `--output-html`
Indicateur facultatif qui spécifie s’il faut ou non convertir le bloc-notes de sortie au format HTML.  Crée un deuxième fichier de sortie.
#### `--arguments -a`
Liste facultative des arguments du bloc-notes à injecter dans l’exécution du bloc-notes.  Encodé en tant que dictionnaire JSON.  Exemple : « { » Name» : « value », « nom2 » : « value2 »}»
#### `--interactive -i`
Exécuter un bloc-notes en mode interactif.
#### `--clear -c`
En mode interactif, effacez la console avant de restituer une cellule.
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les autres commandes **azdata**, consultez [azdata reference](reference-azdata.md). 

- Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
