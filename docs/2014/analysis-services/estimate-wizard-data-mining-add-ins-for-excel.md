---
title: Assistant estimation (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2706dae37c1dc303aa6708fe1f7387a39835e4d5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528367"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a>Assistant Estimation (Compléments d'exploration de données pour Excel)
  ![Assistant Estimation sur le ruban Exploration de données](media/dmc-estimate.gif "Assistant Estimation sur le ruban Exploration de données")  
  
 L’Assistant **estimation** vous aide à créer un modèle d’estimation. Un modèle d'estimation extrait les séquences remarquables des données et utilise ces séquences pour prédire les facteurs qui affectent les résultats.  
  
 L'estimation est utilisée pour prévoir les résultats numériques. Par exemple, si votre colonne cible contient des taux de diplômes pour les écoles, avec des taux de diplôme exprimés en pourcentage, vous pouvez analyser des facteurs qui augmentent ou diminuent les taux de diplômes, tels que le nombre d’étudiants par école, le ratio étudiant-enseignant et le nombre d’enseignants.  
  
## <a name="using-the-estimate-data-wizard"></a>Utilisation de l'Assistant Estimation des données  
  
1.  Sur le ruban **exploration de données** , cliquez sur **estimation**.  
  
2.  Dans la boîte de dialogue **Sélectionner les données source** , sélectionnez les données sources à utiliser. Vous pouvez utiliser les données d’une **table**Excel, d’une **plage de données**Excel ou d’une source de **données externe**.  
  
     Si vous utilisez une source de données externe, vous pouvez créer des vues personnalisées ou des requêtes et les enregistrer en tant que source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Dans la boîte de dialogue **estimation** , sélectionnez la **colonne à analyser**.  
  
     La colonne cible doit contenir des données numériques continues.  
  
4.  Sélectionnez les colonnes à utiliser comme entrée en activant la case à cocher **colonnes d’entrée** .  
  
     Ces colonnes seront utilisées pour créer les modèles. Vous devez éliminer de l'analyse toutes les colonnes qui risquent d'être inutiles, comme les numéros d'identification ou les colonnes qui ne sont pas pertinentes.  
  
5.  L’Assistant **estimation** sélectionne l’algorithme optimal pour votre jeu de données. Toutefois, vous pouvez cliquer sur **paramètres** pour ouvrir la boîte de dialogue **paramètres d’algorithme** et définir des options avancées.  
  
6.  Si vos données sont numériques et que vous pouvez utiliser la méthode de régression linéaire Microsoft, vous pouvez **Vérifier la zone de regression pour** toutes les colonnes numériques que vous savez (ou fortement suspectes) être corrélées avec la valeur prévisible.  
  
     L'algorithme testera ensuite les valeurs dans cette colonne pour déterminer si elles affectent les résultats. Si vous n’en êtes pas sûr, cliquez sur **suggérer** et l’algorithme testera toutes les colonnes et détectera automatiquement les meilleures valeurs à utiliser comme régressions.  
  
    > [!NOTE]  
    >  Un régresseur est requis pour créer une évaluation. L'Assistant recommande toujours le meilleur régresseur, en fonction selon d'une analyse initiale des données. Par conséquent, si vous n'êtes pas sûr, il vaut mieux accepter les sélections recommandées.  
  
7.  Sur la page **fractionner les données en jeux d’apprentissage et jeux de test** , spécifiez si vous souhaitez créer un petit sous-ensemble de données à des fins de test.  
  
8.  Dans la page **Terminer** , fournissez des noms pour la nouvelle structure d’exploration de données et le mode d’exploration de données, ou acceptez les noms par défaut fournis.  
  
9. Définissez des options pour utiliser le modèle.  
  
    -   Sélectionnez **Parcourir** pour ouvrir immédiatement le modèle dans une visionneuse.  
  
         Cette visionneuse graphique affiche un graphique du réseau de dépendances et l'arbre de décision généré par l'algorithme. En explorant ces informations, vous pouvez mieux comprendre les facteurs qui contribuent aux valeurs estimées.  
  
    -   Sélectionnez **activer l’extraction** pour permettre aux utilisateurs de votre analyse d’afficher les données sous-jacentes.  
  
         Cette option est disponible uniquement si vous utilisez les algorithmes MDT ou MLR.  
  
    -   **Utilisez le modèle temporaire**. Si cette option est sélectionnée, le modèle ne sera pas enregistré sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
## <a name="more-about-estimation-models"></a>En savoir plus sur les modèles d'estimation  
 L’Assistant **estimation** prend en charge l’utilisation de l’un des algorithmes suivants :  
  
-   Algorithme d’arbre de décision Microsoft  
  
-   Algorithme MLR (Microsoft Linear Regression)  
  
-   Algorithme MLR (Microsoft Logistic Regression)  
  
-   Algorithme de réseau neuronal Microsoft  
  
 Dans la boîte de dialogue **paramètres d’algorithme** , vous pouvez définir des options avancées supplémentaires, en fonction de l’algorithme que vous avez choisi. Pour plus d'informations sur les options de chaque algorithme, consultez les rubriques de la documentation en ligne de SQL Server :  
  
 [Références techniques relatives à l'algorithme MDT (Microsoft Decision Trees)](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Références techniques relatives à l'algorithme MLR (Microsoft Linear Regression)](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [Références techniques relatives à l’algorithme MLR (Microsoft Logistic Regression)](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Microsoft Neural Network Algorithm Technical Reference](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Spécifications  
 Pour utiliser l'Assistant Estimation des données, vous devez être connecté à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Pour plus d’informations sur la création d’une connexion, consultez [se connecter à des données sources &#40;client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Pour utiliser l'algorithme d'estimation, le résultat que vous tentez de prédire doit être exprimé sous la forme d'une valeur numérique, comme une devise, un montant de vente, une date ou une heure.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Procédure pas à pas du diagramme d’arbre de décision &#40;des compléments d’exploration de données&#41;](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  
