---
title: Test d’un modèle filtré (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: baa4910b2849c4eb2dd04c6d0115c83683ee8bea
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56011140"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>Test d'un modèle filtré (Didacticiel sur l'exploration de données de base)
  Maintenant que vous avez déterminé que le `TM_Decision_Tree` modèle est le plus précis, vous allez personnaliser le modèle pour mieux répondre aux besoins de le [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] campagne de publipostage ciblée. Plus précisément, le service marketing souhaite savoir s'il existe des différences entre les clients hommes et femmes. Les informations les aideront à décider quels magazines utiliser à des fins publicitaires et quels produits présenter dans leurs publipostages.  
  
## <a name="using-filters"></a>Utilisation de filtres  
 Le filtrage vous permet de créer facilement des modèles basés sur des sous-ensembles de vos données. Le filtre est appliqué uniquement au modèle et ne modifie pas la source de données sous-jacente.  
  
 Dans cette leçon, vous allez créer un modèle qui est filtré sur le type, pour prédire les caractéristiques qui influencent le plus le comportement d'achat des hommes et des femmes.  
  
 Tout d’abord, vous effectuerez une copie de la `TM_Decision_Tree` modèle.  
  
#### <a name="to-copy-the-decision-tree-model"></a>Pour copier le modèle d'arbre de décision  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans l’Explorateur de solutions, sélectionnez **BasicDataMining**.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Bouton droit sur le `TM_Decision_Tree` de modèle, puis sélectionnez **nouveau modèle d’exploration de données.**  
  
4.  Dans le **nom_modèle** , tapez `TM_Decision_Tree_Male`.  
  
5.  Cliquez sur **OK**.  
  
 Ensuite, créez un filtre pour sélectionner des clients pour le modèle en fonction de leur sexe.  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>Pour créer un filtre de cas sur un modèle d'exploration de données  
  
1.  Cliquez sur le `TM_Decision_Tree_Male` modèle d’exploration de données pour ouvrir le menu contextuel.  
  
     -- ou --  
  
     Sélectionnez le modèle. Dans le menu **Modèle d'exploration de données** , sélectionnez **Définir le filtre de modèle**.  
  
2.  Dans la boîte de dialogue **Filtre de modèle** , cliquez sur la ligne supérieure dans la grille, dans la zone de texte **Colonne de la structure d'exploration de données** .  
  
     La liste déroulante affiche uniquement les noms des colonnes dans cette table.  
  
3.  Dans la zone de texte colonne de Structure d’exploration de données, sélectionnez **sexe**.  
  
     L'icône située à gauche de la zone de texte change pour indiquer que l'élément sélectionné est une table ou une colonne.  
  
4.  Cliquez sur le **opérateur** zone de texte et sélectionnez l’opérateur égal (=) dans la liste.  
  
5.  Cliquez sur le **valeur** zone de texte et le type **M**.  
  
6.  Cliquez sur la ligne suivante dans la grille.  
  
7.  Cliquez sur **OK** pour fermer la **filtre de modèle** boîte de dialogue.  
  
     Le filtre s’affiche dans le **propriétés** fenêtre. Alternativement, vous pouvez lancer le **filtre de modèle** boîte de dialogue à partir de la **propriétés** fenêtre.  
  
8.  Répétez les étapes ci-dessus, mais cette fois nommez le modèle `TM_Decision_Tree_Female` et type **F** dans le **valeur** zone de texte.  
  
## <a name="process-the-filtered-models"></a>Traiter les modèles filtrés  
 Les modèles ne peuvent pas être utilisés tant qu'ils n'ont pas été déployés et traités. Pour plus d’informations sur les modèles de traitement, consultez [de traitement des modèles dans la Structure de publipostage ciblé &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).  
  
#### <a name="to-process-the-filtered-model"></a>Pour traiter le modèle filtré  
  
1.  Cliquez sur le `TM_Decision_Tree_Male` de modèle et sélectionnez **traiter la Structure d’exploration de données et tous les modèles**s  
  
2.  Cliquez sur **exécuter** pour traiter les nouveaux modèles.  
  
3.  Une fois le traitement est terminé, cliquez sur **fermer** sur les deux fenêtres de traitement.  
  
     Vous avez maintenant deux nouveaux modèles affichés dans le **des modèles d’exploration de données** onglet.  
  
## <a name="evaluate-the-results"></a>Évaluer les résultats  
 Consultez les résultats et déterminez l'exactitude des modèles filtrés de la même manière que vous l'avez fait pour les trois modèles précédents. Pour plus d'informations, consultez :  
  
 [Exploration du modèle Decision Tree &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [Test de la précision à l’aide de graphiques de courbes d’élévation &#40;Didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>Pour explorer les modèles filtrés  
  
1.  Sélectionnez le **visionneuse de modèle d’exploration de données** onglet **Concepteur d’exploration de données**.  
  
2.  Dans la zone modèle d’exploration de données, sélectionnez `TM_Decision_Tree_Male`.  
  
3.  Faites glisser **afficher le niveau** à `3`.  
  
4.  Modifier le **arrière-plan** valeur `1`.  
  
5.  Placez votre curseur sur le nœud intitulé **tous les** pour afficher le nombre d’acheteurs de vélo par rapport aux non-acheteurs de vélo.  
  
6.  Répétez les étapes 1 à 5 pour `TM_Decision_Tree_Female`.  
  
7.  Explorez les résultats pour le `TM_Decision_Tree` et les modèles filtrés par sexe. Comparé à tous les acheteurs de vélo, les acheteurs de vélo homme et femme partagent certaines caractéristiques identiques avec les acheteurs de vélo non filtrés, mais tous les trois présentent aussi des différences significatives. Il s’agit des informations utiles qui [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] peuvent utiliser pour développer sa campagne de marketing.  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>Pour tester la finesse des modèles filtrés  
  
1.  Basculez vers le **graphique de précision d’exploration de données** onglet dans le Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et sélectionnez le **sélection d’entrée** onglet.  
  
2.  Dans le **sélectionner le jeu de données à utiliser pour le graphique de précision** zone de groupe, sélectionnez **utiliser des scénarios de test de structure d’exploration de données**.  
  
3.  Sur le **sélection d’entrée** onglet du Concepteur d’exploration de données, sous **sélectionner des colonnes de modèle d’exploration de données prévisibles à afficher dans le graphique de courbes d’élévation**, activez la case à cocher pour **synchroniser les colonnes de prédiction et Valeurs**.  
  
4.  Dans le **nom de la colonne prédictible** colonne, vérifiez que **Bike Buyer** est sélectionné pour chaque modèle.  
  
5.  Dans le **afficher** colonne, sélectionnez chacun des modèles.  
  
6.  Dans le **prédire la valeur** colonne, sélectionnez `1`.  
  
7.  Sélectionnez le **graphique de courbes d’élévation** onglet pour afficher le graphique de courbes d’élévation.  
  
     Vous remarquerez maintenant que les trois modèles d'arbre de décision fournissent une finesse importante par rapport au modèle d'estimation aléatoire, et devancent également les modèles de Clustering et Naive-Bayes.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur les filtres, consultez [filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Pour obtenir un exemple montrant comment appliquer des filtres aux tables imbriquées, consultez [didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Test de la précision à l’aide de graphiques de courbes d’élévation &#40;Didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 6 : Création et utilisation de prédictions &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Tâches du modèle d'exploration de données et procédures](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Supprimer un filtre d’un modèle d’exploration de données](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
