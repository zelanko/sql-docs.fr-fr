---
title: Déployer des applications avec azdata
titleSuffix: SQL Server big data clusters
description: Déployez un script Python ou R en tant qu' [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]application sur.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 18e97a3567b50982bd2be11dcc3493951dfe8fa9
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653157"
---
# <a name="how-to-deploy-an-app-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Comment déployer une application sur[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment déployer et gérer des scripts R et Python en tant qu’application à l’intérieur d’un cluster SQL Server 2019 Big Data.

## <a name="whats-new-and-improved"></a>Nouveautés et améliorations

- Un même utilitaire de ligne de commande pour la gestion du cluster et de l’application
- Simplification du déploiement des applications et contrôle granulaire à l’aide de fichiers de spécifications
- Prise en charge de l’hébergement de types d’applications supplémentaires-SSIS et MLeap (nouveauté dans CTP 2,3).
- [Extension de Visual Studio code](app-deployment-extension.md) pour gérer le déploiement d’applications.

Les applications sont déployées et gérées à l’aide de l’utilitaire de ligne de commande `azdata`. Cet article fournit des exemples de déploiement d’applications à partir de la ligne de commande. Pour savoir comment l’utiliser dans Visual Studio Code consultez [Visual Studio code extension](app-deployment-extension.md).

Les types d’applications suivants sont pris en charge :
- Applications R et Python (fonctions, modèles et applications)
- MLeap Serving
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data SQL Server 2019](deployment-guidance.md)
- [Utilitaire de ligne de commande azdata](deploy-install-azdata.md)

## <a name="capabilities"></a>Fonctionnalités

Dans SQL Server 2019 (préversion), vous pouvez créer, supprimer, décrire, initialiser, lister et mettre à jour votre application. Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **azdata**.

|Command |Description |
|:---|:---|
|`azdata login` | Pour se connecter à un cluster Big Data SQL Server |
|`azdata app create` | Pour créer une application |
|`azdata app delete` | Pour supprimer une application |
|`azdata app describe` | Pour décrire une application |
|`azdata app init` | Pour démarrer le squelette d’une nouvelle application |
|`azdata app list` | Pour lister les applications |
|`azdata app run` | Pour exécuter une application |
|`azdata app update`| Pour mettre à jour une application |

Vous pouvez utiliser le paramètre `--help` pour obtenir de l’aide, comme dans l’exemple suivant :

```bash
azdata app create --help
```

Les sections suivantes décrivent ces commandes de façon plus détaillée.

## <a name="sign-in"></a>Connexion

Avant de déployer ou d’utiliser les applications, connectez-vous à votre cluster Big Data SQL Server à l’aide de la commande `azdata login`. Spécifiez l’adresse IP externe du service `controller-svc-external` (par exemple, `https://ip-address:30080`), ainsi que le nom d’utilisateur et le mot de passe du cluster.

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>AKS

Si vous utilisez AKS, vous devez exécuter la commande suivante pour obtenir l’adresse IP du service `controller-svc-external` en exécutant cette commande dans une fenêtre bash ou cmd :


```bash
kubectl get svc controller-svc-external -n <name of your big data cluster>
```

## <a name="kubeadm-or-minikube"></a>Kubeadm ou Minikube

Si vous utilisez Kubeadm ou Minikube, exécutez la commande suivante pour demander à l’adresse IP de se connecter au cluster

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Créer une application

Pour créer une application, utilisez `azdata` avec la commande `app create`. Ces fichiers résident localement sur la machine à partir de laquelle vous créez l’application.

Pour créer une application sur un cluster Big Data, utilisez la syntaxe suivante :

```bash
azdata app create --spec <directory containing spec file>
```

La commande suivante montre ce à quoi cela peut ressembler :

```bash
azdata app create --spec ./addpy
```

