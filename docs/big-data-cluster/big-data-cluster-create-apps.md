---
title: Déployer des applications à l’aide de azdata
titleSuffix: SQL Server big data clusters
description: Déployez un script Python ou R en tant qu’application sur le cluster SQL Server 2019 Big Data (version préliminaire).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 06b76e7eb8eec8db1993ca558a1f57355457c4ad
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419485"
---
# <a name="how-to-deploy-an-app-on-sql-server-big-data-cluster-preview"></a>Comment déployer une application sur SQL Server Cluster Big Data (version préliminaire)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment déployer et gérer des scripts R et Python en tant qu’application à l’intérieur d’un cluster SQL Server 2019 Big Data (version préliminaire).

## <a name="whats-new-and-improved"></a>Nouveautés et améliorations

- Un utilitaire de ligne de commande unique pour gérer le cluster et l’application.
- Simplification du déploiement d’applications tout en fournissant un contrôle granulaire via des fichiers de spécifications.
- Prise en charge de l’hébergement de types d’applications supplémentaires-SSIS et MLeap (nouveauté dans CTP 2,3)
- [Extension de vs code](app-deployment-extension.md) pour gérer le déploiement d’applications

Les applications sont déployées et `azdata` gérées à l’aide de l’utilitaire de ligne de commande. Cet article fournit des exemples de déploiement d’applications à partir de la ligne de commande. Pour savoir comment l’utiliser dans Visual Studio Code consultez [vs code extension](app-deployment-extension.md).

Les types d’applications suivants sont pris en charge:
- Applications R et Python (fonctions, modèles et applications)
- Service MLeap
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>Prérequis

- [Cluster SQL Server 2019 Big Data](deployment-guidance.md)
- [utilitaire de ligne de commande azdata](deploy-install-azdata.md)

## <a name="capabilities"></a>Fonctionnalités

Dans SQL Server 2019 (version préliminaire), vous pouvez créer, supprimer, décrire, initialiser, répertorier et mettre à jour votre application. Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **azdata**.

|Command |Description |
|:---|:---|
|`azdata login` | Connectez-vous à un cluster SQL Server Big Data |
|`azdata app create` | Créer une application. |
|`azdata app delete` | Supprimer l’application. |
|`azdata app describe` | Décrire l’application. |
|`azdata app init` | Kickstart nouveau squelette d’application. |
|`azdata app list` | Répertorier les applications. |
|`azdata app run` | Exécutez l’application. |
|`azdata app update`| Mettre à jour l’application. |

Vous pouvez obtenir de l’aide `--help` sur le paramètre comme dans l’exemple suivant:

```bash
azdata app create --help
```

Les sections suivantes décrivent ces commandes plus en détail.

## <a name="sign-in"></a>Connexion

Avant de déployer ou d’interagir avec des applications, connectez-vous d’abord à votre cluster `azdata login` SQL Server Big Data à l’aide de la commande. Spécifiez l’adresse IP externe du `controller-svc-external` service (par exemple: `https://ip-address:30080`), ainsi que le nom d’utilisateur et le mot de passe du cluster.

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>AKS

Si vous utilisez AKS, vous devez exécuter la commande suivante pour obtenir l’adresse IP du `mgmtproxy-svc-external` service en exécutant cette commande dans une fenêtre bash ou cmd:


```bash
kubectl get svc mgmtproxy-svc-external -n <name of your big data cluster>
```

## <a name="kubeadm-or-minikube"></a>Kubeadm ou Minikube

Si vous utilisez Kubeadm ou Minikube, exécutez la commande suivante pour récupérer l’adresse IP pour se connecter au cluster

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Créer une application

Pour créer une application, utilisez `azdata` avec la `app create` commande. Ces fichiers résident localement sur l’ordinateur à partir duquel vous créez l’application.

Pour créer une application dans Big Data cluster, utilisez la syntaxe ci-après:

