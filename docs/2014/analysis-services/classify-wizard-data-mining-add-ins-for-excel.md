---
title: Assistant de classification (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18cbc54053ddabf79ac6bfa30c8d43d05720c840
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527505"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a>Assistant Classification (Compléments d'exploration de données pour Excel)
  ![Assistant Classification sur le ruban Exploration de données](media/dmc-classify.gif "Assistant Classification sur le ruban Exploration de données")  
  
 L’Assistant **classification** vous aide à créer un modèle de classification basé sur des données existantes dans une table Excel, une plage Excel ou une source de données externe.  
  
 Un modèle de classification extrait des séquences de vos données qui indiquent des similarités et vous aide à faire des prédictions basées sur des groupements de valeurs. Par exemple, un modèle de classification peut être utilisé pour prédire un risque en fonction des caractéristiques des revenus ou des dépenses.  
  
## <a name="using-the-classify-wizard"></a>Utilisation de l'Assistant Classification  
  
1.  Dans le ruban **exploration de données** , cliquez sur **classifier**, puis sur **suivant**.  
  
2.  Dans la page **Sélectionner les données sources** , choisissez les données à analyser.  
  
     L'Assistant prend en charge plusieurs types de données : tables Excel, plages Excel et sources de données externes. Les données externes peuvent être ajoutées à Excel, ou bien vous pouvez choisir un ensemble de tables ou vues dans une source de données Analysis Services. Vous pouvez également ajouter des tables et changer les colonnes pour créer une source de données ad hoc.  
  
3.  Dans la page **classification** , choisissez la colonne que vous souhaitez classifier.  
  
     Passez en revue les colonnes de la liste, les **colonnes d’entrée**et désélectionnez toutes les colonnes qui ont des valeurs uniques et, par conséquent, ne sont pas utiles pour créer des modèles, tels que des numéros d’identification, des noms de clients, etc. Vous devez également supprimer les colonnes qui sont des doublons de la colonne à classer.  
  
     Par exemple, si vous classez en fonction de la catégorie d'un produit, vous devez exclure le champ de sous-catégorie s'il existe une règle d'entreprise connue, ou bien la force de cette règle peut vous empêcher de découvrir d'autres corrélations.  
  
4.  Si vous le souhaitez, cliquez sur **paramètres** pour modifier les paramètres d’algorithme et personnaliser le comportement du modèle de clustering.  
  
5.  Dans la page **fractionner les données en jeux d’apprentissage et jeux de test** , spécifiez la quantité de données à conserver pour le test. Le reste est toujours utilisé pour l'apprentissage du modèle.  
  
     Le paramètre par défaut est 30 % de données de test et 70 % de données de formation.  
  
6.  Dans la page **Terminer** , indiquez un nom descriptif pour votre jeu de données et votre modèle, puis définissez les options suivantes qui contrôlent la façon dont vous travaillez avec le modèle terminé :  
  
    -   **Parcourir le modèle**. Lorsque cette option est sélectionnée, dès que l’Assistant a terminé de traiter le modèle, il ouvre une fenêtre **Parcourir** pour vous aider à explorer les résultats. Le contenu de la visionneuse dépend du type de modèle que vous créez. Pour plus d’informations, consultez [exploration d’un modèle d’arbre de décision](browsing-a-decision-trees-model.md) et [exploration d’un modèle de réseau neuronal](browsing-a-neural-network-model.md).  
  
    -   **Activer l’extraction**. Sélectionnez cette option pour examiner les données sous-jacentes du modèle terminé. Cette option est disponible uniquement si vous créez un modèle d'arbre de décision.  
  
    -   **Utilisez le modèle temporaire**. Si cette option est sélectionnée, le modèle ne sera pas enregistré sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
## <a name="more-about-classification-models"></a>En savoir plus sur les modèles de classification  
 Dans la boîte de dialogue **paramètres d’algorithme** , vous pouvez également choisir la méthode de classification parmi les algorithmes fournis dans Analysis Services :  
  
-   Microsoft Decision Tree  
  
-   Microsoft Logistic Regression  
  
-   Microsoft Naive Bayes  
  
-   Microsoft Neural Network  
  
 Bien que les algorithmes puissent donner des résultats similaires, ils analysent les données différemment, par conséquent nous vous recommandons d'essayer plusieurs algorithmes et de comparer les résultats. La méthode par défaut est Microsoft Decision Tree.  
  
 Dans la liste **paramètres** , vous pouvez modifier les options avancées, qui dépendent du type d’algorithme que vous choisissez. Les paramètres de chaque algorithme sont décrits de façon plus détaillée dans la Documentation en ligne de SQL Server.  
  
 [Références techniques relatives à l'algorithme MDT (Microsoft Decision Trees)](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Références techniques relatives à l’algorithme MLR (Microsoft Logistic Regression)](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Références techniques relatives à l'algorithme MNB (Microsoft Naive Bayes)](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [Microsoft Neural Network Algorithm Technical Reference](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Spécifications  
 Pour utiliser l’Assistant **classification** , vous devez être connecté à une [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. Pour plus d’informations sur la création d’une connexion, consultez [se connecter à des données sources &#40;client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d'un modèle d'exploration de données](creating-a-data-mining-model.md)  
  
  
