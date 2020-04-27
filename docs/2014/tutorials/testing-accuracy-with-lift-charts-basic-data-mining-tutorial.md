---
title: Test de précision avec les graphiques de courbes d’élévation (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 06cefcdac192b715fe843f842088456f769cdd24
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63042642"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a>Test de la précision à l'aide de graphiques de courbes d'élévation (Didacticiel sur l'exploration de données de base)
  Sous l’onglet graphique d’analyse de précision de l' **exploration** de données du concepteur d’exploration de données, vous pouvez calculer le degré de prédiction de chacun de vos modèles et comparer les résultats de chaque modèle directement aux résultats des autres modèles. Cette méthode de comparaison est désignée sous le terme de *graphique de courbes d’élévation*. En général, la précision prédictive d'un modèle d'exploration de données se mesure par la finesse ou la précision de classification. Pour ce didacticiel, nous utiliserons le graphique de courbes d'élévation uniquement.  
  
 Au cours de cette rubrique, vous allez effectuer les tâches suivantes :  
  
-   [Choisir des données d'entrée](#BKMK_InputData)  
  
-   [Configurer les paramètres du graphique d'analyse de précision](#BKMK_Selecting)  
  
##  <a name="choosing-the-input-data"></a><a name="BKMK_InputData"></a>Choix des données d’entrée  
 La première étape du test de précision de vos modèles d'exploration de données consiste à sélectionner la source de données que vous allez utiliser pour les tests. Vous allez tester le degré de précision des modèles avec vos données de test, puis vous les utiliserez avec des données externes.  
  
#### <a name="to-select-the-data-set"></a>Pour sélectionner le jeu de données  
  
1.  Basculez vers l’onglet graphique d’analyse de **précision** de l' [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] exploration de données dans le concepteur d’exploration de données dans et sélectionnez l’onglet **sélection d’entrée** .  
  
2.  Dans la zone de groupe **Sélectionner le jeu de données à utiliser pour le graphique de précision** , sélectionnez **utiliser les cas de test**de la structure d’exploration de données. Il s'agit du jeu de données que vous avez mis de côté lorsque vous avez créé la structure d'exploration de données.  
  
     Pour plus d’informations sur les autres options, consultez [choisir un type de graphique d’exactitude et définir des options de graphique](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).  
  
##  <a name="setting-accuracy-chart-parameters"></a><a name="BKMK_Selecting"></a>Définition des paramètres du graphique de précision  
 Pour créer un graphique d'analyse de précision, vous devez définir trois éléments :  
  
-   Les modèles à inclure dans le graphique d'analyse de précision  
  
-   L'attribut prédictible à mesurer Certains modèles peuvent avoir plusieurs cibles, mais chaque graphique ne mesure qu'un seul résultat à la fois.  
  
     Pour utiliser une colonne comme **nom de colonne prévisible** dans un graphique de précision, les colonnes doivent avoir le type d' `Predict` utilisation `Predict Only`ou. En outre, le type de contenu de la colonne cible doit être `Discrete` ou `Discretized`. En d'autres termes, vous ne pouvez pas utiliser le graphique de courbes d'élévation pour mesurer la précision par rapport à des valeurs numériques continues.  
  
-   Voulez-vous mesurer la précision générale du modèle ou sa précision dans la prédiction d’une valeur particulière (par exemple, [vélo Buyer] = 'Oui')  
  
#### <a name="to-generate-the-lift-chart"></a>Pour générer le graphique de courbes d'élévation  
  
1.  Sous l’onglet **sélection d’entrée** du concepteur d’exploration de données, sous sélectionner les colonnes de modèle d’exploration de données **prévisible à afficher dans le graphique de courbes d’élévation**, activez la case à cocher **synchroniser les colonnes de prédiction et les valeurs**.  
  
2.  Dans la colonne nom de la **colonne prévisible** , vérifiez que **vélo Buyer** est sélectionné pour chaque modèle.  
  
3.  Dans la colonne **Afficher** , sélectionnez chacun des modèles.  
  
     Par défaut, tous les modèles de la structure d'exploration de données sont sélectionnés. Vous pouvez choisir de ne pas inclure un modèle, mais pour ce didacticiel, conservez tous les modèles sélectionnés.  
  
4.  Dans la colonne **prédire la valeur** , sélectionnez **1**. La même valeur est automatiquement remplie dans chaque modèle comportant la même colonne prédictible.  
  
5.  Sélectionnez l’onglet **graphique de courbes d’élévation** .  
  
     Lorsque vous cliquez sur l'onglet, une requête de prédiction s'exécute pour obtenir des prédictions pour les données de test, et les résultats sont comparés aux valeurs connues. Les résultats sont reportés sur le graphique.  
  
     Si vous avez spécifié un résultat cible particulier à l’aide de l’option **prédire la valeur** , le graphique de courbes d’élévation trace les résultats des hypothèses aléatoires et les résultats d’un modèle idéal.  
  
    -   La ligne d'estimation aléatoire indique la précision du modèle sans utiliser de données pour éclairer ses prédictions : c'est-à-dire, un fractionnement 50-50 entre deux résultats. Le graphique de courbes d'élévation vous aide à visualiser le gain de performances de votre modèle par rapport à une estimation aléatoire.  
  
    -   La ligne de modèle idéal représente la limite supérieure de précision. Elle indique les éventuels avantages que vous pouvez retirer si votre modèle a toujours effectué des prédictions précises.  
  
     Les modèles d'exploration de données que vous avez créés se situent généralement entre ces deux extrêmes. Toute amélioration par rapport à l’estimation aléatoire est considérée comme une *élévation*.  
  
6.  Utilisez la légende pour repérer les lignes colorées qui représentent le modèle idéal et le modèle d'estimation aléatoire.  
  
     Vous remarquerez que `TM_Decision_Tree` le modèle fournit la plus grande élévation, ce qui a pour avantage les modèles de clustering et Naive Bayes.  
  
 Pour une explication détaillée d’un graphique de courbes d’élévation similaire à celui créé dans cette leçon, consultez [graphique de courbes d’élévation &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Test d’un modèle filtré &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de courbes d’élévation &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Onglet graphique de courbes d’élévation &#40;vue graphique d’analyse de précision de l’exploration de données&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
