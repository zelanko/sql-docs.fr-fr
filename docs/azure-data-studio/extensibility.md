---
title: Ajout de fonctionnalités supplémentaires via l’extensibilité
titleSuffix: Azure Data Studio
description: Apprenez-en davantage sur le modèle d’extensibilité et les domaines d’extensibilité clés pour étendre les fonctionnalités d’Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 20158894567c1452a8d605f5cec84354654c5e96
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959597"
---
# <a name="getting-started-with-includename-sosincludesname-sos-shortmd-extensibility"></a>Prise en main de l’extensibilité [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos.md)] dispose de plusieurs mécanismes d’extensibilité pour personnaliser l’expérience utilisateur et rendre ces personnalisations accessibles à l’ensemble de la communauté d’utilisateurs. La plateforme [!INCLUDE[name-sos](../includes/name-sos.md)] principale repose sur Visual Studio Code, ainsi la plupart des API d’extensibilité de Visual Studio Code sont disponibles. En outre, nous avons fourni des points d’extensibilité supplémentaires pour des activités spécifiques à la gestion des données.

Voici quelques-uns des principaux points d’extensibilité :

- API d’extensibilité de Visual Studio Code
- Outils de création d’extensions Azure Data Studio
- Gestion des contributions du panneau des onglets du tableau de bord
- Insights avec les expériences Actions
- API d’extensibilité d’Azure Data Studio
- API Fournisseur de données personnalisées

## <a name="visual-studio-code-extensibility-apis"></a>API d’extensibilité de Visual Studio Code

Étant donné que la plateforme principale [!INCLUDE[name-sos](../includes/name-sos.md)] repose sur Visual Studio Code, vous trouverez des détails sur les API d’extensibilité de Visual Studio Code dans les documentations [Création d’extensions](https://code.visualstudio.com/docs/extensions/overview) et [API d’extension](https://code.visualstudio.com/docs/extensionAPI/overview) sur le site web Visual Studio Code.

## <a name="manage-dashboard-tab-panel-contributions"></a>Gestion des contributions du panneau des onglets du tableau de bord

Pour plus d’informations, consultez [Points de contribution](#contribution-points) et [Variables de contexte](#context-variables).

## <a name="azure-data-studio-extensibility-apis"></a>API d’extensibilité d’Azure Data Studio

Pour plus d’informations, consultez [API d’extensibilité](extensibility-apis.md).


## <a name="contribution-points"></a>Points de contribution

Cette section décrit les différents points de contribution définis dans le manifeste de l’extension package.json.

IntelliSense est pris en charge dans Azure Data Studio.

## <a name="contributes-dashboard"></a>Tableau de bord de contributions

Onglet contribution, conteneur, widget insight dans le tableau de bord.

![Tableau de bord](media/extensibility/dashboard-page.png)

`dashboard.tabs`

Dashboard.tabs crée les sections d’onglets sur la page de tableau de bord. Il attend un objet ou un tableau d’objets,  

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

au lieu de spécifier le conteneur du tableau de bord inclus (dans le dashboard.tab). Vous pouvez inscrire des conteneurs à l’aide de dashboard.containers. Il accepte un objet ou un tableau d’objets.

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

Pour faire référence au conteneur inscrit, spécifiez l’ID du conteneur

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

Vous pouvez enregistrer des insights à l’aide de dashboard.insights. Cela est similaire au [Didacticiel : Créer un widget insight personnalisé](https://docs.microsoft.com/sql/sql-operations-studio/tutorial-build-custom-insight-sql-server)

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

Quatre types de conteneur sont actuellement pris en charge :

1. `widgets-container`

    ![Conteneur de widgets](media/extensibility/widgets-container.png)

    Liste des widgets qui seront affichés dans le conteneur. Il s’agit d’une mise en page fluide. Il accepte la liste des widgets.

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

    ![Conteneur d’affichage web](media/extensibility/webview-container.png)

    La vue d’affichage web s’affichera dans l’intégralité du conteneur. Elle s’attend à ce que l’ID d’affichage web soit le même que l’ID de l’onglet

    ```json
    "container": {
        "webview-container": null
    }
    ```

3. `grid-container`

   ![Conteneur de grille](media/extensibility/grid-container.png)

   Liste des widgets ou des affichages web qui seront affichés dans la disposition de la grille

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

    ![Section de navigation](media/extensibility/nav-section.png)

    La section de navigation s’affiche dans le conteneur

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

Pour obtenir des informations générales sur le contexte dans Visual Studio Code et Azure Data Studio, consultez [Extensibilité](https://code.visualstudio.com/docs/extensionAPI/extension-points#_example).

Dans Azure Data Studio, nous avons un contexte spécifique pour les connexions de base de données disponibles pour les extensions.

### <a name="dashboard"></a>Tableau de bord

Dans le tableau de bord, nous fournissons les variables de contexte suivantes :

|Variable de contexte| description|
|:---|:---|
|`connectionProvider` | Chaîne de l’identificateur pour le fournisseur de la connexion actuelle. Ex. `connectionProvider == 'MSSQL'`.|
|`serverName`|Chaîne de nom du serveur de la connexion actuelle. Ex. `serverName == 'localhost'`.|
|`databaseName` | Chaîne de nom de la base de données de la connexion actuelle. Ex. `databaseName == 'master'`.|
|`connection` | Objet de profil de connexion complet pour la connexion actuelle (IConnectionProfile)|
|`dashboardContext` | Une chaîne de contexte de la page du tableau de bord est actuellement activée. Il s’agit de « Base de données » ou de « Serveur ». Ex. `dashboardContext == 'database'`|
