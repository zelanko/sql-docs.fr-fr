---
title: Utiliser des applications sur des clusters Big Data SQL Server
titleSuffix: SQL Server big data clusters
description: Utilisation d’une application déployée sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] à l’aide d’un service Web RESTful (version préliminaire).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bd7d5e0093d3805679e59b542582c263dfd56c9c
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978292"
---
# <a name="consume-an-app-deployed-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-using-a-restful-web-service"></a>Utilisation d’une application déployée sur [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] à l’aide d’un service Web RESTful

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment utiliser une application déployée sur un cluster Big Data SQL Server 2019 à l’aide d’un service web RESTful (préversion).

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data SQL Server 2019](deployment-guidance.md)
- [Utilitaire de ligne de commande azdata](deploy-install-azdata.md)
- Application déployée avec [azdata](big-data-cluster-create-apps.md) ou l’[extension de déploiement d’application](app-deployment-extension.md)

## <a name="capabilities"></a>Fonctionnalités

Une fois que vous avez déployé une application [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]sur votre, vous pouvez accéder à cette application et l’utiliser à l’aide d’un service Web RESTful. Vous pouvez ainsi intégrer cette application à partir d’autres applications ou services (par exemple, une application mobile ou un site web). Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **azdata** pour obtenir des informations sur le service web RESTful pour votre application.

|Command |Description |
|:---|:---|
|`azdata app describe` | Décrit l’application. |

Vous pouvez utiliser le paramètre `--help` pour obtenir de l’aide, comme dans l’exemple suivant :

```bash
azdata app describe --help
```

Les sections suivantes décrivent comment récupérer un point de terminaison pour une application et comment utiliser le service web RESTful pour l’intégration d’applications.

## <a name="retrieve-the-endpoint"></a>Récupérer le point de terminaison

La commande **azdata app describe** fournit des informations détaillées sur l’application, notamment le point de terminaison de votre cluster. Ces informations sont généralement utilisées par les développeurs pour créer une application à l’aide du client Swagger et du service web pour interagir avec l’application de manière RESTful.

Décrivez votre application en exécutant une commande semblable à l’exemple suivant :

```bash
azdata app describe --name add-app --version v1
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
    "app": "https://10.1.1.3:30080/app/addpy/v1",
    "swagger": "https://10.1.1.3:30080/app/addpy/v1/swagger.json"
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

Notez l’adresse IP (`10.1.1.3` dans cet exemple) et le numéro de port (`30080`) dans la sortie.

L’une des autres méthodes permettant d’obtenir ces informations consiste à cliquer avec le bouton droit sur gérer sur le serveur dans Azure Data Studio où vous trouverez les points de terminaison des services listés.

![Point de terminaison ADS](media/big-data-cluster-consume-apps/ads_end_point.png)

## <a name="generate-a-jwt-access-token"></a>Générer un jeton d’accès JWT

Pour accéder au service web RESTful pour l’application que vous avez déployée, vous devez d’abord générer un jeton d’accès JWT. Ouvrez l’URL `https://[IP]:[PORT]/docs/swagger.json` dans votre navigateur à l’aide de l’adresse IP et du port que vous avez récupérés en exécutant la commande `describe` ci-dessus. Vous devrez vous connecter avec les informations d’identification que vous avez utilisées pour `azdata login`.

Collez le contenu de `swagger.json` dans [Swagger Editor](https://editor.swagger.io) pour comprendre les méthodes disponibles :

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Notez la méthode GET `app` et la méthode POST `token`. Étant donné que l’authentification pour les applications utilise des jetons JWT, vous devez obtenir un jeton My à l’aide de votre outil favori pour effectuer un `token` appel postérieur à la méthode. Voici un exemple de la procédure à suivre dans [Postman](https://www.getpostman.com/) :

![Jeton Postman](media/big-data-cluster-consume-apps/postman_token.png)

Le résultat de cette demande vous donnera un jeton JWT `access_token`, que vous devrez appeler pour exécuter l’application.

## <a name="execute-the-app-using-the-restful-web-service"></a>Exécuter l’application à l’aide du service web RESTful

> [!NOTE]
> Si vous le souhaitez, vous pouvez ouvrir l’URL de `swagger` qui a été retournée quand vous avez exécuté `azdata app describe --name [appname] --version [version]` dans votre navigateur, ce qui doit être similaire à `https://[IP]:[PORT]/app/[appname]/[version]/swagger.json`. Connectez-vous avec les mêmes informations d’identification que celles utilisées pour `azdata login`. Collez le contenu du fichier `swagger.json` dans [Swagger Editor](https://editor.swagger.io). Vous pouvez voir que le service web expose la méthode `run`. Notez également l’URL de base affichée en haut.

Vous pouvez utiliser votre outil favori pour appeler la méthode `run` (`https://[IP]:30778/api/app/[appname]/[version]/run`), en passant les paramètres dans le corps de votre demande POST au format JSON. Dans cet exemple, nous allons utiliser le [billet](https://www.getpostman.com/). Avant d’effectuer l’appel, vous devez définir `Authorization` avec la valeur `Bearer Token` et coller le jeton récupéré précédemment. Un en-tête est alors défini dans votre demande. Consultez la capture d’écran ci-dessous.

![En-têtes d’exécution Postman](media/big-data-cluster-consume-apps/postman_run_1.png)

Ensuite, dans le corps de la demande, passez les paramètres à l’application que vous appelez et définissez `content-type` avec la valeur `application/json` :

![Corps d’exécution Postman](media/big-data-cluster-consume-apps/postman_run_2.png)

Quand vous envoyez la demande, vous obtenez la même sortie que celle générée lors de l’exécution de l’application avec `azdata app run` :

![Résultat d’exécution Postman](media/big-data-cluster-consume-apps/postman_result.png)

L’application a été appelée par le biais du service web. Vous pouvez suivre des étapes similaires pour intégrer ce service web dans votre application.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez également consulter d’autres [exemples de déploiement d’application](https://aka.ms/sql-app-deploy).

Pour plus d’informations [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]sur, consultez [que [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]sont ?](big-data-cluster-overview.md).
