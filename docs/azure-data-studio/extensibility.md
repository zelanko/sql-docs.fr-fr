---
title: Ajout de fonctionnalités supplémentaire par le biais d’extensibilité
titleSuffix: Azure Data Studio
description: En savoir plus sur le modèle d’extensibilité et les zones d’extensibilité clé pour étendre les fonctionnalités d’Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: ea432d05ea1fde8ec0d2585d0618ea6feba86ccc
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801928"
---
# <a name="getting-started-with-includename-sosincludesname-sos-shortmd-extensibility"></a>Prise en main [!INCLUDE[name-sos](../includes/name-sos-short.md)] extensibilité

[!INCLUDE[name-sos](../includes/name-sos.md)] a plusieurs mécanismes d’extensibilité pour personnaliser l’expérience utilisateur et de proposer ces personnalisations à la Communauté des utilisateurs entière. Le cœur [!INCLUDE[name-sos](../includes/name-sos.md)] plateforme repose sur Visual Studio Code, par conséquent, la plupart des API d’extensibilité de Visual Studio Code est disponible. En outre, nous vous avons fourni des points d’extensibilité supplémentaires pour les activités spécifiques à la gestion de données.

Les points d’extensibilité clés sont notamment :

- Extensibilité de Visual Studio Code API
- Extension Data Studio Azure, outils de création
- Gérer les contributions de panneau onglet tableau de bord
- Insights avec les expériences d’Actions
- API d’extensibilité Data Studio Azure
- API du fournisseur de données personnalisées

## <a name="visual-studio-code-extensibility-apis"></a>Extensibilité de Visual Studio Code API

