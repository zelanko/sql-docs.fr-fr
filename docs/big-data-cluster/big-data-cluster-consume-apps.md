---
title: Utiliser des applications sur des clusters Big Data
titleSuffix: SQL Server big data clusters
description: Consommez une application déployée sur le cluster SQL Server 2019 Big Data à l’aide d’un service Web RESTful (version préliminaire).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a2135ef64fb17eba62eab75b81739eda047167ab
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419510"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Utilisation d’une application déployée sur SQL Server Cluster Big Data à l’aide d’un service Web RESTful

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment utiliser une application déployée sur un cluster SQL Server 2019 Big Data à l’aide d’un service Web RESTful (version préliminaire).

## <a name="prerequisites"></a>Prérequis

- [Cluster SQL Server 2019 Big Data](deployment-guidance.md)
- [utilitaire de ligne de commande mssqlctl](deploy-install-azdata.md)
- Une application déployée à l’aide de [azdata](big-data-cluster-create-apps.md) ou de l' [extension App deploy](app-deployment-extension.md)

## <a name="capabilities"></a>Fonctionnalités

Une fois que vous avez déployé une application sur votre cluster SQL Server 2019 Big Data (version préliminaire), vous pouvez accéder à cette application et l’utiliser à l’aide d’un service Web RESTful. Cela permet l’intégration de cette application à partir d’autres applications ou services (par exemple, une application mobile ou un site Web). Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **azdata** pour obtenir des informations sur le service Web RESTful pour votre application.

|Command |Description |
|:---|:---|
|`azdata app describe` | Décrire l’application. |

Vous pouvez obtenir de l’aide `--help` sur le paramètre comme dans l’exemple suivant:

```bash
azdata app describe --help
```

Les sections suivantes décrivent comment récupérer un point de terminaison pour une application et comment utiliser le service Web RESTful pour l’intégration d’applications.

## <a name="retrieve-the-endpoint"></a>Récupérer le point de terminaison

La commande **azdata App DESCRIBE** fournit des informations détaillées sur l’application, y compris le point de terminaison de votre cluster. Il est généralement utilisé par un développeur d’applications pour créer une application à l’aide du client Swagger et utiliser le service Web pour interagir avec l’application de manière RESTful.

Décrivez votre application en exécutant une commande semblable à la suivante:

```bash
azdata app describe --name addpy --version v1
```

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
    "app": "https://10.1.1.3:30777/api/app/addpy/v1",
    "swagger": "https://10.1.1.3:30777/api/app/addpy/v1/swagger.json"
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

Notez l’adresse IP (`10.1.1.3` dans cet exemple) et le numéro de port`30777`() dans la sortie.

## <a name="generate-a-jwt-access-token"></a>Générer un jeton d’accès JWT

Pour accéder au service Web RESTful pour l’application que vous avez déployée, vous devez d’abord générer un jeton d’accès JWT. Ouvrez l’URL suivante dans votre navigateur: `https://[IP]:[PORT]/api/docs/swagger.json` à l’aide de l’adresse IP et du port `describe` que vous avez récupérés, en exécutant la commande ci-dessus. Vous devrez vous connecter avec les informations d’identification que vous avez utilisées pour `azdata login`.

Collez le contenu de `swagger.json` dans l' [éditeur Swagger](https://editor.swagger.io) pour comprendre les méthodes disponibles:

![Swagger d’API](media/big-data-cluster-consume-apps/api_swagger.png)

Notez la `app` méthode de récupération ainsi que la `token` méthode de publication. Étant donné que l’authentification pour les applications utilise des jetons JWT, vous devez obtenir un jeton My à l’aide de votre outil favori pour effectuer `token` un appel postérieur à la méthode. Voici un exemple de la procédure à suivre dans la [publication](https://www.getpostman.com/):

![Jeton postal](media/big-data-cluster-consume-apps/postman_token.png)

Le résultat de cette demande vous donnera un JWT `access_token`, que vous devrez appeler pour exécuter l’application.

## <a name="execute-the-app-using-the-restful-web-service"></a>Exécuter l’application à l’aide du service Web RESTful

> [!NOTE]
> Si vous le souhaitez, vous pouvez ouvrir l’URL de `swagger` la qui a été retournée `azdata app describe --name [appname] --version [version]` lorsque vous avez exécuté dans votre navigateur, ce `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`qui doit être similaire à. Vous devrez vous connecter avec les informations d’identification que vous avez utilisées pour `azdata login`. Contenu du `swagger.json` que vous pouvez coller dans l' [éditeur Swagger](https://editor.swagger.io). Vous verrez que le service Web expose la `run` méthode. Notez également l’URL de base affichée en haut.

Vous pouvez utiliser votre outil favori pour appeler la `run` méthode (`https://[IP]:30778/api/app/[appname]/[version]/run`), en transmettant les paramètres dans le corps de votre demande de publication au format JSON. Dans cet exemple, nous allons utiliser le [billet](https://www.getpostman.com/). Avant d’effectuer l’appel, vous devrez définir le `Authorization` à `Bearer Token` et coller dans le jeton que vous avez récupéré précédemment. Cela permet de définir un en-tête dans votre demande. Consultez la capture d’écran ci-dessous.

![En-têtes de lancement](media/big-data-cluster-consume-apps/postman_run_1.png)

Ensuite, dans le corps de la requête, transmettez les paramètres à l’application que vous appelez et `content-type` affectez à `application/json`la valeur:

![Corps d’exécution postale](media/big-data-cluster-consume-apps/postman_run_2.png)

Lorsque vous envoyez la demande, vous obtiendrez la même sortie que lorsque vous avez exécuté l’application via `azdata app run`:

![Résultat de l’exécution du billet](media/big-data-cluster-consume-apps/postman_result.png)

L’application a été appelée avec succès par le biais du service Web. Vous pouvez suivre des étapes similaires pour intégrer ce service Web dans votre application.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez également consulter des exemples supplémentaires dans les [exemples de déploiement d’applications](https://aka.ms/sql-app-deploy).

Pour plus d’informations sur les clusters Big Data SQL Server, consultez [que sont les clusters Big Data SQL Server 2019?](big-data-cluster-overview.md).
