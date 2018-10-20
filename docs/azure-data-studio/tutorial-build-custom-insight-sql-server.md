---
title: 'Didacticiel : Créer un widget d’analyse personnalisée dans Azure Data Studio | Microsoft Docs'
description: Ce didacticiel montre comment créer des widgets d’analyse personnalisées et ajoutez-les à la base de données et serveur des tableaux de bord dans Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: caecf780f5c8cc656f6b0b2a95dd3d68c48355cb
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356340"
---
# <a name="tutorial-build-a-custom-insight-widget"></a>Didacticiel : Créer un widget d’analyse personnalisée

Ce didacticiel montre comment utiliser vos propres requêtes insight pour créer des widgets d’analyse personnalisés.

Au cours de ce didacticiel, vous découvrez comment :
> [!div class="checklist"]
> * Exécuter votre propre requête et l’afficher dans un graphique
> * Générer un widget d’analyse personnalisée à partir du graphique
> * Ajouter le graphique à un tableau de bord de serveur ou de base de données
> * Ajouter des détails à votre widget analyse personnalisée

## <a name="prerequisites"></a>Prerequisites

Ce didacticiel requiert SQL Server ou la base de données SQL Azure *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter et interroger à l’aide de la base de données SQL Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Exécuter votre propre requête et afficher le résultat dans une vue graphique
Dans cette étape, exécutez un script sql pour interroger les sessions actives en cours.

1. Pour ouvrir un nouvel éditeur, appuyez sur **Ctrl + N**. 

2. Modifier le contexte de connexion au **TutorialDB**.

3. Collez la requête suivante dans l’éditeur de requête :

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Enregistrer la requête dans l’éditeur pour un \*fichier .sql. Pour ce didacticiel, enregistrez le script sous *activeSession.sql*.

5. Pour exécuter la requête, appuyez sur **F5**.

6. Une fois les résultats de requête sont affichés, cliquez sur **vue en tant que graphique**, puis cliquez sur le **visionneuse de graphique** onglet.

7. Modification **Type de graphique** à **nombre**. Ces paramètres restituent un graphique de nombre.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Ajouter l’analyse personnalisée au tableau de bord de base de données

1. Pour ouvrir la configuration du widget insight, cliquez sur **Insight créer** sur *visionneuse de graphique*:

   ![configuration](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Copier la configuration de l’analyse (les données JSON). 

3. Appuyez sur **Ctrl + virgule** pour ouvrir *paramètres utilisateur*.

4. Type *tableau de bord* dans *les paramètres de recherche*.

5. Cliquez sur **modifier** pour *dashboard.database.widgets*.

   ![paramètres de tableau de bord](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Collez la configuration d’analyse JSON dans *dashboard.database.widgets*. Base de données du tableau de bord paramètres ressemble à ceci :

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
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
            }
        }
    ]
   ```

7. Enregistrer le *paramètres utilisateur* de fichiers et ouvrir le *TutorialDB* tableau de bord de base de données pour voir le widget de sessions actives :

   ![activesession insight](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>Ajouter les détails d’analyse personnalisée

1. Pour ouvrir un nouvel éditeur, appuyez sur **Ctrl + N**.

2. Modifier le contexte de connexion au **TutorialDB**.

3. Collez la requête suivante dans l’éditeur de requête :

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Enregistrer la requête dans l’éditeur pour un \*fichier .sql. Pour ce didacticiel, enregistrez le script sous *activeSessionDetail.sql*.

5. Appuyez sur **Ctrl + virgule** pour ouvrir *paramètres utilisateur*.

6. Modifier existants *dashboard.database.widgets* nœud dans votre fichier de paramètres :

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql",
                    "details": {
                        "queryFile": "{your file folder}/activeSessionDetail.sql",
                        "label": "SID",
                        "value": "Login Name"
                    }
                }
            }
        }
    ]
   ```

7. Enregistrer le *paramètres utilisateur* de fichiers et ouvrir le *TutorialDB* tableau de bord de base de données. Cliquez sur le bouton de sélection (...) en regard *mes Widget* pour afficher les détails :

    ![activesession insight](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Exécuter votre propre requête et l’afficher dans un graphique
> * Générer un widget d’analyse personnalisée à partir du graphique
> * Ajouter le graphique à un tableau de bord de serveur ou de base de données
> * Ajouter des détails à votre widget analyse personnalisée

Pour savoir comment sauvegarder et restaurer des bases de données, suivre le didacticiel suivant :

> [!div class="nextstepaction"]
> [Sauvegarde et restauration des bases de données](tutorial-backup-restore-sql-server.md).
