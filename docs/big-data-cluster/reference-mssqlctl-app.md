---
title: référence d’application mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de l’application mssqlctl.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a14b548ed8c16776b4883e54f3ca47588dbb3e6b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958206"
---
# <a name="mssqlctl-app"></a>Application mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **application** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[modèle d’application mssqlctl](reference-mssqlctl-app-template.md) | modèles.
[mssqlctl application init](#mssqlctl-app-init) | Kickstart nouveau squelette d’application.
[créer des applications de mssqlctl](#mssqlctl-app-create) | Créer l’application.
[mise à jour des application mssqlctl](#mssqlctl-app-update) | Mettre à jour d’application.
[mssqlctl app list](#mssqlctl-app-list) | Liste des applications.
[mssqlctl app delete](#mssqlctl-app-delete) | Supprimer l’application.
[exécution de l’application mssqlctl](#mssqlctl-app-run) | Exécuter l’application.
[mssqlctl app describe](#mssqlctl-app-describe) | Décrire l’application.
## <a name="mssqlctl-app-init"></a>mssqlctl application init
Vous permet de squelette d’application nouveau kickstart et/ou fichiers spec selon les environnements d’exécution.
```bash
mssqlctl app init [--spec -s] 
                  [--name -n]  
                  [--version -v]  
                  [--template -t]  
                  [--destination -d]  
                  [--url -u]
```
### <a name="examples"></a>Exemples
Générer automatiquement une nouvelle application `spec.yaml` uniquement.
```bash
mssqlctl app init --spec
```
Générer automatiquement un nouveau squelette d’application d’application R selon la `r` modèle.
```bash
mssqlctl app init --name reduce --template r
```
Générer automatiquement un nouveau squelette d’application Python application selon la `python` modèle.
```bash
mssqlctl app init --name reduce --template python
```
Générer automatiquement un nouveau squelette d’application d’application SSIS selon la `ssis` modèle.
```bash
mssqlctl app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--spec -s`
Générer uniquement un spec.yaml de l’application.
#### `--name -n`
Nom de l'application.
#### `--version -v`
Version de l’application.
#### `--template -t`
Nom du modèle. Pour obtenir la liste complète désactiver les noms de modèle pris en charge s’exécuter `mssqlctl app template list`
#### `--destination -d`
Où placer la structure de l’application. Par défaut : répertoire de travail actuel.
#### `--url -u`
Spécifiez un emplacement de dépôt de modèle différent. Par défaut : https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-app-create"></a>créer des applications de mssqlctl
Créer une application.
```bash
mssqlctl app create --spec -s 
                    
```
### <a name="examples"></a>Exemples
Créer une nouvelle application à partir d’un répertoire qui contient une spécification de déploiement spec.yaml valide.
```bash
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--spec -s`
Chemin d’accès à un répertoire avec un fichier spec YAML décrivant l’application.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-app-update"></a>mise à jour des application mssqlctl
Mettre à jour une application.
```bash
mssqlctl app update [--spec -s] 
                    [--yes -y]
```
### <a name="examples"></a>Exemples
Mettre à jour une application existante à partir d’un répertoire qui contient une spécification de déploiement spec.yaml valide.
```bash
mssqlctl app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--spec -s`
Chemin d’accès à un répertoire avec un fichier spec YAML décrivant l’application.
#### `--yes -y`
Ne pas demander confirmation lors de la mise à jour une application à partir du fichier de spec.yaml du répertoire de travail actuel.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-app-list"></a>liste d’applications mssqlctl
Répertorier une application (s).,
```bash
mssqlctl app list [--name -n] 
                  [--version -v]
```
### <a name="examples"></a>Exemples
Application de la liste par nom et la version.
```bash
mssqlctl app list --name reduce  --version v1
```
Répertoriez toutes les versions de l’application par nom.
```bash
mssqlctl app list --name reduce
```
Répertoriez toutes les versions de l’application par nom.
```bash
mssqlctl app list
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
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-app-delete"></a>suppression d’application mssqlctl
Supprimer une application.
```bash
mssqlctl app delete --name -n 
                    --version -v
```
### <a name="examples"></a>Exemples
Supprimer l’application par le nom et la version.
```bash
mssqlctl app delete --name reduce --version v1    
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
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-app-run"></a>exécution de l’application mssqlctl
Exécuter une application.
```bash
mssqlctl app run --name -n 
                 --version -v  
                 [--inputs]
```
### <a name="examples"></a>Exemples
Exécutez l’application sans aucun paramètre d’entrée.
```bash
mssqlctl app run --name reduce --version v1
```
Exécutez l’application avec le paramètre d’entrée 1.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10
```
Exécuter l’application avec plusieurs paramètres d’entrée.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom de l'application.
#### `--version -v`
Version de l’application.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--inputs`
Application des paramètres d’un fichier CSV d’entrée `name=value` format.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-app-describe"></a>application de mssqlctl décrivent
Décrire une application.
```bash
mssqlctl app describe [--spec -s] 
                      [--name -n]  
                      [--version -v]
```
### <a name="examples"></a>Exemples
Décrire l’application.
```bash
mssqlctl app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--spec -s`
Chemin d’accès à un répertoire avec un fichier spec YAML décrivant l’application.
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
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).