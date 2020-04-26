---
title: Modification de la structure de prévision (didacticiel sur l’exploration de données intermédiaire) | Microsoft Docs
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63301301"
---
# <a name="modifying-the-forecasting-structure-intermediate-data-mining-tutorial"></a>Modification de la structure de prévision (Didacticiel sur l'exploration de données intermédiaire)
  La structure d'exploration de données créée dans la tâche précédente contient un seul modèle de prédiction. Avant de pouvoir traiter et explorer le modèle, vous devez légèrement modifier sa structure et modifier l'une de ses propriétés.  
  
## <a name="modifying-the-mining-structure"></a>Modification de la structure d'exploration de données  
 Vous pouvez modifier la structure d’exploration de données à l’aide de l’onglet **structure d’exploration** de données du concepteur d’exploration de données. Lors de la création du modèle à l'aide de l'Assistant Exploration de données, vous avez utilisé trois colonnes : ReportingDate, ModelRegion et Quantity. Toutefois, la table de **prévision** contient également une colonne Amount, que vous pouvez utiliser pour prévoir le montant des ventes. À l’aide de l’onglet **structure d’exploration** de données, vous pouvez ajouter cette colonne de la vue de source de données à la structure d’exploration de données.  
  
#### <a name="to-add-the-amount-column-to-the-forecasting-mining-structure"></a>Pour ajouter la colonne Amount dans la table Forecasting de la structure d'exploration de données  
  
1.  Sous l’onglet **structure d’exploration** de données du concepteur d’exploration de données, dans le volet vue de source de **données** , sélectionnez la colonne Amount dans la table vTimeSeries.  
  
2.  Faites glisser la colonne Amount du volet **vue de source de données** vers la liste des colonnes pour la structure de **prévision** .  
  
     La colonne Amount est maintenant incluse dans la **prévision** de la structure d’exploration de données.  
  
## <a name="modifying-the-columns-in-the-mining-model"></a>Modification des colonnes dans le modèle d'exploration de données  
 Étant donné que vous avez ajouté une nouvelle colonne à la structure, vous devez définir la façon dont le modèle devra utiliser cette colonne. Vous pouvez spécifier comment la colonne sera utilisée dans l’onglet **modèles d’exploration** de données du concepteur d’exploration de données.  
  
 L’onglet **modèles d’exploration de données** répertorie les colonnes que contient la structure d’exploration de données dans la colonne **structure** de la grille et répertorie les colonnes que contient le modèle d’exploration de données dans la colonne qui porte le nom du modèle, dans ce cas **prévisions**. Sélectionnez les noms des colonnes pour apporter des modifications. Dans le modèle d’exploration de données **prévision** , la colonne Amount est utilisée comme colonne d’entrée et est également utilisée pour prévoir les ventes futures. Par conséquent, vous devez définir les propriétés de la colonne afin qu'elle puisse être utilisée à la fois comme colonne d'entrée et comme colonne prédictible.  
  
> [!NOTE]  
>  Dans l’onglet **modèles d’exploration de données** , vous pouvez également créer des modèles basés sur la même structure, et vous pouvez ajuster les propriétés de l’algorithme et de la colonne pour chaque modèle. Toutefois, vous devez traiter le modèle au préalable pour que les modifications apportées prennent effet.  
  
#### <a name="to-define-how-the-amount-column-will-be-used"></a>Pour définir la façon dont la colonne Amount sera utilisée  
  
1.  Dans la colonne **prévision** de la grille, sous l’onglet **modèles d’exploration de données** , cliquez sur la cellule dans la ligne montant.  
  
2.  Sélectionnez **prédire** dans la liste.  
  
     La colonne Amount est maintenant à la fois une colonne d'entrée et une colonne prédictible.  
  
 Vous pouvez également modifier les propriétés des colonnes individuelles en sélectionnant la colonne et en ouvrant la fenêtre **Propriétés** . Pour ouvrir la fenêtre **Propriétés** , cliquez avec le bouton droit sur le nom de la colonne, puis sélectionnez **Propriétés**. Si vous modifiez une propriété dans cette colonne pour un modèle individuel, vous pouvez modifier les propriétés de ce modèle uniquement. Toutefois, lorsque vous modifiez une propriété dans la colonne de **structure** , la modification affecte tous les modèles associés à la structure. Chaque fois que vous apportez des modifications au modèle ou à la structure, vous devez effectuer un nouveau traitement pour constater les effets.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Personnalisation et traitement du modèle de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’exploration de données &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
