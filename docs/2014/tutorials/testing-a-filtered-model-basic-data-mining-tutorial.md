---
title: Test d’un modèle filtré (didacticiel sur l’exploration de données de base) | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044094"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>Test d'un modèle filtré (Didacticiel sur l'exploration de données de base)
  Maintenant que vous avez déterminé que le `TM_Decision_Tree` modèle est le plus précis, vous allez personnaliser le modèle pour qu’il réponde mieux aux [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] besoins de la campagne de publipostage ciblée. Plus précisément, le service marketing souhaite savoir s'il existe des différences entre les clients hommes et femmes. Ces informations les aideront à décider quels magazines utiliser pour la publicité et quels produits présenter dans leurs publipostages.  
  
## <a name="using-filters"></a>Utilisation de filtres  
 Le filtrage vous permet de créer facilement des modèles basés sur des sous-ensembles de vos données. Le filtre est appliqué uniquement au modèle et ne modifie pas la source de données sous-jacente.  
  
 Dans cette leçon, vous allez créer un modèle qui est filtré sur le type, pour prédire les caractéristiques qui influencent le plus le comportement d'achat des hommes et des femmes.  
  
 Tout d’abord, vous allez effectuer une `TM_Decision_Tree` copie du modèle.  
  
#### <a name="to-copy-the-decision-tree-model"></a>Pour copier le modèle d'arbre de décision  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans Explorateur de solutions, sélectionnez **BasicDataMining**.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Cliquez avec le `TM_Decision_Tree` bouton droit sur le modèle, puis sélectionnez **nouveau modèle d’exploration de données.**  
  
4.  Dans le champ **nom du modèle** , `TM_Decision_Tree_Male`tapez.  
  
5.  Cliquez sur **OK**.  
  
 Ensuite, créez un filtre pour sélectionner des clients pour le modèle en fonction de leur sexe.  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>Pour créer un filtre de cas sur un modèle d'exploration de données  
  
1.  Cliquez avec le bouton `TM_Decision_Tree_Male` droit sur le modèle d’exploration de données pour ouvrir le menu contextuel.  
  
     \- ou -  
  
     Sélectionnez le modèle. Dans le menu **Modèle d'exploration de données** , sélectionnez **Définir le filtre de modèle**.  
  
2.  Dans la boîte de dialogue **Filtre de modèle** , cliquez sur la ligne supérieure dans la grille, dans la zone de texte **Colonne de la structure d'exploration de données** .  
  
     La liste déroulante affiche uniquement les noms des colonnes dans cette table.  
  
3.  Dans la zone de texte colonne de la structure d’exploration de données, sélectionnez **sexe**.  
  
     L'icône située à gauche de la zone de texte change pour indiquer que l'élément sélectionné est une table ou une colonne.  
  
4.  Cliquez sur la zone de texte **opérateur** et sélectionnez l’opérateur égal à (=) dans la liste.  
  
5.  Cliquez sur la zone de texte **valeur** et tapez **M**.  
  
6.  Cliquez sur la ligne suivante dans la grille.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **filtre de modèle** .  
  
     Le filtre s’affiche dans la fenêtre **Propriétés** . Vous pouvez également lancer la boîte de dialogue **filtre de modèle** à partir de la fenêtre **Propriétés** .  
  
8.  Répétez les étapes ci-dessus, mais cette fois `TM_Decision_Tree_Female` nommez le modèle et tapez **F** dans la zone de texte **valeur** .  
  
## <a name="process-the-filtered-models"></a>Traiter les modèles filtrés  
 Les modèles ne peuvent pas être utilisés tant qu'ils n'ont pas été déployés et traités. Pour plus d’informations sur le traitement des modèles, consultez [traitement des modèles dans la structure de publipostage ciblée &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).  
  
#### <a name="to-process-the-filtered-model"></a>Pour traiter le modèle filtré  
  
