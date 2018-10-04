---
title: Estimer l’Assistant (Data Mining Add-ins pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04a5bf6b80e95df3b01ac73fd4580813c0709fe9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48182459"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a>Assistant Estimation (Compléments d'exploration de données pour Excel)
  ![Assistant estimation dans le ruban Exploration de données](media/dmc-estimate.gif "Assistant estimation dans le ruban Exploration de données")  
  
 Le **estimation** Assistant vous permet de créer un modèle d’estimation. Un modèle d'estimation extrait les séquences remarquables des données et utilise ces séquences pour prédire les facteurs qui affectent les résultats.  
  
 L'estimation est utilisée pour prévoir les résultats numériques. Par exemple, si votre colonne cible contient le taux d’obtention du diplôme pour les écoles, avec des taux d’obtention du diplôme exprimé sous forme de pourcentages, vous pouvez analyser les facteurs qui font augmenter ou diminuer les taux d’obtention du diplôme, telles que le nombre d’élèves par école, le rapport élève-professeur et le nombre de professeurs.  
  
## <a name="using-the-estimate-data-wizard"></a>Utilisation de l'Assistant Estimation des données  
  
1.  Sur le **d’exploration de données** ruban, cliquez sur **estimation**.  
  
2.  Dans le **sélectionner les données Source** boîte de dialogue, sélectionnez les données source à utiliser. Vous pouvez utiliser des données dans un Excel **Table**, d’Excel **plage de données**, ou à partir d’un **source de données externe**.  
  
     Si vous utilisez une source de données externe, vous pouvez créer des vues personnalisées ou des requêtes et les enregistrer en tant que source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Dans le **Estimation** boîte de dialogue, sélectionnez le **colonne à analyser**.  
  
     La colonne cible doit contenir des données numériques continues.  
  
4.  Sélectionnez les colonnes à utiliser comme entrée en vérifiant la **colonnes d’entrée** case à cocher.  
  
     Ces colonnes seront utilisées pour créer les modèles. Vous devez éliminer de l'analyse toutes les colonnes qui risquent d'être inutiles, comme les numéros d'identification ou les colonnes qui ne sont pas pertinentes.  
  
5.  Le **estimation** Assistant sélectionne l’algorithme optimal pour votre jeu de données. Toutefois, vous pouvez cliquer sur **paramètres** pour ouvrir le **paramètres d’algorithme** boîte de dialogue et définir des options avancées.  
  
6.  Si vos données sont numériques, et vous pouvez utiliser la méthode Microsoft Linear Regression, vous pouvez vérifier le **régresseur** boîte pour toutes les colonnes numériques que vous connaissez (ou présumez fortement) à mettre en corrélation avec la valeur prévisible.  
  
     L'algorithme testera ensuite les valeurs dans cette colonne pour déterminer si elles affectent les résultats. Si vous ne savez pas, cliquez sur **suggérer** et l’algorithme sera toutes les colonnes et détecter automatiquement les meilleures valeurs à utiliser comme régresseur.  
  
    > [!NOTE]  
    >  Un régresseur est requis pour créer une évaluation. L'Assistant recommande toujours le meilleur régresseur, en fonction selon d'une analyse initiale des données. Par conséquent, si vous n'êtes pas sûr, il vaut mieux accepter les sélections recommandées.  
  
7.  Sur le **fractionner les données d’apprentissage et jeux de test** , spécifiez si vous souhaitez créer un petit sous-ensemble de données pour le test.  
  
8.  Sur le **Terminer** page, fournir des noms pour la nouvelle structure d’exploration de données et le mode d’exploration de données ou acceptez les noms par défaut qui sont fournies.  
  
9. Définissez des options pour utiliser le modèle.  
  
    -   Sélectionnez **Parcourir** pour ouvrir immédiatement le modèle dans une visionneuse.  
  
         Cette visionneuse graphique affiche un graphique du réseau de dépendances et l'arbre de décision généré par l'algorithme. En explorant ces informations, vous pouvez mieux comprendre les facteurs qui contribuent aux valeurs estimées.  
  
    -   Sélectionnez **activer l’extraction** pour permettre aux utilisateurs de votre analyse de visualiser les données sous-jacentes.  
  
         Cette option est disponible uniquement si vous utilisez les algorithmes MDT ou MLR.  
  
    -   **Utiliser le modèle temporaire**. Si cette option est sélectionnée, le modèle ne sera pas enregistré sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
## <a name="more-about-estimation-models"></a>En savoir plus sur les modèles d'estimation  
 Le **estimation** Assistant prend en charge l’utilisation d’un des algorithmes suivants :  
  
-   Algorithme d’arbre de décision de Microsoft  
  
-   Algorithme MLR (Microsoft Linear Regression)  
  
-   Algorithme MLR (Microsoft Logistic Regression)  
  
-   Algorithme de Microsoft Neural network  
  
 Dans le **paramètres d’algorithme** boîte de dialogue, vous pouvez définir des options avancées supplémentaires, selon l’algorithme que vous avez choisi. Pour plus d'informations sur les options de chaque algorithme, consultez les rubriques de la documentation en ligne de SQL Server :  
  
 [Informations techniques de référence sur l’algorithme MDT (Microsoft Decision Trees)](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Informations techniques de référence sur l’algorithme Microsoft Linear Regression](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [Informations techniques de référence sur l’algorithme Microsoft Logistic Regression](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Informations techniques de référence sur l’algorithme MNN (Microsoft Neural Network)](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Spécifications  
 Pour utiliser l'Assistant Estimation des données, vous devez être connecté à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Pour plus d’informations sur la création d’une connexion, consultez [se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Pour utiliser l'algorithme d'estimation, le résultat que vous tentez de prédire doit être exprimé sous la forme d'une valeur numérique, comme une devise, un montant de vente, une date ou une heure.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Procédure pas à pas diagramme d’arbre de décision &#40;compléments d’exploration de données&#41;](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  
