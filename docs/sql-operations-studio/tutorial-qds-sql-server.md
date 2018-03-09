---
title: "Didacticiel : Activer les cinq premières requêtes exemple widget - opérations de SQL Studio (version préliminaire) | Documents Microsoft"
description: "Ce didacticiel montre comment activer le widget exemple requêtes les plus lents cinq sur le tableau de bord de base de données."
ms.custom: tools|sos
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc30051dff2bef07ac3e7d06aa98d92d4e05e79e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Didacticiel : Ajouter la *cinq premières requêtes* widget exemple au tableau de bord de base de données

Ce didacticiel illustre le processus d’ajout d’un des [!INCLUDE[name-sos](../includes/name-sos-short.md)]de widgets exemple intégrés à la *tableau de bord de base de données* pour afficher rapidement les cinq premières requêtes d’une base de données. Vous apprendrez également à afficher les détails des lenteur des requêtes et plans de requête à l’aide de [!INCLUDE[name-sos](../includes/name-sos-short.md)]de fonctionnalités. Au cours de ce didacticiel, vous apprendrez comment :

> [!div class="checklist"]
> * Activez le magasin de requête sur une base de données
> * Ajouter un widget insight prédéfinis au tableau de bord de base de données
> * Afficher les détails sur les requêtes les plus lents de la base de données
> * Afficher les plans d’exécution pour les requêtes lentes

[!INCLUDE[name-sos](../includes/name-sos-short.md)]inclut plusieurs insight widgets out-of-the-box. Ce didacticiel montre comment ajouter la *insight du db magasin de requête données* widget, mais les étapes sont les mêmes que pour l’ajout d’un widget.

## <a name="prerequisites"></a>Prerequisites

Ce didacticiel nécessite SQL Server ou la base de données SQL Azure *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter et interroger à l’aide de la base de données SQL Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>Activer le magasin de requêtes pour votre base de données

Le widget dans cet exemple nécessite *magasin de requêtes* soit activé donc exécuter l’instruction Transact-SQL (T-SQL) suivante sur votre base de données :

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-an-insight-widget-to-your-database-dashboard"></a>Ajouter un widget d’insight à votre tableau de bord de base de données

Pour ajouter un widget insight à votre tableau de bord, vous devez modifier le *dashboard.database.widgets* définition dans votre *paramètres utilisateur* fichier.

1. Ouvrez *paramètres utilisateur* en appuyant sur **Ctrl + Maj + P** pour ouvrir le *Palette de commandes*.
2. Type *paramètres* dans la zone de recherche et à partir des fichiers de paramètres disponibles, sélectionnez **préférences : ouvrir les paramètres utilisateur**.

   ![Commande de paramètres utilisateur ouverts](./media/tutorial-qds-sql-server/open-user-settings.png)

2. Type *tableau de bord* dans la recherche de paramètres et recherchez **dashboard.database.widgets**.

   ![Paramètres de recherche](./media/tutorial-qds-sql-server/search-settings.png)

3. Pour personnaliser le **dashboard.database.widgets** définition, placez le curseur sur l’icône de crayon à gauche de la **dashboard.database.widgets** texte, cliquez sur **modifier**  >  **Copie paramètres**.

4. Après avoir copié les paramètres pour **dashboard.database.widgets**, placez votre curseur à la fin de la ligne après la parenthèse ouvrante, appuyez sur **entrée**, puis ajoutez une accolade comme suit (l’accolade fermante s’affiche automatiquement) :

   ```json
   "dashboard.database.widgets": [
   {}
   ```
5. Placez votre curseur à l’intérieur des accolades, appuyez sur **Ctrl + espace** et sélectionnez **nom**. 
6. Terminer la configuration du widget afin qu’il ressemble à ceci :

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
        }
    ...
    ```

5. Appuyez sur **Ctrl + S** pour enregistrer la modification **paramètres utilisateur**.

6. Ouvrez le *tableau de bord de base de données* en accédant à **TutorialDB** dans les *serveurs* encadré, avec le bouton droit et sélectionnez **gérer**.

   ![Tableau de bord ouvert](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Le widget d’aperçu s’affiche sur le tableau de bord : 

   ![Widget QDS](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>Afficher les détails d’un aperçu pour plus d’informations

1. Pour afficher des informations supplémentaires pour un widget d’un aperçu, cliquez sur le bouton de sélection (**...** ) dans le coin supérieur droit, puis sélectionnez **afficher les détails**.
2. Pour afficher plus de détails sur un élément, sélectionnez un élément de **les données du graphique** liste.

   ![Boîte de dialogue Détails Insight](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Avec le bouton droit **query_sql_txt** dans **détails de l’élément** et cliquez sur **copier la cellule**.

4. Fermer le **Insights** volet.

## <a name="view-the-query-plan"></a>Afficher le plan de requête 

1. Ouvrez un nouvel éditeur de requête en appuyant sur **Ctrl + N**.

2. Collez le texte de requête de l’étape précédente dans l’éditeur.

3. Cliquez sur **expliquent**.

   ![Insight QDS expliquent](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Afficher le plan d’exécution de la requête :

   ![plan d'exécution de requêtes](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Enregistrez et ouvrez un plan de requête 

1. Ouvrez la boîte de dialogue Détail insight.
2. Sélectionnez un des éléments de la requête.
2. Avec le bouton droit **query_plan** valeur et sélectionnez **copier la cellule**

   ![Plan QDS Insights](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. Appuyez sur **Ctrl + N** pour ouvrir un nouvel éditeur.

4. Collez le plan copié dans l’éditeur.

5. Appuyez sur **Ctrl + S** pour enregistrer le fichier, modifier l’extension de fichier *.sqlplan*. Pour ce didacticiel, nommez le fichier *slowquery.sqlplan*.

6. Le plan de requête s’ouvre dans [!INCLUDE[name-sos](../includes/name-sos-short.md)]de visionneuse de plan de requête :

   ![Plan QDS Insights](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Activez le magasin de requête sur une base de données
> * Ajouter un widget insight au tableau de bord de base de données
> * Afficher les détails sur les requêtes les plus lents de la base de données
> * Afficher les plans d’exécution pour les requêtes lentes


Pour savoir comment activer la **utilisation de l’espace de table** exemple insight, effectuer le didacticiel suivant :

> [!div class="nextstepaction"]
> [Activer le widget de tableau espace exemple insight](tutorial-table-space-sql-server.md)