1.  Cliquez avec le bouton `TM_Decision_Tree_Male` droit sur le modèle et sélectionnez **traiter l’exploration de données structure et tous les modèles**.  
  
2.  Cliquez sur **exécuter** pour traiter les nouveaux modèles.  
  
3.  Une fois le traitement terminé, cliquez sur **Fermer** dans les deux fenêtres de traitement.  
  
     Vous avez maintenant deux nouveaux modèles affichés sous l’onglet **modèles d’exploration de données** .  
  
## <a name="evaluate-the-results"></a>Évaluer les résultats  
 Consultez les résultats et déterminez l'exactitude des modèles filtrés de la même manière que vous l'avez fait pour les trois modèles précédents. Pour plus d'informations, consultez les pages suivantes :  
  
 [Exploration du modèle d’arbre de décision &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [Test de précision avec les graphiques de courbes d’élévation &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>Pour explorer les modèles filtrés  
  
1.  Sélectionnez l’onglet **visionneuse de modèle d’exploration** de données dans le concepteur d’exploration de **données**.  
  
2.  Dans la zone modèle d’exploration de `TM_Decision_Tree_Male`données, sélectionnez.  
  
3.  **Affichez** le niveau `3`de diaporama sur.  
  
4.  Remplacez la valeur d' **arrière-plan** par `1`.  
  
5.  Placez le curseur sur le nœud intitulé **tout** pour voir le nombre d’acheteurs de vélos par rapport aux acheteurs non-Bikes.  
  
6.  Répétez les étapes `TM_Decision_Tree_Female`1-5 pour.  
  
7.  Explorez les résultats pour le `TM_Decision_Tree` et les modèles filtrés pour le sexe. Comparé à tous les acheteurs de vélo, les acheteurs de vélo homme et femme partagent certaines caractéristiques identiques avec les acheteurs de vélo non filtrés, mais tous les trois présentent aussi des différences significatives. Il s’agit d’informations [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] utiles qui peuvent être utilisées pour développer leur campagne marketing.  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>Pour tester la finesse des modèles filtrés  
  
1.  Basculez vers l’onglet graphique d’analyse de **précision** de l' [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] exploration de données dans le concepteur d’exploration de données dans et sélectionnez l’onglet **sélection d’entrée** .  
  
2.  Dans la zone de groupe **Sélectionner le jeu de données à utiliser pour le graphique de précision** , sélectionnez **utiliser les cas de test**de la structure d’exploration de données.  
  
3.  Sous l’onglet **sélection d’entrée** du concepteur d’exploration de données, sous sélectionner les colonnes de modèle d’exploration de données **prévisible à afficher dans le graphique de courbes d’élévation**, activez la case à cocher **synchroniser les colonnes de prédiction et les valeurs**.  
  
4.  Dans la colonne nom de la **colonne prévisible** , vérifiez que **vélo Buyer** est sélectionné pour chaque modèle.  
  
5.  Dans la colonne **Afficher** , sélectionnez chacun des modèles.  
  
6.  Dans la colonne **prédire** la valeur `1`, sélectionnez.  
  
7.  Sélectionnez l’onglet **graphique de courbes d’élévation** pour afficher le graphique de courbes d’élévation.  
  
     Vous remarquerez maintenant que les trois modèles d'arbre de décision fournissent une finesse importante par rapport au modèle d'estimation aléatoire, et devancent également les modèles de Clustering et Naive-Bayes.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur les filtres, consultez [filtres pour les modèles d’exploration de données &#40;Analysis Services-exploration de données&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Pour obtenir un exemple d’application de filtres à des tables imbriquées, consultez le didacticiel sur l' [exploration de données intermédiaire &#40;Analysis Services-exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Test de précision avec les graphiques de courbes d’élévation &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 6 : création et utilisation de prédictions &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’exploration de données intermédiaire &#40;Analysis Services d’exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Tâches du modèle d’exploration de données et procédures](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Supprimer un filtre d’un modèle d’exploration de données](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
