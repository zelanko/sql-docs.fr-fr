---
title: Modification de la Structure de prévision (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1a6c138e-643b-4ae6-ad08-93631f149c20
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a86ddf0a715fc3a2313f555e898b3bd94cf66d8c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301301"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a>Modification de la structure de prévision (Didacticiel sur l'exploration de données intermédiaire)
  La structure d'exploration de données créée dans la tâche précédente contient un seul modèle de prédiction. Avant de pouvoir traiter et explorer le modèle, vous devez légèrement modifier sa structure et modifier l'une de ses propriétés.  
  
## <a name="modifying-the-mining-structure"></a>Modification de la structure d'exploration de données  
 Vous pouvez modifier la structure d’exploration de données à l’aide de la **Structure d’exploration de** onglet du Concepteur d’exploration de données. Lorsque vous avez créé le modèle avec l’Assistant exploration de données, vous avez utilisé trois colonnes : ReportingDate, ModelRegion et Quantity. Toutefois, le **Forecasting** table contient également une colonne de montant, ce qui vous permet de prévoir la quantité de ventes. À l’aide de la **Structure d’exploration de** onglet, vous pouvez ajouter cette colonne à partir de la vue de source de données à la structure d’exploration de données.  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a>Pour ajouter la colonne Amount dans la table Forecasting de la structure d'exploration de données  
  
1.  Sur le **Structure d’exploration de données** onglet du Concepteur d’exploration de données, dans le **vue de Source de données** volet, sélectionnez la colonne Amount dans la table vTimeSeries.  
  
2.  Faites glisser la colonne de quantité à partir de la **vue de Source de données** volet dans la liste des colonnes pour le **Forecasting** structure.  
  
     La colonne Amount est maintenant incluse dans le **Forecasting** structure d’exploration de données.  
  
## <a name="modifying-the-columns-in-the-mining-model"></a>Modification des colonnes dans le modèle d'exploration de données  
 Étant donné que vous avez ajouté une nouvelle colonne à la structure, vous devez définir la façon dont le modèle devra utiliser cette colonne. Vous pouvez spécifier la façon dont la colonne sera utilisée sur le **des modèles d’exploration de données** onglet du Concepteur d’exploration de données.  
  
 Le **les modèles d’exploration de données** onglet répertorie les colonnes contenant la structure d’exploration de données dans le **Structure** colonne de la grille et répertorie les colonnes contenant le modèle d’exploration de données dans la colonne portant le nom de la modèle, dans ce cas **Forecasting**. Sélectionnez les noms des colonnes pour apporter des modifications. Dans le **Forecasting** modèle d’exploration de données, la colonne Amount est utilisée comme colonne d’entrée et est également utilisée pour prédire les ventes futures. Par conséquent, vous devez définir les propriétés de la colonne afin qu'elle puisse être utilisée à la fois comme colonne d'entrée et comme colonne prédictible.  
  
> [!NOTE]  
>  Dans le **des modèles d’exploration de données** onglet, vous pouvez également créer des modèles basés sur la même structure, et vous pouvez ajuster les propriétés d’algorithme et des colonnes pour chaque modèle. Toutefois, vous devez traiter le modèle au préalable pour que les modifications apportées prennent effet.  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a>Pour définir la façon dont la colonne Amount sera utilisée  
  
1.  Dans le **Forecasting** colonne de la grille sur la **des modèles d’exploration de données** , cliquez sur la cellule dans la ligne Amount.  
  
2.  Sélectionnez **Predict** dans la liste.  
  
     La colonne Amount est maintenant à la fois une colonne d'entrée et une colonne prédictible.  
  
 Vous pouvez également modifier les propriétés des colonnes en sélectionnant la colonne et en ouvrant le **propriétés** fenêtre. Pour ouvrir le **propriétés** fenêtre, cliquez sur le nom de colonne, puis sélectionnez **propriétés**. Si vous modifiez une propriété dans cette colonne pour un modèle individuel, vous pouvez modifier les propriétés de ce modèle uniquement. Toutefois, lorsque vous modifiez une propriété dans le **Structure** colonne, la modification affecte tous les modèles qui sont associé à la structure. Chaque fois que vous apportez des modifications au modèle ou à la structure, vous devez effectuer un nouveau traitement pour constater les effets.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Personnalisation et traitement du modèle de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’exploration de données &#40;Analysis Services – Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
