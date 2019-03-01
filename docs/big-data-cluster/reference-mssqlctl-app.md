---
title: référence d’application mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Article de référence pour les commandes de l’application mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fa2b43c352fbab39cd00112b9646a87a2b752f5b
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018485"
---
# <a name="mssqlctl-app"></a>mssqlctl app

L’article suivant fournit la référence pour le **application** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a id="commands"></a> Commandes

|||
|---|---|
| [create](#create) | Créer l’application. |
| [delete](#delete) | Supprimer l’application. |
| [describe](#describe) | Décrire l’application. |
| [init](#init) | Kickstart nouveau squelette d’application. |
| [list](#list) | Liste des applications. |
| [run](#run) | Exécuter l’application. |
| [update](#update) | Mettre à jour d’application. |
| [template](reference-mssqlctl-app-template.md) | Commandes du modèle. |

## <a id="create"></a> mssqlctl app create

Créer l’application.

```
mssqlctl app create
   --assets
   --code
   --description
   --entrypoint
   --inputs
   --name
   --outputs
   --runtime
   --spec
   --version
   --yes
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--assets -a** | Liste des composants de fichier d’application supplémentaires à inclure. |
| **--code -c** | Chemin d’accès au fichier de code R ou Python. |
| **--description -d** | Description de l'application. |
| **--entrypoint** |  |
| **--inputs** | Schéma de paramètre d’entrée. |
| **--name -n** | Nom de l'application. |
| **--outputs** | Schéma du paramètre de sortie. |
| **--runtime -r** | Exécution de l’application.  Valeurs autorisées : Mleap, Python, R, SSIS. |
| **--spec -s** | Chemin d’accès à un répertoire avec un fichier spec YAML décrivant l’application. |
| **--version -v** | Version de l’application. |
| **--yes -y** | Ne pas demander confirmation lors de la création d’une application à partir du fichier de spec.yaml du répertoire de travail actuel. |

### <a name="examples"></a>Exemples

Créez une application via spec.yaml (recommandé).

```
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```

Créer un nouveau inline d’application Python à l’aide des arguments.

```
mssqlctl app create --name add --version v1 --inputs x=float, y=float --outputs result=float --runtime Python --code add.py  --init init.py
```

Créer un nouveau inline d’application R à l’aide des arguments.

```
mssqlctl app create --name add --version v1 --inputs x=numeric, y=numeric --outputs result=numeric --runtime R --code add.R  --init init.R
```

Créer un nouveau en ligne application R avec des ressources de fichiers supplémentaires à inclure.

```
mssqlctl app create --name add --version v1 --runtime R --code  add.R --assets file.RData,/path/to/more/files
```

## <a id="delete"></a> mssqlctl app delete

Supprimer l’application.

```
mssqlctl app delete
   --name
   --version
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--name -n** | Nom de l'application. |
| **--version -v** | Version de l’application. |

### <a name="examples"></a>Exemples

Supprimer l’application par le nom et la version.

```
mssqlctl app delete --name reduce --version v1
```

## <a id="describe"></a> mssqlctl app describe

Décrire l’application.

```
mssqlctl app describe
   --name
   --spec
   --version
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--name -n** | Nom de l'application. |
| **--spec -s** | Chemin d’accès à un répertoire avec un fichier spec YAML décrivant l’application. |
| **--version -v** | Version de l’application. |

### <a name="examples"></a>Exemples

Décrire l’application.

```
mssqlctl app describe --name reduce --version v1
```

## <a id="init"></a> mssqlctl app init

Kickstart nouveau squelette d’application.

```
mssqlctl app init
   --destination
   --name
   --spec
   --template
   --url
   --version
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--destination -d** | Où placer la structure de l’application. Par défaut : répertoire de travail actuel. |
| **--name -n** | Nom de l'application. |
| **--spec -s** | Générer uniquement un spec.yaml de l’application. |
| **--template -t** | Nom du modèle. Pour obtenir la liste complète désactiver les noms de modèle pris en charge, exécutez `mssqlctl app template list`. |
| **--url -u** | Spécifiez un emplacement de dépôt de modèle différent. Par défaut : https://github.com/Microsoft/sql-server-samples.git. |
| **--version -v** | Version de l’application. |

### <a name="examples"></a>Exemples

Générer automatiquement une nouvelle application `spec.yaml` uniquement.

```
mssqlctl app init --spec
```

Générer automatiquement un nouveau squelette d’application d’application R selon la `r` modèle.

```
mssqlctl app init --name reduce --template r
```

Générer automatiquement un nouveau squelette d’application Python application selon la `python` modèle.

```
mssqlctl app init --name reduce --template python
```

Générer automatiquement un nouveau squelette d’application d’application SSIS selon la `ssis` modèle.

```
mssqlctl app init --name reduce --template ssis
```

## <a id="list"></a> mssqlctl app list

Liste des applications.

```
mssqlctl app list
   --name
   --version
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--name -n** | Nom de l'application. |
| **--version -v** | Version de l’application. |

### <a name="examples"></a>Exemples

Application de la liste par nom et la version.

```
mssqlctl app list --name reduce  --version v1
```

Répertoriez toutes les versions de l’application par nom.

```
mssqlctl app list --name reduce
```

Répertorier toutes les applications.

```
mssqlctl app list
```

## <a id="run"></a> mssqlctl app run

Exécuter l’application.

```
mssqlctl app run
   --name
   --version
   --inputs
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--name -n** | Nom de l'application. |
| **--version -v** | Version de l’application. |
| **--inputs** | Application des paramètres d’un fichier CSV d’entrée `name=value` format. |

### <a name="examples"></a>Exemples

Exécutez l’application sans aucun paramètre d’entrée.

```
mssqlctl app run --name reduce --version v1
```

Exécutez l’application avec le paramètre d’entrée 1.

```
mssqlctl app run --name reduce --version v1 --inputs x=10
```

Exécuter l’application avec plusieurs paramètres d’entrée.

```
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6
```

## <a id="update"></a> mssqlctl app update

Mettre à jour d’application.

```
mssqlctl app update
   --spec
   --yes
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--spec -s** | Chemin d’accès à un répertoire avec un fichier spec YAML décrivant l’application. |
| **--yes -y** | Ne pas demander confirmation lors de la mise à jour une application à partir du fichier de spec.yaml du répertoire de travail actuel. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).