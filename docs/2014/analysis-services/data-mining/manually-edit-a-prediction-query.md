---
title: Modifier manuellement une requête de prédiction | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8809e025a60a47acb2db5dae312702ee2e3effd3
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522085"
---
# <a name="manually-edit-a-prediction-query"></a>Modifier manuellement une requête de prédiction
  Après avoir créé une requête en utilisant le Générateur de requêtes de prédiction, vous pouvez modifier la requête en activant le mode Texte de la requête sous l’onglet **Prédiction de modèle d’exploration de données** du Concepteur d’exploration de données. Un éditeur de texte apparaît au bas de l'écran pour afficher la requête créée par le Générateur de requêtes.  
  
 Le basculement vers le mode Texte de la requête est utile pour effectuer des ajouts à la requête. Par exemple, vous pouvez ajouter une clause WHERE ou une clause ORDER BY.  
  
 Utilisez la grille dans le Générateur de requêtes de prédiction pour insérer le nom des objets et des colonnes, ainsi que pour configurer la syntaxe de fonctions de prédiction individuelles, puis basculez vers le mode de modification manuelle pour modifier des valeurs de paramètres.  
  
> [!NOTE]  
>  Si vous repassez du mode **Texte de la requête** au mode **Conception** , toutes les modifications apportées en mode **Texte de la requête** sont perdues.  
  
### <a name="modify-a-query"></a>Modifier une requête  
  
1.  Sous l’onglet **Prédiction de modèle d’exploration de données** du Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur **SQL**.  
  
     La grille au bas de l'écran est remplacée par un éditeur de texte qui contient la requête. Vous pouvez modifier la requête dans cet éditeur.  
  
2.  Pour exécuter la requête, dans le menu **Modèle d’exploration de données** , sélectionnez **Résultat**ou cliquez sur le bouton pour passer aux résultats de la requête.  
  
    > [!NOTE]  
    >  Si la requête que vous avez créée n'est pas valide, la fenêtre Résultats n'affiche ni erreur ni résultats. Cliquez sur le bouton **Conception** ou sélectionnez **Conception** ou **Requête** dans le menu **Modèle d’exploration de données** pour résoudre le problème et réexécuter la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes d’exploration de données](data-mining-queries.md)   
 [Prédiction Générateur de requêtes &#40;l’exploration de données&#41;](../prediction-query-builder-data-mining.md)   
 [Leçon 6 : création et utilisation de prédictions &#40;Didacticiel sur l’exploration de données de base&#41;](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  
