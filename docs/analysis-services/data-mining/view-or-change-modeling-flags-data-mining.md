---
title: "Afficher ou modifier les indicateurs de modélisation (exploration de données) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0109b4a95a81536cee4b00a5b4da05697219f769
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="view-or-change-modeling-flags-data-mining"></a>Afficher ou modifier les indicateurs de modélisation (Exploration de données)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Les indicateurs de modélisation sont des propriétés que vous définissez sur une colonne de structure d'exploration de données ou des colonnes du modèle d'exploration de données afin de contrôler la façon dont l'algorithme traite les données pendant l'analyse.  
  
 Dans le Concepteur d'exploration de données, vous pouvez afficher et modifier les indicateurs de modélisation associés à une structure d'exploration de données ou une colonne d'exploration de données en affichant les propriétés de la structure ou du modèle. Vous pouvez également définir des indicateurs de modélisation à l'aide de DMX, AMO ou XMLA.  
  
 Cette procédure décrit comment modifier les indicateurs de modélisation dans le concepteur.  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>Afficher ou modifier l'indicateur de modélisation pour une colonne de structure ou une colonne de modèle  
  
1.  Dans SQL Server Design Studio, ouvrez l'explorateur de solutions, puis double-cliquez sur la structure d'exploration de données.  
  
2.  Pour définir l'indicateur de modélisation NOT NULL, cliquez sur l'onglet **Structure d'exploration de données** . Pour définir les indicateurs REGRESSOR ou MODEL_EXISTENCE_ONLY, cliquez sur l’onglet **Modèle d’exploration de données** .  
  
3.  Cliquez avec le bouton droit sur la colonne à afficher ou à modifier, puis sélectionnez **Propriétés**.  
  
4.  Pour ajouter un nouvel indicateur de modélisation, cliquez sur la zone de texte en regard de la propriété **ModelingFlags** , puis activez la ou les cases à cocher en regard des indicateurs de modélisation à utiliser.  
  
     Les indicateurs de modélisation sont affichés uniquement s'ils sont appropriés pour le type de données de colonne.  
  
    > [!NOTE]  
    >  Après avoir modifié un indicateur de modélisation, vous devez retraiter le modèle.  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>Obtenir les indicateurs de modélisation utilisés dans le modèle  
  
-   Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez une fenêtre de requête DMX et tapez une requête comme celle qui suit :  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches liées aux modèles d’exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Modélisation des indicateurs &#40; exploration de données &#41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
