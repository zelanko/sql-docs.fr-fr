---
title: "Didacticiel : Activer la table d’utilisation exemple insight le widget d’espace dans les opérations de SQL Studio (version préliminaire) | Documents Microsoft"
description: "Ce didacticiel montre comment activer la table d’utilisation exemple insight le widget d’espace sur le tableau de bord de base de données SQL opérations Studio (version préliminaire)."
ms.custom: tools|sos
ms.date: 11/15/2017
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
ms.openlocfilehash: 7c51c7d1804baa490e665d316a08d911038c9f11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Didacticiel : Activer la table d’espace d’utilisation exemple insight widget à l’aide[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Ce didacticiel montre comment activer un widget d’un aperçu du tableau de bord de base de données, en fournissant une vue en un coup de œil sur l’utilisation de l’espace pour toutes les tables dans une base de données. Au cours de ce didacticiel, vous apprendrez comment :

> [!div class="checklist"]
> * Activer rapidement un widget d’un aperçu à l’aide d’un exemple de widget insight intégrés
> * Afficher les détails d’utilisation d’espace de table
> * Filtrer les données et afficher les détails de l’étiquette sur un graphique d’analyse

## <a name="prerequisites"></a>Prerequisites

Ce didacticiel nécessite SQL Server ou la base de données SQL Azure *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Se connecter et interroger à l’aide de la base de données SQL Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Activer une vision de gestion sur [!INCLUDE[name-sos](../includes/name-sos-short.md)]du tableau de bord de base de données
[!INCLUDE[name-sos](../includes/name-sos-short.md)]a un widget exemples intégrés pour surveiller l’espace utilisé par les tables dans une base de données.

1. Ouvrez **paramètres utilisateur** en appuyant sur **Ctrl + Maj + P** pour ouvrir *Palette de commandes*, type *paramètres* dans la zone de recherche et sélectionnez  **Préférences : Ouvrez les paramètres de l’utilisateur**.

   ![Commande de paramètres utilisateur ouverts](./media/tutorial-table-space-sql-server/open-user-settings.png)

2. Type *tableau de bord* zone de recherche de paramètres d’entrée et recherchez **dashboard.database.widgets**.

   ![Paramètres de recherche](./media/tutorial-table-space-sql-server/search-settings.png)

3. Pour personnaliser le **dashboard.database.widgets** définition, placez le curseur sur l’icône de crayon à gauche de la **dashboard.database.widgets** texte, cliquez sur **modifier**  >  **Copie paramètres**.

4. À l’aide de [!INCLUDE[name-sos](../includes/name-sos-short.md)]de configurer les paramètres d’informations sur IntelliSense, *nom* pour le titre de widget, *gridItemConfig* pour la taille du widget, et *widget* en sélectionnant **table-espace-db-insight** dans la liste déroulante, comme indiqué dans la capture d’écran suivante :

   ![Paramètres d’analyse](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Appuyez sur **Ctrl + S** pour enregistrer les paramètres.

6. Tableau de bord de base de données ouverte en cliquant sur **TutorialDB** et cliquez sur **gérer**.

   ![Tableau de bord ouvert](./media/tutorial-table-space-sql-server/insight-open-dashboard.png)

7. Vue *espace utilisé par les tables* comme indiqué dans la capture d’écran suivante : 

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Travailler avec le graphique d’analyse

[!INCLUDE[name-sos](../includes/name-sos-short.md)]du graphique d’insight fournit des informations de filtrage et de pointage. Pour essayer les étapes suivantes :

1. Cliquez sur et activer/désactiver le *row_count* légende sur le graphique. [!INCLUDE[name-sos](../includes/name-sos-short.md)]Affiche ou masque les séries de données lorsque vous faites une légende ou désactiver.
    
2. Placez le pointeur de la souris sur le graphique. [!INCLUDE[name-sos](../includes/name-sos-short.md)]affiche plus d’informations sur l’étiquette de série de données et sa valeur comme indiqué dans la capture d’écran suivante.

   ![bascule du graphique et la légende](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Activer rapidement un widget d’un aperçu à l’aide d’un exemple de widget insight intégrés.
> * Afficher les détails d’utilisation d’espace de table.
> * Filtrer les données et afficher les détails de l’étiquette sur un graphique d’analyse

Pour savoir comment générer un widget insight personnalisées, exécutez le didacticiel suivant :

> [!div class="nextstepaction"]
> [Générer un widget insight personnalisé](tutorial-build-custom-insight-sql-server.md).