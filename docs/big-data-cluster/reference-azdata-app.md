---
title: Référence de l’application azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de l’application azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 793edde26ebebf9e55c5751adbedf662142280de
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426279"
---
# <a name="azdata-app"></a>application azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de l' **application** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[modèle d’application azdata](reference-azdata-app-template.md) | Ceux.
[initialisation d’application azdata](#azdata-app-init) | Kickstart nouveau squelette d’application.
[création de l’application azdata](#azdata-app-create) | Créer une application.
[mise à jour d’application azdata](#azdata-app-update) | Mettre à jour l’application.
[Liste des applications azdata](#azdata-app-list) | Répertorier les applications.
[suppression de l’application azdata](#azdata-app-delete) | Supprimer l’application.
[exécution de l’application azdata](#azdata-app-run) | Exécutez l’application.
[Description de l’application azdata](#azdata-app-describe) | Décrire l’application.
## <a name="azdata-app-init"></a>initialisation d’application azdata
Vous aide à Kickstart de nouveaux fichiers de squelette et/ou de spécifications d’application basés sur les environnements d’exécution.
```bash
azdata app init [--spec -s] 
                [--name -n]  
                [--version -v]  
                [--template -t]  
                [--destination -d]  
                [--url -u]
```
### <a name="examples"></a>Exemples
Structurer une nouvelle `spec.yaml` application uniquement.
```bash
azdata app init --spec
```
Structurez une nouvelle structure d’application R basée `r` sur le modèle.
```bash
azdata app init --name reduce --template r
```
Structurez une nouvelle structure d’application python basée `python` sur le modèle.
```bash
azdata app init --name reduce --template python
```
Structurez un nouveau squelette d’application SSIS basé `ssis` sur le modèle.
```bash
azdata app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--spec -s`
Générez simplement une application spec. YAML.
#### `--name -n`
Nom de l'application.
#### `--version -v`
Version de l’application.
#### `--template -t`
Nom du modèle. Pour obtenir la liste complète des noms de modèles pris en charge, exécutez`azdata app template list`
#### `--destination -d`
Où placer le squelette de l’application. Valeur par défaut: répertoire de travail actuel.
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
## <a name="azdata-app-create"></a>création de l’application azdata
Créer une application.
```bash
azdata app create --spec -s 
                  
```
### <a name="examples"></a>Exemples
Créez une application à partir d’un répertoire contenant une spécification de déploiement spec. YAML valide.
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--spec -s`
Chemin d’accès à un répertoire contenant un fichier de spécification YAML décrivant l’application.
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
## <a name="azdata-app-update"></a>mise à jour d’application azdata
Mettre à jour une application.
```bash
azdata app update [--spec -s] 
                  [--yes -y]
```
### <a name="examples"></a>Exemples
Mettre à jour une application existante à partir d’un répertoire contenant une spécification de déploiement spec. YAML valide.
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--spec -s`
Chemin d’accès à un répertoire contenant un fichier de spécification YAML décrivant l’application.
#### `--yes -y`
Ne pas demander de confirmation lors de la mise à jour d’une application à partir du fichier spec. YAML de CWD.
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
## <a name="azdata-app-list"></a>Liste des applications azdata
Répertorie une ou plusieurs applications.
```bash
azdata app list [--name -n] 
                [--version -v]
```
### <a name="examples"></a>Exemples
Répertorie les applications par nom et version.
```bash
azdata app list --name reduce  --version v1
```
Répertorie toutes les versions d’application par nom.
```bash
azdata app list --name reduce
```
Répertorie toutes les versions d’application par nom.
```bash
azdata app list
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom de l'application.
#### `--version -v`
Version de l’application.
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
## <a name="azdata-app-delete"></a>suppression de l’application azdata
Supprimer une application.
```bash
azdata app delete --name -n 
                  --version -v
```
### <a name="examples"></a>Exemples
Supprimer l’application par nom et par version.
```bash
azdata app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom de l'application.
#### `--version -v`
Version de l’application.
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
## <a name="azdata-app-run"></a>exécution de l’application azdata
Exécuter une application.
```bash
azdata app run --name -n 
               --version -v  
               [--inputs]
```
### <a name="examples"></a>Exemples
Exécutez l’application sans paramètres d’entrée.
```bash
azdata app run --name reduce --version v1
```
Exécutez l’application avec 1 paramètre d’entrée.
```bash
azdata app run --name reduce --version v1 --inputs x=10
```
Exécutez l’application avec plusieurs paramètres d’entrée.
```bash
azdata app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom de l'application.
#### `--version -v`
Version de l’application.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--inputs`
Paramètres d’entrée de l’application `name=value` au format CSV.
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
## <a name="azdata-app-describe"></a>Description de l’application azdata
Décrire une application.
```bash
azdata app describe [--spec -s] 
                    [--name -n]  
                    [--version -v]
```
### <a name="examples"></a>Exemples
Décrivez l’application.
```bash
azdata app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--spec -s`
Chemin d’accès à un répertoire contenant un fichier de spécification YAML décrivant l’application.
#### `--name -n`
Nom de l'application.
#### `--version -v`
Version de l’application.
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
