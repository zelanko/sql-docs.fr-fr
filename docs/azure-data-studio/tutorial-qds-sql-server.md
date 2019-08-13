---
title: 'Tutoriel : Activer le widget d’exemple qui affiche les cinq requêtes les plus lentes'
titleSuffix: Azure Data Studio
description: Ce didacticiel montre comment activer le widget qui affiche les cinq requêtes les plus lentes dans le tableau de bord de la base de données.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 5c94d2cf8b80ad7724cc1f710dc67d3f4a13c59e
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959064"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Tutoriel : Ajouter le widget d’exemple *cinq requêtes les plus lentes* au tableau de bord de la base de données

Ce didacticiel montre le processus d’ajout d’un widget d’exemple intégré de [!INCLUDE[name-sos](../includes/name-sos-short.md)] au *tableau de bord de la base de données* pour afficher rapidement les cinq requêtes les plus lentes d’une base de données. Vous allez également apprendre à afficher les détails des requêtes lentes et les plans de requête à l’aide des fonctionnalités de [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> * Activer le Magasin des requêtes sur une base de données
> * Ajouter un widget d’insight prédéfini au tableau de bord de la base de données
> * Afficher des détails sur les requêtes les plus lentes de la base de données
> * Afficher les plans d’exécution de requête pour les requêtes lentes

[!INCLUDE[name-sos](../includes/name-sos-short.md)] comprend plusieurs widgets d’insight prêts à l’emploi. Ce didacticiel montre comment ajouter le widget *query-data-store-db-insight*, mais les étapes sont fondamentalement les mêmes pour l’ajout de n’importe quel widget.

## <a name="prerequisites"></a>Conditions préalables requises

Ce didacticiel nécessite la base de données *TutorialDB* de SQL Server ou Azure SQL Database. Pour créer la base de données *TutorialDB*, suivez un des démarrages rapides suivants :

- [Se connecter à et interroger SQL Server avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter à et interroger Azure SQL Database avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



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

2. Saisissez *dashboard* dans la zone de recherche de paramètres et recherchez **dashboard.database.widgets**.

   ![Rechercher des paramètres](./media/tutorial-qds-sql-server/search-settings.png)

3. Pour personnaliser les paramètres **dashboard.database.widgets**, vous devez modifier l'entrée **dashboard.database.widgets** dans la section **PARAMÈTRES UTILISATEUR** (la colonne du côté droit). S’il n’existe pas de **dashboard.database.widgets** dans la section **PARAMÈTRES UTILISATEUR**, placez le curseur sur le texte **dashboard.database.widgets** dans la colonne PARAMÈTRES PAR DÉFAUT et cliquez sur l’icône de crayon qui apparaît à gauche du texte et cliquez sur **Copier vers les paramètres**. Si la fenêtre contextuelle indique **Remplacer dans les paramètres**, ne cliquez pas dessus ! Accédez à la colonne **PARAMÈTRES UTILISATEUR** à droite et recherchez la section **dashboard.database.widgets** et passez à l’étape suivante.

4. Dans la section **dashboard.database.widgets**, ajoutez ce qui suit :

   ```json
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
    ```

1. S’il s’agit de la première fois que vous ajoutez un nouveau widget, la section **dashboard.database.widgets** doit ressembler à ceci :

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

1. Appuyez sur **Ctrl+S** pour enregistrer les **Paramètres utilisateur**.

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

1. Ouvrez un nouvel éditeur de requête en appuyant sur **Ctrl + N**.

2. Collez le texte de la requête des étapes précédentes dans l’éditeur.

3. Cliquez sur **Expliquer**.

   ![Expliquer insight QDS](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Affichez le plan d’exécution de la requête :

   ![plan d'exécution de requêtes](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Enregistrer et ouvrir un plan de requête 

1. Ouvrez la boîte de dialogue détails de l’insight.
2. Sélectionnez un des éléments de la requête.
2. Cliquez avec le bouton droit sur la valeur **query_plan** et sélectionnez **Copier la cellule**

   ![Plan d’insights QDS](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. Appuyez sur **Ctrl+N** pour ouvrir un nouvel éditeur.

4. Collez le plan copié dans l’éditeur.

5. Appuyez sur **Ctrl+S** pour enregistrer le fichier et remplacez l’extension de fichier par *.sqlplan*. *.sqlplan* n’apparaît pas dans la liste déroulante d’extensions de fichier, vous devez donc saisir l’extension directement. Pour ce didacticiel, nommez le fichier *slowquery.sqlplan*.

6. Le plan de requête s'ouvre dans la visionneuse du plan de requête de [!INCLUDE[name-sos](../includes/name-sos-short.md)] :

   ![Plan d’insights QDS](./media/tutorial-qds-sql-server/sqlplan.png)


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
