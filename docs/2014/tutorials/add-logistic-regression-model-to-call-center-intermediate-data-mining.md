---
title: Ajout d’un modèle de régression logistique à la Structure de centre d’appels (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4afe3881d8e5eafaeffbd45aa7f64a514d8c70a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208201"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a>Ajout d'un modèle de régression logistique à la structure de centre d'appels (Didacticiel sur l'exploration de données intermédiaire)
  En plus d'analyser les facteurs qui peuvent affecter le fonctionnement d'un centre d'appels, il vous a été demandé de fournir des recommandations spécifiques sur la façon dont le personnel peut améliorer la qualité de service. Au cours de cette tâche, vous utiliserez la même structure d'exploration de données que celle que vous avez utilisée pour générer le modèle exploratoire et ajouter un modèle d'exploration de données qui sera utilisé pour créer des prédictions.  
  
 Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], un modèle de régression logistique est basé sur l'algorithme MNN (Microsoft Neural Network) et fournit par conséquent la même souplesse et la même puissance qu'un modèle de réseau neuronal. Toutefois, la régression logistique est particulièrement bien adaptée pour prévoir les résultats binaires.  
  
 Pour ce scénario, vous utiliserez la même structure d'exploration de données que celle utilisée pour le modèle de réseau neuronal. Toutefois, vous personnaliserez le nouveau modèle pour cibler vos questions professionnelles. Vous êtes intéressé par l'amélioration de la qualité de service et par la détermination du nombre d'opérateurs expérimentés dont vous avez besoin. Vous allez donc définir votre modèle pour prédire ces valeurs.  
  
 Pour garantir que tous les modèles basés sur les données de centre d'appels soient aussi semblables que possible, vous utiliserez la même valeur initiale qu'auparavant. La définition du paramètre de valeur initiale garantit que le modèle traite les données à partir du même point de départ et réduit les variations provoquées par les artefacts dans les données.  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a>Pour ajouter un nouveau modèle d'exploration de données à la structure d'exploration de données de centre d'appels  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans l’Explorateur de solutions, cliquez sur la structure d’exploration de données, **placées dans un conteneur Center appeler**, puis sélectionnez **ouvrir le concepteur**.  
  
2.  Dans le Concepteur d’exploration de données, cliquez sur le **des modèles d’exploration de données** onglet.  
  
3.  Cliquez sur **créer un modèle d’exploration de données**.  
  
4.  Dans le **nouveau modèle d’exploration de données** boîte de dialogue pour **nom_modèle**, type `Call Center - LR`.  Pour **nom de l’algorithme**, sélectionnez **Microsoft Logistic Regression**.  
  
5.  Cliquez sur **OK**.  
  
     Le nouveau modèle d’exploration de données s’affiche dans le **les modèles d’exploration de données** onglet.  
  
### <a name="to-customize-the-logistic-regression-model"></a>Pour personnaliser le modèle de régression logistique  
  
1.  Dans la colonne pour le nouveau modèle d’exploration de données, `Call Center - LR`, laissez l’ID Factcallcenter comme clé.  
  
2.  Modifiez la valeur de ServiceGrade et de Leveltwooperators par **Predict**.  
  
     Ces colonnes seront utilisées aussi bien comme entrée que pour la prédiction. Fondamentalement, vous créez deux modèles distincts sur les mêmes données : un qui prédit le nombre d'opérateurs et un qui prédit le niveau de service.  
  
3.  Modifier tous les autres colonnes à **entrée**.  
  
### <a name="to-specify-the-seed-and-process-the-models"></a>Pour spécifier la valeur initiale et traiter les modèles  
  
1.  Dans le **Mining Model** onglet, cliquez sur la colonne sur le modèle nommé Centre d’appels - LR et sélectionnez **paramètres d’algorithme définir**.  
  
2.  Dans la ligne correspondant au paramètre HOLDOUT_SEED, cliquez sur la cellule vide sous **valeur**et le type `1`. Cliquez sur **OK**.  
  
    > [!NOTE]  
    >  La valeur que vous choisissez comme valeur initiale n'a pas d'importance tant que vous utilisez la même valeur initiale pour tous les modèles associés.  
  
3.  Dans le **des modèles d’exploration de données** menu, sélectionnez **traiter la Structure d’exploration de données et tous les modèles**. Cliquez sur **Oui** pour déployer le projet d’exploration de données mises à jour sur le serveur.  
  
4.  Dans le **traiter le modèle d’exploration de données** boîte de dialogue, cliquez sur **exécuter**.  
  
5.  Cliquez sur **fermer** pour fermer la **progression du traitement** boîte de dialogue, puis cliquez sur **fermer** à nouveau dans le **traiter le modèle d’exploration de données** boîte de dialogue.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création de prédictions pour les modèles de centre d’appels &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des exigences et considérations &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
