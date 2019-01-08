---
title: Classer Assistant (Data Mining Add-ins pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9109f47ba1173c115234f9040445fb110e3f0e3c
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419680"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a>Assistant Classification (Compléments d'exploration de données pour Excel)
  ![Assistant classification dans le ruban Exploration de données](media/dmc-classify.gif "Assistant classification dans le ruban Exploration de données")  
  
 Le **classifier** Assistant vous aide à créer un modèle de classification basé sur des données existantes dans un tableau Excel, une plage Excel ou une source de données externe.  
  
 Un modèle de classification extrait des séquences de vos données qui indiquent des similarités et vous aide à faire des prédictions basées sur des groupements de valeurs. Par exemple, un modèle de classification peut être utilisé pour prédire un risque en fonction des caractéristiques des revenus ou des dépenses.  
  
## <a name="using-the-classify-wizard"></a>Utilisation de l'Assistant Classification  
  
1.  Dans le **d’exploration de données** ruban, cliquez sur **classifier**, puis cliquez sur **suivant**.  
  
2.  Dans le **sélectionner les données Source** page, choisissez les données à analyser.  
  
     Cet Assistant prend en charge plusieurs types de données : Tables Excel, plages Excel et sources de données externes. Les données externes peuvent être ajoutées à Excel, ou bien vous pouvez choisir un ensemble de tables ou vues dans une source de données Analysis Services. Vous pouvez également ajouter des tables et changer les colonnes pour créer une source de données ad hoc.  
  
3.  Sur le **Classification** page, choisissez la colonne que vous souhaitez classer.  
  
     Passez en revue les colonnes dans la liste, **colonnes d’entrée**et désactivez les colonnes qui ont des valeurs uniques et par conséquent, ne sont pas utiles pour la création de modèles, tels que des numéros d’identification, les noms des clients et ainsi de suite. Vous devez également supprimer les colonnes qui sont des doublons de la colonne à classer.  
  
     Par exemple, si vous classez en fonction de la catégorie d'un produit, vous devez exclure le champ de sous-catégorie s'il existe une règle d'entreprise connue, ou bien la force de cette règle peut vous empêcher de découvrir d'autres corrélations.  
  
4.  Si vous le souhaitez, cliquez sur **paramètres** pour modifier les paramètres d’algorithme et personnaliser le comportement du modèle de clustering.  
  
5.  Dans le **fractionner les données d’apprentissage et jeux de test** , spécifiez la quantité de données à exclure pour le test. Le reste est toujours utilisé pour l'apprentissage du modèle.  
  
     Le paramètre par défaut est 30 % de données de test et 70 % de données de formation.  
  
6.  Sur le **Terminer** page, fournissez un nom descriptif pour votre jeu de données et le modèle et définir les options suivantes qui contrôlent la façon dont vous travaillez avec le modèle fini :  
  
    -   **Parcourir le modèle**. Lorsque cette option est sélectionnée, dès que l’Assistant termine de traiter le modèle, il ouvre une **Parcourir** fenêtre pour vous aider à Explorer les résultats. Le contenu de la visionneuse dépend du type de modèle que vous créez. Pour plus d’informations, consultez [exploration d’un modèle d’arbres de décision](browsing-a-decision-trees-model.md) et [exploration d’un modèle de réseau neuronal](browsing-a-neural-network-model.md).  
  
    -   **Activer l’extraction**. Sélectionnez cette option pour examiner les données sous-jacentes du modèle terminé. Cette option est disponible uniquement si vous créez un modèle d'arbre de décision.  
  
    -   **Utiliser le modèle temporaire**. Si cette option est sélectionnée, le modèle ne sera pas enregistré sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
## <a name="more-about-classification-models"></a>En savoir plus sur les modèles de classification  
 Dans le **paramètres d’algorithme** boîte de dialogue, vous pouvez également choisir la méthode de classification parmi ces algorithmes fournis dans Analysis Services :  
  
-   Microsoft Decision Tree  
  
-   Microsoft Logistic Regression  
  
-   Microsoft Naive Bayes  
  
-   Microsoft Neural Network  
  
 Bien que les algorithmes puissent donner des résultats similaires, ils analysent les données différemment, par conséquent nous vous recommandons d'essayer plusieurs algorithmes et de comparer les résultats. La méthode par défaut est Microsoft Decision Tree.  
  
 Dans le **paramètres** liste, vous pouvez modifier les options avancées qui dépendent du type d’algorithme que vous choisissez. Les paramètres de chaque algorithme sont décrits de façon plus détaillée dans la Documentation en ligne de SQL Server.  
  
 [Informations techniques de référence sur l’algorithme MDT (Microsoft Decision Trees)](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Informations techniques de référence sur l’algorithme Microsoft Logistic Regression](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Informations techniques de référence sur l’algorithme MNB (Microsoft Naive Bayes)](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [Informations techniques de référence sur l’algorithme MNN (Microsoft Neural Network)](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>Configuration requise  
 Pour utiliser le **classifier** Assistant, vous devez être connecté à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. Pour plus d’informations sur la création d’une connexion, consultez [se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)  
  
  
