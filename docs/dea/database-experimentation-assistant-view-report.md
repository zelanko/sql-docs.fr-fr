---
title: Afficher les rapports d’analyse dans l’Assistant expérimentation de base de données pour les mises à niveau de SQL Server
description: Afficher les rapports d’analyse dans l’Assistant expérimentation de base de données
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
manager: jroth
ms.openlocfilehash: da99a24ab6729e78220aeed3d18819e7b075603f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794440"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Afficher les rapports d’analyse dans l’Assistant expérimentation de base de données

Après avoir [créer votre rapport d’analyse](database-experimentation-assistant-create-report.md) dans base de données expérimentation Compagnon (DEA), effectuez les étapes décrites dans cet article pour afficher le rapport et obtenir des informations de performances fournies par votre A / B test.

## <a name="select-a-server"></a>Sélectionnez un serveur

Dans la DEA, sélectionnez l’icône de menu. Dans le menu développé, sélectionnez **rapports d’analyse** près de l’icône de liste de vérification pour ouvrir la fenêtre de rapports d’analyse.

Sous **rapports d’analyse**, entrez le nom d’un ordinateur exécutant SQL Server qui a une base de données d’analyse. Sélectionnez **Se connecter**. 

![Se connecter à un rapport existant](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

S’il vous manque des dépendances, le **conditions préalables** page vous invite avec des liens vers les installer. Installer les composants requis, puis sélectionnez **réessayez**.

![Page Configuration requise](./media/database-experimentation-assistant-view-report/dea-view-report-prereq.png)

## <a name="select-an-analysis-report-to-view"></a>Sélectionnez un rapport d’analyse pour afficher

Dans la liste des rapports d’analyse, double-cliquez sur un rapport pour l’ouvrir.

![Afficher le rapport existant](./media/database-experimentation-assistant-view-report/dea-view-report-view-existing.png)

Vous pouvez obtenir des informations sur la façon dont votre charge de travail est représenté, comme illustré dans cet exemple de graphique :

![Graphiques de la charge de travail Rep](./media/database-experimentation-assistant-view-report/dea-view-report-workload-compare.png)

## <a name="view-and-understand-the-analysis-report"></a>Afficher et comprendre le rapport d’analyse

Cette section vous guide dans le rapport d’analyse.

### <a name="query-categories"></a>Catégories de la requête

Sélectionnez les différents segments du graphique à secteurs gauche pour afficher uniquement les requêtes qui font partie de cette catégorie.

![Secteurs de rapport](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

- **Détérioré requêtes**: Requêtes qui été plus performant dans A à b.  
- **Erreurs**: Requêtes pour afficher les erreurs dans l’instance B, mais pas dans l’instance A.  
- **Amélioration des requêtes**: Requêtes exécutées dans l’instance B à mieux dans l’instance A.  
- **Requêtes indéterminés**: Requêtes qui comportait une modification de performances indéterminé.  
- **Même**: Requêtes dans laquelle performances restent identiques entre les instances A et B.

### <a name="individual-query-drill-down"></a>Requête individuelle Descendre

Vous pouvez sélectionner les liens du modèle de requête pour afficher des informations plus détaillées sur des requêtes spécifiques.

![Requête d’exploration](./media/database-experimentation-assistant-view-report/dea-view-report-drilldown.png)

Sélectionnez une requête spécifique pour ouvrir un résumé de la requête de comparaison.

![Synthèse de la comparaison](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

Vous pouvez voir les instances A et B qui la requête s’exécutait sur. Vous pouvez également voir un modèle de quoi peut ressembler la requête. Une table affiche des informations de requête qui sont spécifiques aux instances A et B.

### <a name="error-queries"></a>Requêtes de l’erreur

Le rapport de synthèse de comparaison a extensible **des informations d’erreur** et **informations de Plan de requête** sections. Les sections indiquent les erreurs et informations pour les deux instances de plan.

Sélectionnez le graphique à secteurs de l’erreur (rouge) pour afficher ces types d’erreurs :
- **Erreurs existantes**: Erreurs qui se trouvaient dans A.
- **Nouvelles erreurs**: Erreurs qui se trouvaient dans B.
- **Erreurs résolues**: Erreurs qui ont été dans A, mais pas dans B.

![Graphiques de l’erreur](./media/database-experimentation-assistant-view-report/dea-view-report-error-charts.png)

## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment générer un rapport d’analyse à l’invite de commande, consultez [s’exécutent à l’invite de commandes](database-experimentation-assistant-run-command-prompt.md).

- Pour une présentation 19 minutes DEA et de démonstration, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
