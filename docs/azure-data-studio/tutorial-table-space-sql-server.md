---
title: 'Tutoriel : Activer le widget de tableau espace utilisation exemple insight'
titleSuffix: Azure Data Studio
description: Ce didacticiel montre comment activer le widget d’insight exemple de table espace l’utilisation du tableau de bord de base de données Azure Data Studio.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ebd3b1af1bc9b342ad6b2d33596e69b487888ced
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239511"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Tutoriel : Activer la table espace utilisation exemple insight widget à l’aide [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Ce didacticiel montre comment activer un widget d’un aperçu du tableau de bord de base de données, en fournissant une vue d’un coup de œil sur l’utilisation de l’espace pour toutes les tables dans une base de données. Au cours de ce didacticiel, vous découvrez comment :

> [!div class="checklist"]
> * Activez rapidement un widget d’insight à l’aide d’un exemple de widget insight intégrés
> * Afficher les détails d’utilisation d’espace de table
> * Filtrer les données et afficher les détails de l’étiquette sur un graphique insight

## <a name="prerequisites"></a>Configuration requise

Ce didacticiel requiert SQL Server ou la base de données SQL Azure *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter et interroger à l’aide de la base de données SQL Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Activer un insight de gestion sur [!INCLUDE[name-sos](../includes/name-sos-short.md)]du tableau de bord de base de données
[!INCLUDE[name-sos](../includes/name-sos-short.md)] comporte un widget exemples intégrés pour surveiller l’espace utilisé par les tables dans une base de données.

1. Ouvrez *paramètres utilisateur* en appuyant sur **Ctrl + Maj + P** pour ouvrir le *Palette de commandes*.
2. Type *paramètres* dans la zone de recherche, puis sélectionnez **préférences : Ouvrez les paramètres utilisateur**.
2. Type *tableau de bord* zone de recherche des paramètres d’entrée et recherchez **dashboard.database.widgets**.

3. Pour personnaliser le **dashboard.database.widgets** paramètres, vous devez modifier le **dashboard.database.widgets** entrée dans le **paramètres utilisateur** section (la colonne dans le côté droit). S’il existe aucune **dashboard.database.widgets** dans le **paramètres utilisateur** section, placez le curseur sur le **dashboard.database.widgets** texte dans la colonne de paramètres par défaut et cliquez sur l’icône de crayon qui apparaît à gauche du texte et cliquez sur **copie aux paramètres**. Si la fenêtre contextuelle indique **remplacer dans les paramètres**, ne cliquez pas dessus ! Accédez à la **paramètres utilisateur** colonne vers la droite et recherchez le **dashboard.database.widgets** section et passez à l’étape suivante.

4. Dans le **dashboard.database.widgets** section, ajoutez le code suivant :

   ```json
        {
            "name": "Space Used by Tables",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "table-space-db-insight": null
            }
        },
    ```
Le **dashboard.database.widgets** section doit ressembler à l’image suivante :

   ![Paramètres de recherche](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Appuyez sur **Ctrl + S** pour enregistrer les paramètres.

6. Tableau de bord de base de données ouvert en double-cliquant sur **TutorialDB** et cliquez sur **gérer**.

7. Afficher le *espace de table* widget insight comme indiqué dans l’image suivante : 

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Travailler avec le graphique insight

[!INCLUDE[name-sos](../includes/name-sos-short.md)]du graphique d’analyse fournit des informations de filtrage et de pointage de souris. Pour essayer les étapes suivantes :

1. Cliquez sur et activer/désactiver le *row_count* légende sur le graphique. [!INCLUDE[name-sos](../includes/name-sos-short.md)] affiche et masque la série de données que vous basculez une légende ou désactiver.
    
2. Placez le pointeur de la souris sur le graphique. [!INCLUDE[name-sos](../includes/name-sos-short.md)] affiche plus d’informations sur l’étiquette de série de données et sa valeur comme indiqué dans la capture d’écran suivante.

   ![Activer/désactiver graphique et la légende](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Activez rapidement un widget d’insight à l’aide d’un exemple de widget insight intégrés.
> * Afficher les détails d’utilisation d’espace de table.
> * Filtrer les données et afficher les détails de l’étiquette sur un graphique insight

Pour savoir comment générer un widget personnalisé insight, suivre le didacticiel suivant :

> [!div class="nextstepaction"]
> [Générer un widget personnalisé insight](tutorial-build-custom-insight-sql-server.md).
