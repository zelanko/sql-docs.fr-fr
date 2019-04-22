---
title: Utiliser les applications sur les clusters de données volumineuses
titleSuffix: SQL Server big data clusters
description: Consommer une application déployée sur SQL Server 2019 cluster de données volumineux à l’aide d’un service web RESTful (version préliminaire).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: jroth
manager: craigg
ms.date: 03/18/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4d299f364b4d67e1f31ce7c0e70d6ba062933f37
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860540"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Utiliser une application déployée sur un cluster de données volumineux de SQL Server à l’aide d’un service web RESTful

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment utiliser une application déployée sur un cluster de données volumineuses de SQL Server 2019 à l’aide d’un service web RESTful (version préliminaire).

## <a name="prerequisites"></a>Prérequis

- [Cluster de données volumineux de SQL Server 2019](deployment-guidance.md)
- [mssqlctl command-line utility](deploy-install-mssqlctl.md)
- Une application déployée à l’aide [ `mssqlctl` ](big-data-cluster-create-apps.md) ou [application déployer une extension](app-deployment-extension.md)

## <a name="capabilities"></a>Fonctions

Une fois que vous avez déployé une application sur votre cluster big data de SQL Server 2019 (version préliminaire), vous pouvez accéder et utiliser cette application à l’aide d’un service web RESTful. Cela permet l’intégration de cette application à partir d’autres applications ou services (par exemple, une application mobile ou un site Web). Le tableau suivant décrit les commandes de déploiement d’application que vous pouvez utiliser avec **mssqlctl** pour obtenir des informations sur le service web RESTful pour votre application.

|Command |Description |
|:---|:---|
|`mssqlctl app describe` | Décrire l’application. |

Vous pouvez obtenir de l’aide avec le `--help` paramètre comme dans l’exemple suivant :

```bash
mssqlctl app describe --help
```

Les sections suivantes décrivent comment récupérer un point de terminaison pour une application et comment utiliser le service web RESTful pour l’intégration de l’application.

## <a name="retrieve-the-endpoint"></a>Récupérer le point de terminaison

Le **mssqlctl application décrivent** commande fournit des informations détaillées sur l’application, y compris le point de terminaison dans votre cluster. Cela est généralement utilisé par un développeur d’application pour générer une application à l’aide du client de swagger et le service Web pour interagir avec l’application de manière RESTful.

Décrire votre application en exécutant une commande semblable à ce qui suit :

```bash
mssqlctl app describe --name addpy --version v1
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

Pour accéder au service web RESTful pour l’application que vous avez déployé, vous devez tout d’abord générer un jeton d’accès JWT. Ouvrez l’URL suivante dans votre navigateur : `https://[IP]:[PORT]/api/docs/swagger.json` à l’aide de l’adresse IP et le port que vous avez récupéré en cours d’exécution le `describe` commande ci-dessus. Vous devrez vous connecter avec les mêmes informations d’identification que vous avez utilisé pour `mssqlctl login`.

Collez le contenu de la `swagger.json` dans le [Swagger Editor](https://editor.swagger.io) de comprendre quelles méthodes sont disponibles :

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Notez que le `app` méthode GET ainsi que le `token` méthode POST. Étant donné que l’authentification pour les applications utilise des jetons JWT, vous devez obtenir un jeton à mon à l’aide de votre outil préféré pour effectuer un appel POST à la `token` (méthode). Voici un exemple montrant comment procéder [Postman](https://www.getpostman.com/):

![Jeton de postman](media/big-data-cluster-consume-apps/postman_token.png)

Le résultat de cette demande vous donnera un JWT `access_token`, que vous devez appeler l’URL pour exécuter l’application.

## <a name="execute-the-app-using-the-restful-web-service"></a>Exécutez l’application à l’aide du service web RESTful

> [!NOTE]
> Si vous le souhaitez, vous pouvez ouvrir l’URL pour le `swagger` qui a été retourné lors de l’exécution `mssqlctl app describe --name [appname] --version [version]` dans votre navigateur, qui doit être similaire à `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`. Vous devrez vous connecter avec les mêmes informations d’identification que vous avez utilisé pour `mssqlctl login`. Le contenu de la `swagger.json` vous pouvez coller dans [Swagger Editor](https://editor.swagger.io). Vous verrez que le service web expose le `run` (méthode). Notez également l’URL de Base affichée en haut.

Vous pouvez utiliser votre outil préféré pour appeler le `run` (méthode) (`https://[IP]:30778/api/app/[appname]/[version]/run`), en passant les paramètres dans le corps de votre demande POST en tant que json. Dans cet exemple, nous utiliserons [Postman](https://www.getpostman.com/). Avant d’effectuer l’appel, vous devez définir le `Authorization` à `Bearer Token` et collez dans le jeton que vous avez récupéré précédemment. Ceci définit un en-tête de votre demande. Consultez la capture d’écran ci-dessous.

![Postman exécuter en-têtes](media/big-data-cluster-consume-apps/postman_run_1.png)

Ensuite, dans le corps de demandes, transmettre les paramètres à l’application que vous appelez et définissez le `content-type` à `application/json`:

![Postman exécuter corps](media/big-data-cluster-consume-apps/postman_run_2.png)

Lorsque vous envoyez la demande, vous obtiendrez la même sortie que vous l’avez fait lorsque vous avez exécuté l’application `mssqlctl app run`:

![Résultat de l’exécution postman](media/big-data-cluster-consume-apps/postman_result.png)

Vous avez appelé désormais correctement l’application via le service web. Vous pouvez suivre des étapes similaires pour intégrer ce service web dans votre application.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez également consulter des exemples supplémentaires à [exemples de déploiement d’applications](https://aka.ms/sql-app-deploy).

Pour plus d’informations sur les clusters de données volumineuses de SQL Server, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
