---
title: Test de la précision avec des graphiques de courbes d’élévation (didacticiel d’exploration de données de base de données) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8ce5ba972af0b1dda27521dbc5dc58041e386a69
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312557"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a>Test de la précision à l'aide de graphiques de courbes d'élévation (Didacticiel sur l'exploration de données de base)
  Sur le **graphique de précision d’exploration de données** onglet du Concepteur d’exploration de données, vous pouvez calculer la manière dont chacun de vos modèles effectue des prédictions et comparer les résultats de chaque modèle directement sur les résultats des autres modèles. Cette méthode de comparaison est appelée un *graphique de courbes d’élévation*. En général, la précision prédictive d'un modèle d'exploration de données se mesure par la finesse ou la précision de classification. Pour ce didacticiel, nous utiliserons le graphique de courbes d'élévation uniquement.  
  
 Au cours de cette rubrique, vous allez effectuer les tâches suivantes :  
  
-   [Choisissez les données d’entrée](#BKMK_InputData)  
  
-   [Configurer les paramètres du graphique d’analyse de précision](#BKMK_Selecting)  
  
##  <a name="BKMK_InputData"></a> Sélection des données d’entrée  
 La première étape du test de précision de vos modèles d'exploration de données consiste à sélectionner la source de données que vous allez utiliser pour les tests. Vous allez tester le degré de précision des modèles avec vos données de test, puis vous les utiliserez avec des données externes.  
  
#### <a name="to-select-the-data-set"></a>Pour sélectionner le jeu de données  
  
1.  Basculez vers le **graphique de précision d’exploration de données** onglet dans le Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et sélectionnez le **sélection d’entrée** onglet.  
  
2.  Dans le **sélectionner le jeu de données à utiliser pour le graphique d’analyse de précision** zone de groupe, sélectionnez **utiliser des scénarios de test de structure d’exploration de données**. Il s'agit du jeu de données que vous avez mis de côté lorsque vous avez créé la structure d'exploration de données.  
  
     Pour plus d’informations sur les autres options, consultez [choisir un Type de graphique d’analyse de précision et de définir les Options de graphique](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).  
  
##  <a name="BKMK_Selecting"></a> Définition des paramètres du graphique d’analyse de précision  
 Pour créer un graphique d'analyse de précision, vous devez définir trois éléments :  
  
-   Les modèles à inclure dans le graphique d'analyse de précision  
  
-   L'attribut prédictible à mesurer Certains modèles peuvent avoir plusieurs cibles, mais chaque graphique ne mesure qu'un seul résultat à la fois.  
  
     Pour utiliser une colonne en tant que le **nom de la colonne prédictible** dans un graphique de précision, les colonnes doivent avoir le type d’utilisation `Predict` ou `Predict Only`. En outre, le type de contenu de la colonne cible doit être `Discrete` ou `Discretized`. En d'autres termes, vous ne pouvez pas utiliser le graphique de courbes d'élévation pour mesurer la précision par rapport à des valeurs numériques continues.  
  
-   Voulez-vous mesurer la précision générale du modèle, ou sa précision lors de la prédiction d'une valeur spécifique (notamment [Bike Buyer] = « Oui »)  
  
#### <a name="to-generate-the-lift-chart"></a>Pour générer le graphique de courbes d'élévation  
  
1.  Sur le **sélection d’entrée** onglet du Concepteur d’exploration de données, sous **sélectionner les colonnes du modèle d’exploration de données prévisibles à afficher dans le graphique de courbes d’élévation**, activez la case à cocher pour **synchroniser les colonnes de prédiction et Valeurs**.  
  
2.  Dans le **nom de la colonne prédictible** colonne, vérifiez que **Bike Buyer** est sélectionnée pour chaque modèle.  
  
3.  Dans le **afficher** colonne, sélectionnez chacun des modèles.  
  
     Par défaut, tous les modèles de la structure d'exploration de données sont sélectionnés. Vous pouvez choisir de ne pas inclure un modèle, mais pour ce didacticiel, conservez tous les modèles sélectionnés.  
  
4.  Dans le **prédire la valeur** colonne, sélectionnez **1**. La même valeur est automatiquement remplie dans chaque modèle comportant la même colonne prédictible.  
  
5.  Sélectionnez le **graphique de courbes d’élévation** onglet.  
  
     Lorsque vous cliquez sur l'onglet, une requête de prédiction s'exécute pour obtenir des prédictions pour les données de test, et les résultats sont comparés aux valeurs connues. Les résultats sont reportés sur le graphique.  
  
     Si vous avez spécifié un résultat cible particulier à l’aide du **prédire la valeur** option, le graphique de courbes d’élévation trace les résultats de l’estimation aléatoire et les résultats d’un modèle idéal.  
  
    -   La ligne d'estimation aléatoire indique la précision du modèle sans utiliser de données pour éclairer ses prédictions : c'est-à-dire, un fractionnement 50-50 entre deux résultats. Le graphique de courbes d'élévation vous aide à visualiser le gain de performances de votre modèle par rapport à une estimation aléatoire.  
  
    -   La ligne de modèle idéal représente la limite supérieure de précision. Elle indique les éventuels avantages que vous pouvez retirer si votre modèle a toujours effectué des prédictions précises.  
  
     Les modèles d'exploration de données que vous avez créés se situent généralement entre ces deux extrêmes. Toute amélioration par rapport à l’estimation aléatoire est considérée comme *de courbes d’élévation*.  
  
6.  Utilisez la légende pour repérer les lignes colorées qui représentent le modèle idéal et le modèle d'estimation aléatoire.  
  
     Vous remarquerez que le `TM_Decision_Tree` modèle fournit la plus grande finesse, devançant ainsi les modèles à la fois le Clustering et Naive Bayes.  
  
 Pour obtenir une explication approfondie d’un graphique de courbes d’élévation semblable à celui créé dans cette leçon, consultez [graphique de courbes d’élévation &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Test d’un modèle filtré &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de courbes d’élévation &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Onglet graphique de courbes d’élévation &#40;vue graphique d’analyse de précision d’exploration de données&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  