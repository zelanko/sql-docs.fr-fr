---
title: Utiliser des applications sur des clusters Big Data
titleSuffix: SQL Server big data clusters
description: Utilisez une application déployée sur un cluster Big Data SQL Server 2019 à l’aide d’un service web RESTful (préversion).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a2135ef64fb17eba62eab75b81739eda047167ab
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419510"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Utiliser une application déployée sur un cluster Big Data SQL Server à l’aide d’un service web RESTful

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment utiliser une application déployée sur un cluster Big Data SQL Server 2019 à l’aide d’un service web RESTful (préversion).

## <a name="prerequisites"></a>Prérequis

- [Cluster Big Data SQL Server 2019](deployment-guidance.md)
- [Utilitaire de ligne de commande mssqlctl](deploy-install-azdata.md)
- Application déployée avec [azdata](big-data-cluster-create-apps.md) ou l’[extension de déploiement d’application](app-deployment-extension.md)

## <a name="capabilities"></a>Fonctions

Après avoir déployé une application sur votre cluster Big Data SQL Server 2019 (préversion), vous pouvez accéder à cette application et l’utiliser à l’aide d’un service web RESTful. Vous pouvez ainsi intégrer cette application à partir d’autres applications ou services (par exemple, une application mobile ou un site web). Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **azdata** pour obtenir des informations sur le service web RESTful pour votre application.

|Commande |Description |
|:---|:---|
|`azdata app describe` | Décrit l’application. |

Vous pouvez utiliser le paramètre `--help` pour obtenir de l’aide, comme dans l’exemple suivant :

```bash
azdata app describe --help
```

Les sections suivantes décrivent comment récupérer un point de terminaison pour une application et comment utiliser le service web RESTful pour l’intégration d’applications.

## <a name="retrieve-the-endpoint"></a>Récupérer le point de terminaison

La commande **azdata app describe** fournit des informations détaillées sur l’application, notamment le point de terminaison de votre cluster. Ces informations sont généralement utilisées par les développeurs pour créer une application à l’aide du client Swagger et du service web pour interagir avec l’application de manière RESTful.

Décrivez votre application en exécutant une commande semblable à la suivante :

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

Notez l’adresse IP (`10.1.1.3` dans cet exemple) et le numéro de port (`30777`) dans la sortie.

## <a name="generate-a-jwt-access-token"></a>Générer un jeton d’accès JWT

Pour accéder au service web RESTful pour l’application que vous avez déployée, vous devez d’abord générer un jeton d’accès JWT. Ouvrez l’URL `https://[IP]:[PORT]/api/docs/swagger.json` dans votre navigateur à l’aide de l’adresse IP et du port que vous avez récupérés en exécutant la commande `describe` ci-dessus. Connectez-vous avec les mêmes informations d’identification que celles utilisées pour `azdata login`.

Collez le contenu de `swagger.json` dans [Swagger Editor](https://editor.swagger.io) pour comprendre les méthodes disponibles :

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Notez la méthode GET `app` et la méthode POST `token`. Étant donné que l’authentification des applications utilise des jetons JWT, vous devez obtenir un jeton à l’aide de votre outil favori pour effectuer un appel POST à la méthode`token`. Voici un exemple de la procédure à suivre dans [Postman](https://www.getpostman.com/) :

![Jeton Postman](media/big-data-cluster-consume-apps/postman_token.png)

Cette demande génère un `access_token` JWT avec lequel devez appeler l’URL pour exécuter l’application.

## <a name="execute-the-app-using-the-restful-web-service"></a>Exécuter l’application à l’aide du service web RESTful

> [!NOTE]
> Si vous le souhaitez, vous pouvez ouvrir l’URL de `swagger` qui a été retournée quand vous avez exécuté `azdata app describe --name [appname] --version [version]` dans votre navigateur, ce qui doit être similaire à `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`. Connectez-vous avec les mêmes informations d’identification que celles utilisées pour `azdata login`. Collez le contenu du fichier `swagger.json` dans [Swagger Editor](https://editor.swagger.io). Vous pouvez voir que le service web expose la méthode `run`. Notez également l’URL de base affichée en haut.

Vous pouvez utiliser votre outil favori pour appeler la méthode `run` (`https://[IP]:30778/api/app/[appname]/[version]/run`), en passant les paramètres dans le corps de votre demande POST au format JSON. Dans cet exemple, nous utilisons [Postman](https://www.getpostman.com/). Avant d’effectuer l’appel, vous devez définir `Authorization` avec la valeur `Bearer Token` et coller le jeton récupéré précédemment. Un en-tête est alors défini dans votre demande. Consultez la capture d’écran ci-dessous.

![En-têtes d’exécution Postman](media/big-data-cluster-consume-apps/postman_run_1.png)

Ensuite, dans le corps de la demande, passez les paramètres à l’application que vous appelez et définissez `content-type` avec la valeur `application/json` :

![Corps d’exécution Postman](media/big-data-cluster-consume-apps/postman_run_2.png)

Quand vous envoyez la demande, vous obtenez la même sortie que celle générée lors de l’exécution de l’application avec `azdata app run` :

![Résultat d’exécution Postman](media/big-data-cluster-consume-apps/postman_result.png)

L’application a été appelée par le biais du service web. Vous pouvez suivre des étapes similaires pour intégrer ce service web dans votre application.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez également consulter d’autres [exemples de déploiement d’application](https://aka.ms/sql-app-deploy).

Pour plus d’informations sur les clusters Big Data SQL Server, consultez [Présentation des clusters Big Data SQL Server 2019](big-data-cluster-overview.md).