```bash
azdata app create --spec <directory containing spec file>
```

La commande suivante affiche un exemple de ce à quoi peut ressembler cette commande:

```bash
azdata app create --spec ./addpy
```

Cela suppose que votre application est stockée dans le `addpy` dossier. Ce dossier doit également contenir un fichier de spécification pour l’application, `spec.yaml`appelé. Pour plus d’informations sur le `spec.yaml` fichier, consultez [la page déploiement de l’application](concept-application-deployment.md) .

Pour déployer cet exemple d’application d’application, créez les fichiers suivants dans un `addpy`répertoire appelé:

- `add.py`. Copiez le code python suivant dans ce fichier:
   ```py
   #add.py
   def add(x,y):
        result = x+y
        return result
    result=add(x,y)
   ```
- `spec.yaml`. Copiez le code suivant dans ce fichier:
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

Exécutez ensuite la commande ci-dessous:

```bash
azdata app create --spec ./addpy
```

Vous pouvez vérifier si l’application est déployée à l’aide de la commande list:

```bash
azdata app list
```

Si le déploiement n’est pas terminé, vous devriez `state` voir `WaitingforCreate` s’afficher comme dans l’exemple suivant:

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

Une fois le déploiement réussi, vous devez voir la `state` modification de `Ready` l’État:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Répertorier une application

Vous pouvez répertorier toutes les applications qui ont été correctement `app list` créées avec la commande.

La commande suivante répertorie toutes les applications disponibles dans votre cluster Big Data:

```bash
azdata app list
```

Si vous spécifiez un nom et une version, il répertorie cette application spécifique et son état (création ou prêt):

```bash
azdata app list --name <app_name> --version <app_version>
```

L’exemple suivant illustre cette commande:

```bash
azdata app list --name add-app --version v1
```

Une sortie similaire à l’exemple suivant doit s’afficher:

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

Si l’application est dans un `Ready` État, vous pouvez l’utiliser en l’exécutant avec les paramètres d’entrée spécifiés. Pour exécuter une application, utilisez la syntaxe ci-après:

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

L’exemple de commande suivant illustre la commande exécuter:

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Si l’exécution a réussi, vous devez voir votre sortie telle que spécifiée lors de la création de l’application. Voici un exemple.

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

La commande init fournit une structure avec les artefacts appropriés nécessaires au déploiement d’une application. L’exemple ci-dessous crée Hello. pour ce faire, exécutez la commande suivante.

```bash
azdata app init --name hello --version v1 --template python
```

Cela créera un dossier appelé Hello.  Vous pouvez `cd` dans le répertoire et inspecter les fichiers générés dans le dossier. Spec. YAML définit l’application, telle que le nom, la version et le code source. Vous pouvez modifier la spécification pour modifier le nom, la version, l’entrée et les sorties.

Voici un exemple de sortie de la commande init que vous verrez dans le dossier

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>Décrire une application

La commande DESCRIBE fournit des informations détaillées sur l’application, y compris le point de terminaison de votre cluster. Il est généralement utilisé par un développeur d’applications pour créer une application à l’aide du client Swagger et utiliser le service Web pour interagir avec l’application de manière RESTful. Pour plus d’informations, consultez [utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md) .

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
    "app": "https://10.1.1.3:30777/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30777/api/app/add-app/v1/swagger.json"
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

Pour supprimer une application de votre cluster Big Data, utilisez la syntaxe suivante:

```bash
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment intégrer des applications déployées sur des clusters de SQL Server Big Data dans vos propres applications pour [utiliser des applications sur des clusters Big Data](big-data-cluster-consume-apps.md) pour plus d’informations. Vous pouvez également consulter des exemples supplémentaires dans les [exemples de déploiement d’applications](https://aka.ms/sql-app-deploy).

Pour plus d’informations sur les clusters Big Data SQL Server, consultez [que sont les clusters Big Data SQL Server 2019?](big-data-cluster-overview.md).