Cela suppose que votre application est stockée dans le dossier `addpy`. Ce dossier doit également contenir un fichier de spécifications (nommé `spec.yaml`) pour l’application. Pour plus d’informations sur le `spec.yaml` fichier, consultez [la page déploiement de l’application](concept-application-deployment.md) .

Pour déployer cet exemple d’application, créez les fichiers suivants dans un répertoire appelé `addpy` :

- `add.py` . Copiez le code Python suivant dans ce fichier :
   ```py
   #add.py
  def add(x, y):
    result = x+y
    return result
  result=add(x,y)
   ```
- `spec.yaml` . Copiez le code suivant dans ce fichier :
   ```yaml
   #spec.yaml
   name: add-app #name of your python script
   version: v1  #version of the app
   runtime: Python #the language this app uses (R or Python)
   src: ./add.py #full path to the location of the app
   entrypoint: add #the function that will be called upon execution
   replicas: 1  #number of replicas needed
   poolsize: 1  #the pool size that you need your app to scale
   inputs:  #input parameters that the app expects and the type
     x: int
     y: int
   output: #output parameter the app expects and the type
     result: int
   ```

Ensuite, exécutez la commande ci-dessous :

```bash
azdata app create --spec ./addpy
```

Vous pouvez vérifier si l’application est déployée à l’aide de la commande list :

```bash
azdata app list
```

Si le déploiement n’est pas terminé, `state` doit afficher `WaitingforCreate`, comme dans l’exemple suivant :

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

Une fois le déploiement réussi, l’état de `state` doit passer à `Ready` :

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Lister une application

Vous pouvez lister toutes les applications qui ont été créées à l’aide de la commande `app list`.

La commande suivante liste toutes les applications qui sont disponibles dans votre cluster Big Data :

```bash
azdata app list
```

Si vous spécifiez un nom et une version, la commande liste une application et son état (En cours de création ou Prêt) :

```bash
azdata app list --name <app_name> --version <app_version>
```

L’exemple ci-dessous montre cette commande :

```bash
azdata app list --name add-app --version v1
```

Vous devez obtenir une sortie similaire à la suivante :

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Exécuter une application

Si l’état de l’application est `Ready`, vous pouvez l’utiliser en l’exécutant avec les paramètres d’entrée spécifiés. Utilisez la syntaxe suivante pour exécuter une application :

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

L’exemple suivant montre la commande run :

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Si l’exécution a réussi, vous devez voir votre sortie telle que vous l’avez spécifiée lors de la création de l’application. Voici un exemple.

```json
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

## <a name="create-an-app-skeleton"></a>Créer un squelette d’application

La commande init fournit une structure avec les artefacts nécessaires au déploiement d’une application. L’exemple ci-dessous crée « hello », en exécutant la commande suivante.

```bash
azdata app init --name hello --version v1 --template python
```

Cela crée un dossier nommé « hello ».  Vous pouvez `cd` dans le répertoire et inspecter les fichiers générés dans le dossier. Spec. YAML définit l’application, telle que le nom, la version et le code source. Vous pouvez modifier la spécification pour modifier le nom, la version, l’entrée et les sorties.

Voici un exemple de sortie de la commande init que vous verrez dans le dossier.

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>Décrire une application

La commande describe fournit des informations détaillées sur l’application, notamment le point de terminaison de votre cluster. Ces informations sont généralement utilisées par les développeurs pour créer une application à l’aide du client Swagger et du service web pour interagir avec l’application de manière RESTful. Pour plus d’informations, consultez [Utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md).

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30080/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30080/api/app/add-app/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

## <a name="delete-an-app"></a>Supprimer une application

Pour supprimer une application de votre cluster Big Data, utilisez la syntaxe suivante :

```bash
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment intégrer des applications déployées [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] dans vos propres applications pour [utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md) pour plus d’informations. Vous pouvez également consulter d’autres [exemples de déploiement d’application](https://aka.ms/sql-app-deploy).

Pour plus d’informations [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]sur, consultez [que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]sont?](big-data-cluster-overview.md).
