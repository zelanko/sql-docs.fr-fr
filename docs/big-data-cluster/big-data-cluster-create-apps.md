---
title: Comment déployer une application
titleSuffix: SQL Server 2019 big data clusters
description: Déployer un script Python ou R en tant qu’application sur un cluster de données volumineux de SQL Server 2019 (version préliminaire).
author: TheBharath
ms.author: bharaths
manager: craigg
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: cca0ac5e7b81318d95fbb133758fca83e1a0742e
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246405"
---
# <a name="how-to-deploy-an-app-on-sql-server-2019-big-data-cluster-preview"></a>Comment déployer une application sur un cluster de données volumineux de SQL Server 2019 (version préliminaire)

Cet article décrit comment déployer et gérer le script R et Python en tant qu’application à l’intérieur d’un cluster de données volumineuses de SQL Server 2019 (version préliminaire).

Les applications R et Python sont déployées et gérées avec le **mssqlctl-pre** utilitaire de ligne de commande qui est inclus dans les CTP 2.2. Cet article fournit des exemples montrant comment déployer ces scripts R et Python en tant qu’applications à partir de la ligne de commande.

## <a name="prerequisites"></a>Prérequis

Vous devez disposer d’un cluster de données volumineuses de SQL Server 2019 configuré. Pour plus d’informations, consultez [le déploiement de SQL Server du cluster big data sur Kubernetes](deployment-guidance.md). 

## <a name="installation"></a>Installation

Le **mssqlctl-pre** utilitaire de ligne de commande est fourni pour afficher un aperçu de la fonctionnalité de déploiement d’application Python et R. Utilisez la commande suivante pour installer l’utilitaire :

```cmd
pip install -r https://private-repo.microsoft.com/python/ctp-2.2/mssqlctlpre/mssqlctlpre.txt --trusted-host https://private-repo.microsoft.com
```

## <a name="capabilities"></a>Fonctions

Dans CTP 2.2, que vous pouvez créer, supprimer, répertorier et exécuter une application R ou Python. Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **mssqlctl-pre**.

| Command | Description |
|---|---|
| `mssqlctl-pre login` | Se connecter à un cluster de données volumineux de SQL Server |
| `mssqlctl-pre app create` | Créer une application |
| `mssqlctl-pre app list` | Liste des applications déployées |
| `mssqlctl-pre app delete` | Supprimer une application |
| `mssqlctl-pre app run` | Liste des applications en cours d’exécution |

Vous pouvez obtenir de l’aide avec le `--help` paramètre comme dans l’exemple suivant :

```bash
mssqlctl-pre app create --help
```

Les sections suivantes décrivent ces commandes plus en détail.

## <a name="log-in"></a>Connectez-vous

Avant de configurer des applications R et Python, tout d’abord vous connecter à votre serveur SQL Server en cluster big data avec le `mssqlctl-pre login` commande. Spécifiez l’adresse IP externe de la `service-proxy-lb` ou `service-proxy-nodeport` services (par exemple : `https://ip-address:30777`), ainsi que le nom d’utilisateur et le mot de passe pour le cluster.

Vous pouvez obtenir l’adresse IP de la **proxy-service-lb** ou **proxy-service-nodeport** service en exécutant cette commande dans une fenêtre bash ou cmd :

```bash 
kubectl get svc service-proxy-lb -n <name of your cluster>
```

```bash
mssqlctl-pre login -e https://<ip-address-of-service-proxy-lb>:30777 -u <user-name> -p <password>
```

## <a name="create-an-app"></a>Créer une application

Pour créer une application, vous transmettez des fichiers de code Python ou R à **mssqlctl-pre** avec la `app create` commande. Ces fichiers résident localement sur l’ordinateur que vous créez l’application à partir de.

Pour créer une nouvelle application dans votre cluster de données volumineux, utilisez la syntaxe suivante :

```bash
mssqlctl-pre app create -n <app_name> -v <version_number> -r <runtime> -i <path_to_code_init> -c <path_to_code> --inputs <input_params> --outputs <output_params> 
```

La commande suivante montre un exemple de ce que cette commande peut ressembler :

```py
#add.py
def add(x,y):
        result = x+y
        return result;
result=add(x,y)
```
Pour tester cela, enregistrez les lignes de code ci-dessus dans votre répertoire local en tant que `add.py` et exécutez la commande suivante

```bash
mssqlctl-pre app create --name add-app --version v1 --runtime Python --code ./add.py  --inputs x=int,y=int --outputs result=int 
```

Vous pouvez vérifier si l’application est déployée à l’aide de la commande list :

```bash
mssqlctl-pre app list
```

Si le déploiement n’est pas terminé vous devez voir « state » affiche « Création » : 

```
[
  {
    "name": "add-app",
    "state": "Creating",
    "version": "v1"
  }
]
```

Une fois le déploiement réussi, vous devez voir « État » modifier à l’état « Prêt » :

```
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Une application de liste

Vous pouvez répertorier toutes les applications qui ont été créées avec le `app list` commande.

La commande suivante répertorie toutes les applications disponibles dans votre cluster big data :

```bash
mssqlctl-pre app list
```

Si vous spécifiez un nom et la version, il répertorie cette application spécifique et son état (création ou prêt) :

```bash
mssqlctl-pre app list --name <app_name> --version <app_version>
```

L’exemple suivant illustre cette commande :

```bash
mssqlctl-pre app list --name add-app --version v1
```

Vous devez voir une sortie similaire à l’exemple suivant :

```
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Exécuter une application

Si l’application est dans un état « Prêt », vous pouvez l’utiliser en l’exécutant avec vos paramètres d’entrée spécifiés. Pour exécuter une application, utilisez la syntaxe suivante :

```bash
mssqlctl-pre app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

L’exemple de commande suivant montre la commande d’exécution :

```bash
mssqlctl-pre app run --name add-app --version v1 --inputs x=1,y=2
```

Si l’exécution a réussi, vous devez voir votre sortie comme spécifié lors de la création de l’application. Voici un exemple.

```
{
  "changedFiles": [],
  "consoleOutput": "",
  "errorMessage": "",
  "outputFiles": {},
  "outputParameters": {
    "result": 3
  },
  "success": true
}
```

## <a name="delete-an-app"></a>Supprimer une application

Pour supprimer une application à partir de votre cluster de données volumineux, utilisez la syntaxe suivante :

```bash
mssqlctl-pre app delete --name add-app --version v1
```

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez également consulter des exemples supplémentaires à [ https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster). 

Pour plus d’informations sur les clusters de données volumineuses de SQL Server, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
