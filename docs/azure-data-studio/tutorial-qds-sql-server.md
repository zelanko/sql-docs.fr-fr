---
title: Activer le widget d’exemple qui affiche les cinq requêtes les plus lentes
titleSuffix: Azure Data Studio
description: Ce didacticiel montre comment activer le widget qui affiche les cinq requêtes les plus lentes dans le tableau de bord de la base de données.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 08/02/2019
ms.openlocfilehash: 3f940f0f18df676eae2ca101a2eccaa2be7169e2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "74957043"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Tutoriel : Ajouter le widget d’exemple *cinq requêtes les plus lentes* au tableau de bord de la base de données

Ce didacticiel montre le processus d’ajout d’un widget d’exemple intégré de [!INCLUDE[name-sos](../includes/name-sos-short.md)] au *tableau de bord de la base de données* pour afficher rapidement les cinq requêtes les plus lentes d’une base de données. Vous allez également apprendre à afficher les détails des requêtes lentes et les plans de requête à l’aide des fonctionnalités de [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> * Activer le Magasin des requêtes sur une base de données
> * Ajouter un widget d’insight prédéfini au tableau de bord de la base de données
> * Afficher des détails sur les requêtes les plus lentes de la base de données
> * Afficher les plans d’exécution de requête pour les requêtes lentes

[!INCLUDE[name-sos](../includes/name-sos-short.md)] comprend plusieurs widgets d’insight prêts à l’emploi. Ce didacticiel montre comment ajouter le widget *query-data-store-db-insight*, mais les étapes sont fondamentalement les mêmes pour l’ajout de n’importe quel widget.

## <a name="prerequisites"></a>Prérequis

Ce didacticiel nécessite la base de données *TutorialDB* de SQL Server ou Azure SQL Database. Pour créer la base de données *TutorialDB*, suivez un des démarrages rapides suivants :

* [Se connecter à et interroger SQL Server avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)

* [Se connecter à et interroger Azure SQL Database avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)

## <a name="turn-on-query-store-for-your-database"></a>Activez le Magasin des requêtes pour votre base de données

Dans cet exemple, le widget requiert l’activation du *Magasin des requêtes*.

1. Cliquez avec le bouton droit sur la base de données **TutorialDB** (dans la barre latérale **SERVEURS**) et sélectionnez **Nouvelle requête**.

2. Collez l’instruction Transact-SQL suivante dans l’éditeur de requête et cliquez sur **Exécuter** :

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>Ajouter le widget de requêtes lentes au tableau de bord de votre base de données

Pour ajouter le *widget de requêtes lentes* à votre tableau de bord, modifiez le paramètre *dashboard.database.widgets* dans votre fichier de *Paramètres utilisateur*.

1. Ouvrez les *Paramètres utilisateur* en appuyant sur **Ctrl+Maj+P** pour ouvrir la *Palette de commandes*.

2. Saisissez *préférences* dans la zone de recherche et sélectionnez **Préférences : Ouvrir les paramètres utilisateur**.

   ![Commande d’ouverture des paramètres utilisateur](./media/tutorial-qds-sql-server/open-user-settings.png)

3. Saisissez *dashboard* dans la zone de recherche de paramètres, recherchez **dashboard.database.widgets**, puis cliquez sur *Modifier dans settings.json*.

   ![Rechercher des paramètres](./media/tutorial-qds-sql-server/search-settings.png)

4. Dans settings.json, ajoutez le code suivant :

   ```json
   "dashboard.database.widgets": [
       {
           "name": "slow queries widget",
           "gridItemConfig": {
               "sizex": 2,
               "sizey": 1
           },
           "widget": {
               "query-data-store-db-insight": null
           }
       },
       {
           "name": "Tasks",
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 1
           },
           "widget": {
               "tasks-widget": {}
           }
       },
       {
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 2
           },
           "widget": {
               "explorer-widget": {}
           }
       }
   ]
   ```

5. Appuyez sur **Ctrl+S** pour enregistrer les **Paramètres utilisateur**.

6. Ouvrez le *Tableau de bord de la base de données* en accédant à **TutorialDB** dans la barre latérale **SERVEURS**, cliquez avec le bouton droit, puis sélectionnez **Gérer**.

   ![Ouvrir le tableau de bord](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Le widget d’insight apparaît sur le tableau de bord :

   ![Widget QDS](./media/tutorial-qds-sql-server/insight-qds-result.png)

## <a name="view-insight-details-for-more-information"></a>Afficher les détails de l’insight pour plus d'informations

1. Pour afficher des informations supplémentaires sur un widget d’insight, cliquez sur les points de suspension ( **...** ) dans le coin supérieur droit, puis sélectionnez **Afficher les détails**.

2. Pour afficher plus de détails sur un élément, sélectionnez n’importe quel élément dans la liste **Données du graphique**.

   ![Boîte de dialogue de détails d’insight](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Cliquez avec le bouton droit sur la cellule située à droite de **query_sql_txt** dans les **Détails de l'élément**, puis cliquez sur **Copier la cellule**.

4. Fermez le volet **Insights**.

## <a name="view-the-query-plan"></a>Afficher le plan de requête

1. Cliquez avec le bouton droit sur la base de données **TutorialDB**, puis sélectionnez *Gérer*.

2. Sous *slow queries widget* : pour afficher des informations supplémentaires sur un widget d’insights, cliquez sur les points de suspension ( **...** ) situés en haut à droite, puis sélectionnez **Exécuter la requête**.

    ![Exécuter la requête](media/tutorial-qds-sql-server/run-query.png)

3. Vous devez maintenant voir une nouvelle fenêtre de requête avec les résultats.

    ![Résultats de l’exécution de la requête](media/tutorial-qds-sql-server/run-query-results.png)

4. Cliquez sur **Expliquer**.

   ![Expliquer insight QDS](./media/tutorial-qds-sql-server/insight-qds-explain.png)

5. Affichez le plan d’exécution de la requête :

   ![plan d'exécution de requêtes](./media/tutorial-qds-sql-server/showplan.png)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Activer le Magasin des requêtes sur une base de données
> * Ajouter un widget d’insight au tableau de bord de la base de données
> * Afficher des détails sur les requêtes les plus lentes de la base de données
> * Afficher les plans d’exécution de requête pour les requêtes lentes

Pour savoir comment activer l’exemple d’insight **d’utilisation de l’espace de table**, effectuez le didacticiel suivant :

> [!div class="nextstepaction"]
> [Activer le widget d’exemple d’aperçu d’espace de table](tutorial-table-space-sql-server.md)