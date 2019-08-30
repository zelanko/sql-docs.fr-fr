---
title: azdata app reference
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes de l’application azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ec7e461705138905713b803e2f0f96934044d971
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155294"
---
# <a name="azdata-app"></a>azdata app

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata app template](reference-azdata-app-template.md) | Modèles.
[azdata app init](#azdata-app-init) | Lancez un nouveau squelette d’applications.
[azdata app create](#azdata-app-create) | Créez une application.
[azdata app update](#azdata-app-update) | Mettez à jour une application.
[azdata app list](#azdata-app-list) | Répertoriez une ou des applications.
[azdata app delete](#azdata-app-delete) | Supprimez une application.
[azdata app run](#azdata-app-run) | Exécutez une application.
[azdata app describe](#azdata-app-describe) | Décrivez une application.
## <a name="azdata-app-init"></a>azdata app init
Vous aide à lancer un nouveau squelette et/ou des fichiers de spécification d’applications basés sur des environnements runtime.
```bash
azdata app init 
```
### <a name="examples"></a>Exemples
Générer un modèle automatique d’une nouvelle `spec.yaml` d’applications uniquement.
```bash
azdata app init --spec
```
Structurez une nouvelle structure d’application R basée sur `r` le modèle.
```bash
azdata app init --name reduce --template r
```
Structurez une nouvelle structure d’application python basée sur `python` le modèle.
```bash
azdata app init --name reduce --template python
```
Structurez une nouvelle structure d’application SSIS basée sur `ssis` le modèle.
```bash
azdata app init --name reduce --template ssis            
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-app-create"></a>azdata app create
Créez une application.
```bash
azdata app create 
```
### <a name="examples"></a>Exemples
Créez une nouvelle application à partir d’un répertoire contenant une spécification de déploiement spec.yaml valide.
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-app-update"></a>azdata app update
Mettez à jour une application.
```bash
azdata app update 
```
### <a name="examples"></a>Exemples
Mettez à jour une application existante à partir d’un répertoire contenant une spécification de déploiement spec.yaml valide.
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-app-list"></a>azdata app list
Répertoriez une ou des applications.
```bash
azdata app list 
```
### <a name="examples"></a>Exemples
Répertoriez les applications par nom et par version.
```bash
azdata app list --name reduce  --version v1
```
Répertoriez toutes les versions d’applications par nom.
```bash
azdata app list --name reduce
```
Répertoriez toutes les versions d’applications par nom.
```bash
azdata app list
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-app-delete"></a>azdata app delete
Supprimez une application.
```bash
azdata app delete 
```
### <a name="examples"></a>Exemples
Supprimez les applications par nom et par version.
```bash
azdata app delete --name reduce --version v1    
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
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-app-run"></a>azdata app run
Exécutez une application.
```bash
azdata app run 
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
## <a name="azdata-app-describe"></a>azdata app describe
Décrivez une application.
```bash
azdata app describe 
```
### <a name="examples"></a>Exemples
Décrivez l’application.
```bash
azdata app describe --name reduce --version v1    
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
