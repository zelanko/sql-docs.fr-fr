---
title: 'Didacticiel : Activer les cinq requêtes les plus lentes exemple widget - Studio de données Azure | Microsoft Docs'
description: Ce didacticiel montre comment activer le widget d’exemple requêtes les plus lentes cinq sur le tableau de bord de base de données.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 839f72a83d45f49004f0bbfb876baadbeaafdeea
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038534"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Didacticiel : Ajouter la *cinq requêtes les plus lentes* widget exemple au tableau de bord de base de données

Ce didacticiel illustre le processus d’ajout d’un des [!INCLUDE[name-sos](../includes/name-sos-short.md)]de widgets exemples intégrés pour le *tableau de bord de base de données* pour afficher rapidement les requêtes les plus lentes cinq une base de données. Vous allez également apprendre à afficher les détails des requêtes lentes et plans de requête à l’aide [!INCLUDE[name-sos](../includes/name-sos-short.md)]de fonctionnalités. Au cours de ce didacticiel, vous découvrez comment :

> [!div class="checklist"]
> * Activer le Store de requête sur une base de données
> * Ajouter un widget insight prédéfinis au tableau de bord de base de données
> * Afficher les détails sur les requêtes les plus lentes de la base de données
> * Afficher les plans d’exécution pour les requêtes lentes

[!INCLUDE[name-sos](../includes/name-sos-short.md)] inclut plusieurs insight widgets out-of-the-box. Ce didacticiel montre comment ajouter la *query-data-store-db-insight* widget, mais les étapes sont essentiellement les mêmes pour l’ajout d’un widget.

## <a name="prerequisites"></a>Configuration requise

Ce didacticiel requiert SQL Server ou la base de données SQL Azure *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter et interroger à l’aide de la base de données SQL Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>Activer le Store de la requête pour votre base de données

Le widget dans cet exemple nécessite *requête Store* doit être activé.

1. Bouton droit sur le **TutorialDB** base de données (dans le **serveurs** encadré) et sélectionnez **nouvelle requête**.
2. Collez l’instruction Transact-SQL (T-SQL) suivante dans l’éditeur de requête, puis cliquez sur **exécuter**:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>Ajouter le widget de requêtes lentes à votre tableau de bord de base de données

Pour ajouter le *ralentir le widget de requêtes* à votre tableau de bord, vous devez modifier le *dashboard.database.widgets* définissant dans votre *paramètres utilisateur* fichier.

1. Ouvrez *paramètres utilisateur* en appuyant sur **Ctrl + Maj + P** pour ouvrir le *Palette de commandes*.
2. Type *paramètres* dans la zone de recherche, puis sélectionnez **préférences : ouvrir les paramètres utilisateur**.

   ![Commande de paramètres utilisateur ouvertes](./media/tutorial-qds-sql-server/open-user-settings.png)

2. Type *tableau de bord* dans la recherche de paramètres et recherchez **dashboard.database.widgets**.

   ![Paramètres de recherche](./media/tutorial-qds-sql-server/search-settings.png)

3. Pour personnaliser le **dashboard.database.widgets** paramètres, vous devez modifier le **dashboard.database.widgets** entrée dans le **paramètres utilisateur** section (la colonne dans le côté droit). S’il existe aucune **dashboard.database.widgets** dans le **paramètres utilisateur** section, placez le curseur sur le **dashboard.database.widgets** texte dans la colonne de paramètres par défaut et cliquez sur l’icône de crayon qui apparaît à gauche du texte et cliquez sur **copie aux paramètres**. Si la fenêtre contextuelle indique **remplacer dans les paramètres**, ne cliquez pas dessus ! Accédez à la **paramètres utilisateur** colonne vers la droite et recherchez le **dashboard.database.widgets** section et passez à l’étape suivante.

4. Dans le **dashboard.database.widgets** section, ajoutez le code suivant :

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

1. Si c’est la première fois, ajout d’un nouveau widget, le **dashboard.database.widgets** section doit ressembler à ceci :

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

1. Appuyez sur **Ctrl + S** pour enregistrer la modification **paramètres utilisateur**.

6. Ouvrez le *tableau de bord de base de données* en accédant à **TutorialDB** dans le **serveurs** encadré, avec le bouton droit et sélectionnez **gérer**.

   ![Tableau de bord ouvert](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Le widget insight s’affiche sur le tableau de bord : 

   ![Widget QDS](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>Afficher les détails d’un aperçu pour plus d’informations

1. Pour afficher des informations supplémentaires pour un widget d’un aperçu, cliquez sur le bouton de sélection (**...** ) dans le coin supérieur droit et sélectionnez **afficher les détails**.
2. Pour afficher plus de détails sur un élément, sélectionnez un élément de **données du graphique** liste.

   ![Boîte de dialogue Détail Insight](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Avec le bouton droit de la cellule située à droite de **query_sql_txt** dans **détails de l’élément** et cliquez sur **copier la cellule**.

4. Fermer le **Insights** volet.

## <a name="view-the-query-plan"></a>Afficher le plan de requête 

1. Ouvrez un nouvel éditeur de requête en appuyant sur **Ctrl + N**.

2. Collez le texte de requête de l’étape précédente dans l’éditeur.

3. Cliquez sur **expliquent**.

   ![Expliquez Insight QDS](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Afficher le plan d’exécution de la requête :

   ![plan d'exécution de requêtes](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Enregistrer et ouvrir un plan de requête 

1. Ouvrez la boîte de dialogue Détail insight.
2. Sélectionnez un des éléments de la requête.
2. Avec le bouton droit **query_plan** valeur et sélectionnez **copier la cellule**

   ![Insights QDS plan](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. Appuyez sur **Ctrl + N** pour ouvrir un nouvel éditeur.

4. Collez le plan copié dans l’éditeur.

5. Appuyez sur **Ctrl + S** pour enregistrer le fichier et remplacez l’extension de fichier par *.sqlplan*. *.sqlplan* ne pas apparaître dans la liste déroulante extension de fichier, donc, tapez-la dans. Pour ce didacticiel, nommez le fichier *slowquery.sqlplan*.

6. Le plan de requête s’ouvre dans [!INCLUDE[name-sos](../includes/name-sos-short.md)]de visionneuse de plan de requête :

   ![Insights QDS plan](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Activer le Store de requête sur une base de données
> * Ajouter un widget d’insight au tableau de bord de base de données
> * Afficher les détails sur les requêtes les plus lentes de la base de données
> * Afficher les plans d’exécution pour les requêtes lentes


Pour savoir comment activer la **utilisation de l’espace de table** exemple d’analyse, de suivre le didacticiel suivant :

> [!div class="nextstepaction"]
> [Activer le widget de tableau espace exemple insight](tutorial-table-space-sql-server.md)
