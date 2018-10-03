---
title: Exploration du modèle Decision Tree (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 2e1472c2-3f3e-4dae-acb3-62fca374d397
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a8d8a5238caa09d9b4a3d85d014b2891c3f427e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145909"
---
# <a name="exploring-the-decision-tree-model-basic-data-mining-tutorial"></a>Exploration du modèle Decision Tree (Didacticiel sur l'exploration de données de base)
  L'algorithme MDT ([!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Tree) prédit quelles colonnes influencent la décision d'acheter un vélo en fonction des colonnes restantes dans le jeu d'apprentissage.  
  

  
##  <a name="Decision_Tree_Tab"></a> Onglet arbre de décision  
 Sur le **arbre de décision** onglet, vous pouvez afficher les arbres de décision pour chaque attribut prédictible dans le jeu de données.  
  
 Dans ce cas, le modèle ne prédit qu’une seule colonne, Bike Buyer, par conséquent, il n'est qu’un seul arbre à afficher. Si plusieurs arbre existaient, vous pouvez utiliser la **arborescence** zone pour sélectionner une autre arborescence.  
  
 Lorsque vous consultez le `TM_Decision_Tree` modèle dans la visionneuse d’arbre de décision, vous pouvez voir les attributs les plus importants sur le côté gauche du graphique. « Plus importants » signifie que ces attributs ont la plus grande influence sur le résultat. Les attributs plus bas dans l'arborescence (à droite du graphique) ont moins d'importance.  
  
 Dans cet exemple, l'âge est le facteur le plus important pour prédire les achats de vélo. Le modèle regroupe les clients par âge, puis indique l'attribut le plus important suivant pour chaque catégorie d'âge. Par exemple, dans le groupe de clients âgés de 34 à 40 ans, le nombre de voitures possédées est le facteur de prédiction le plus important après l'âge.  
  
#### <a name="to-explore-the-model-in-the-decision-tree-tab"></a>Pour explorer le modèle sous l'onglet Arbre de décision  
  
1.  Sélectionnez le **visionneuse de modèle d’exploration de données** onglet **Concepteur d’exploration de données**.  
  
     Par défaut, le concepteur s’ouvre pour le premier modèle qui a été ajouté à la structure, dans ce cas, `TM_Decision_Tree`.  
  
2.  Utilisez les boutons de la loupe pour ajuster la taille d'affichage de l'arbre.  
  
     Par défaut, la visionneuse d'arborescences [!INCLUDE[msCoName](../includes/msconame-md.md)] affiche uniquement les trois premiers niveaux de l'arbre. Si l'arbre contient moins de trois niveaux, la visionneuse affiche uniquement les niveaux existants. Vous pouvez afficher davantage de niveaux à l’aide de la **afficher le niveau** curseur ou la **Expansion par défaut** liste.  
  
3.  Faites glisser **afficher le niveau** jusqu'à la quatrième barre.  
  
4.  Modifier le **arrière-plan** valeur `1`.  
  
     En modifiant le **arrière-plan** définition, vous pouvez rapidement voir le nombre de cas dans chaque nœud présentant la valeur cible de `1` pour [Bike Buyer]. Souvenez-vous que dans ce scénario particulier, chaque cas représente un client. La valeur `1` indique que le client a précédemment acheté un vélo ; la valeur **0** indique que le client n’a pas acheté un vélo. Plus l'ombrage du nœud est foncé, plus le pourcentage de cas dans le nœud possédant la valeur cible est élevé.  
  
5.  Placez votre curseur sur le nœud intitulé **tous les**. Une info-bulle affiche les informations suivantes :  
  
    -   Nombre total de cas  
  
    -   Nombre de cas n'ayant pas acheté de vélo  
  
    -   Nombre de cas ayant acheté un vélo  
  
    -   Nombre de cas avec des valeurs manquantes pour [Bike Buyer]  
  
     Vous pouvez également placer votre curseur au-dessus d'un nœud dans l'arbre pour voir la condition requise afin d'atteindre ce nœud depuis le nœud qui le précède. Vous pouvez également afficher ces mêmes informations dans le **légende d’exploration de données**.  
  
6.  Cliquez sur le nœud pour **âge > = 34 et < 41**. L'histogramme s'affiche sous la forme d'une fine barre horizontale sur le nœud et représente la distribution des clients dans cette tranche d'âge qui ont acheté (rose) et qui n'ont pas acheté (bleu) un vélo par le passé. La visionneuse nous indique qu'il est probable que les clients âgés de 34 à 40 ans possèdent une seule voiture ou n'en possédant aucune achètent un vélo. En approfondissant, nous découvrons que la probabilité d'acheter un vélo augmente si le client est en fait âgé de 38 à 40 ans.  
  
 Étant donné que vous avez activé l'extraction lorsque vous avez créé la structure et le modèle, vous pouvez extraire des informations détaillées des cas du modèle et de la structure d'exploration de données, notamment les colonnes qui n'ont pas été incluses dans le modèle d'exploration de données (par exemple, emailAddress, FirstName).  
  
 Pour plus d’informations, consultez [Requêtes d’extraction &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-drill-through-to-case-data"></a>Pour extraire des données de cas  
  
1.  Cliquez sur un nœud, puis sélectionnez **extraire** puis **colonnes de modèle uniquement**.  
  
     Les détails de chaque cas d'apprentissage s'affichent au format feuille de calcul. Ces détails viennent de la vue vTargetMail que vous avez sélectionnée comme table de cas lors de la génération de la structure d'exploration de données.  
  
2.  Cliquez sur un nœud, puis sélectionnez **extraire** puis **modèle et les colonnes de Structure**.  
  
     La même feuille de calcul s'affiche avec les colonnes de structure ajoutées à la fin.  
  
  
###  <a name="Dependency_Network_Tab"></a> Onglet réseau de dépendances  
 Le **réseau de dépendances** onglet affiche les relations entre les attributs qui contribuent à la capacité de prédiction du modèle d’exploration de données. La Visionneuse du réseau de dépendance renforce nos conclusions selon lesquelles l'âge et la région sont des facteurs importants pour prédire l'achat de vélos.  
  
##### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>Pour explorer le modèle sous l'onglet Réseau de dépendances  
  
1.  Cliquez sur le `Bike Buyer` nœud pour identifier ses dépendances.  
  
     Le nœud central du réseau de dépendances, `Bike Buyer`, représente l’attribut prédictible dans le modèle d’exploration de données. Le graphique met en surbrillance les nœuds connectés qui ont un impact sur l'attribut prédictible.  
  
2.  Ajuster la **tous les liens** curseur pour identifier l’attribut le plus influent.  
  
     Lorsque vous faites glisser le curseur vers le bas, les attributs ayant un faible impact sur la colonne [Bike Buyer] sont supprimés à partir du graphique. En ajustant le curseur, vous découvrez que l'âge et la région sont les facteurs les plus importants pour prédire si quelqu'un va acheter un vélo.  
  
## <a name="related-tasks"></a>Tâches associées  
 Consultez les rubriques suivantes pour explorer les données à l'aide d'autres types de modèles.  
  
-   [Exploration du modèle de Clustering &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [Exploration du modèle Naive Bayes &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du modèle de Clustering &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la visionneuse modèle d’exploration de données et de procédures](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Onglet arbre de décision &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md)   
 [Onglet réseau de dépendances &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)   
 [Explorer un modèle à l’aide de la visionneuse d’arborescences Microsoft](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
  