Étant donné que le noyau [!INCLUDE[name-sos](../includes/name-sos.md)] plateforme repose sur Visual Studio Code, plus d’informations sur les API d’extensibilité de Visual Studio Code sont trouvent dans le [création d’extensions](https://code.visualstudio.com/docs/extensions/overview) et [API d’Extension](https://code.visualstudio.com/docs/extensionAPI/overview) documentation sur le site Web de Visual Studio Code.

## <a name="manage-dashboard-tab-panel-contributions"></a>Gérer les contributions de panneau onglet tableau de bord

Pour plus d’informations, consultez [Contribution Points](#contribution-points) et [Variables de contexte](#context-variables).

## <a name="azure-data-studio-extensibility-apis"></a>API d’extensibilité Data Studio Azure

Pour plus d’informations, consultez [API d’extensibilité](extensibility-apis.md).


## <a name="contribution-points"></a>Points de contribution

Cette section aborde les différents points de contribution qui sont définis dans le manifeste d’extension package.json.

IntelliSense est prise en charge à l’intérieur d’azuredatastudio.

## <a name="contributes-dashboard"></a>Contribue de tableau de bord

Contribuer onglet, conteneur, widget insight au tableau de bord.

![Tableau de bord](media/extensibility/dashboard-page.png)

`dashboard.tabs`

Dashboard.Tabs crée les sections d’onglet à l’intérieur de la page tableau de bord. Il attend un objet ou un tableau d’objets.  

```json
"dashboard.tabs": [
{
    "id": "test-tab1",
    "title": "Test 1",
    "description": "The test 1 displays a list of widgets.",
    "when": "connectionProvider == 'MSSQL' && !mssql:iscloud",
    "alwaysShow": true,
    "container": {
        ...
    }
}
]
```

`dashboard.containers`

Au lieu de spécifier un tableau de bord conteneur inline (à l’intérieur du dashboard.tab). Vous pouvez inscrire des conteneurs à l’aide de dashboard.containers. Il accepte un objet ou un tableau de l’objet.

```json
"dashboard.containers": [
{
    "id": "innerTab1",
    "container": {
        ...
    }
},
{
    "id": "innerTab2",
    "container": {
       ...
    }
}
]
```

Pour faire référence au conteneur inscrit, spécifiez l’id du conteneur

```json
"dashboard.tabs": [
{
    ...
    "container": {
        "innerTab1": {             
        }
    }
}
]

```

`dashboard.insights`

Vous pouvez inscrire des insights à l’aide de dashboard.insights. Cela revient à [didacticiel : Générer un widget d’analyse personnalisée](https://docs.microsoft.com/sql/sql-operations-studio/tutorial-build-custom-insight-sql-server)

```json
"dashboard.insights": {
"id": "my-widget"
"type": {
    "count": {
        "dataDirection": "vertical",
        "dataType": "number",
        "legendPosition": "none",
           "labelFirstColumn": false,
        "columnsAsLabels": false
       }
   },
   "queryFile": "{your file folder}/activeSession.sql"
}
```


### <a name="dashboard-container-types"></a>Types de conteneurs de tableau de bord

Il existe actuellement quatre types de conteneurs pris en charge :

1. `widgets-container`

    ![Conteneur de widgets](media/extensibility/widgets-container.png)

    La liste de widgets qui s’affichera dans le conteneur. Il est une mise en page fluide. Il accepte la liste de widgets.

    ```json
    "container": {
        "widgets-container": [
        {
            "widget": {
                "query-data-store-db-insight": {
                }
            }
        },
        {
            "widget": {
                "explorer-widget": {
                }
            }
        }
      ]
    }
    ```

2. `webview-container`

    ![conteneur de WebView](media/extensibility/webview-container.png)

    L’affichage Web s’affichera dans l’intégralité du conteneur. Il attend id webview pour être que le même ID de l’onglet se trouve

    ```json
    "container": {
        "webview-container": null
    }
    ```

3. `grid-container`

   ![conteneur de la grille](media/extensibility/grid-container.png)

   La liste des widgets ou des vues Web qui s’affichera dans la disposition de grille

    ```json
    "container": {
        "grid-container": [
        {
            "name": "widget 1",
            "widget": {
                "explorer-widget": {
                }
            },
            "row":0,
            "col":0
        },
        {
            "name": "widget 2",
            "widget": {
                "tasks-widget": {
                    "backup", 
                    "restore",
                    "configureDashboard",
                    "newQuery"
                }
            },
            "row":0,
            "col":1
        },
        {
            "name": "Webview 1",
            "webview": {
                "id": "google"
            },
            "row":1,
            "col":0,
            "colspan":2
        },
        {
            "name": "widget 3",
            "widget": {
                "explorer-widget": {}
            },
            "row":0,
            "col":3,
            "rowspan":2
        },
    ]
    ```

4.  `nav-section`

    ![section de navigation](media/extensibility/nav-section.png)

    La section de navigation s’affichera dans le conteneur

    ```json
    "container": {
        "nav-section": [
            {
                "id": "innerTab1",
                "title": "inner-tab1",
                "icon": {
                    "light": "./icons/tab1Icon.svg",
                    "dark": "./icons/tab1Icon_dark.svg"
                }
                "container": {
                    ...
                }
            },
            {
                "id": "innerTab2",
                "title": "inner-tab2",
                "icon": {
                    "light": "./icons/tab2Icon.svg",
                    "dark": "./icons/tab2Icon_dark.svg"
                }
                "container": {
                    ...
                }
            }
        ]
    }
    ```



## <a name="context-variables"></a>Variables de contexte

Pour obtenir des informations générales sur le contexte dans Visual Studio Code et par la suite d’Azure Data Studio, consultez [extensibilité](https://code.visualstudio.com/docs/extensionAPI/extension-points#_example).

Dans Azure Data Studio, nous avons un contexte spécifique autour des connexions de base de données disponibles pour les extensions.

### <a name="dashboard"></a>Tableau de bord

Dans le tableau de bord, nous fournissons les variables de contexte suivantes :

|variable de contexte| description|
|:---|:---|
|`connectionProvider` | Une chaîne de l’identificateur pour le fournisseur de la connexion actuelle. Ex. `connectionProvider == 'MSSQL'` .|
|`serverName`|Chaîne du nom du serveur de la connexion actuelle. Ex. `serverName == 'localhost'` .|
|`databaseName` | Chaîne du nom de base de données de la connexion actuelle. Ex. `databaseName == 'master'` .|
|`connection` | L’objet de profil de connexion complète pour la connexion actuelle (IConnectionProfile)|
|`dashboardContext` | Une chaîne du contexte de la page du tableau de bord est actuellement placé. « Base de données » ou « server ». Ex. `dashboardContext == 'database'`|
