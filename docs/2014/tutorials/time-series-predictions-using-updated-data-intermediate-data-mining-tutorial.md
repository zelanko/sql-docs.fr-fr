---
title: À l’aide de la mise à jour des données (didacticiel d’exploration de données intermédiaire) des prédictions de série chronologique | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2017defaba74071b1a12bee14a5d8907e4c71cda
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63067555"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a>Prédictions de série chronologique à l'aide des données mises à jour (Didacticiel intermédiaire sur l'exploration de données)
    
## <a name="creating-predictions-using-the-extended-sales-data"></a>Création de prédictions à l'aide des données de ventes étendues  
 Dans cette leçon, vous allez créer une requête de prédiction qui ajoute les nouvelles données de ventes au modèle. En étendant le modèle avec de nouvelles données, vous pouvez obtenir des prédictions à jour qui comprennent les points de données les plus récents.  
  
 Est facile de créer des prédictions de série chronologique qui utilisent les nouvelles données : vous ajoutez simplement le paramètre EXTEND_MODEL_CASES à la [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) de fonction, spécifiez la source des nouvelles données et indiquez combien vous souhaitez obtenir les prédictions.  
  
> [!WARNING]  
>  Le paramètre EXTEND_MODEL_CASES est facultatif ; par défaut le modèle est étendu à chaque fois que vous créez une requête de prédiction de série chronologique en joignant de nouvelles données comme entrées.  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a>Pour générer la requête de prédiction et ajouter de nouvelles données  
  
1.  Si le modèle n’est pas déjà ouvert, double-cliquez sur la structure Forecasting, dans le Concepteur d’exploration de données, cliquez sur le **prévision de modèle d’exploration de données** onglet.  
  
2.  Dans le **Mining Model** volet, le modèle de prévision doit déjà être sélectionnée. Si elle n’est pas sélectionnée, cliquez sur **sélectionner un modèle**, puis sélectionnez le modèle de la prévision.  
  
3.  Dans le **sélectionner une ou plusieurs tables d’entrée** volet, cliquez sur **sélectionner la Table de cas**.  
  
4.  Dans le **sélectionner une Table** boîte de dialogue, sélectionnez la source de données [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].  
  
     Dans la liste des vues de sources de données, sélectionnez NewSalesData, puis cliquez **OK**.  
  
5.  Cliquez sur la surface de la zone de conception et sélectionnez **modifier les connexions**.  
  
6.  À l’aide de la **modifier le mappage** boîte de dialogue zone, mappez les colonnes dans le modèle aux colonnes dans les données externes, comme suit :  
  
    -   Mapper la colonne ReportingDate dans le modèle d’exploration de données à la colonne NewDate dans les données d’entrée.  
  
    -   Mapper la colonne Amount dans le modèle d’exploration de données à la colonne NewAmount dans les données d’entrée.  
  
    -   Mapper la colonne de quantité dans le modèle d’exploration de données à la colonne NewQty dans les données d’entrée.  
  
    -   Mapper la colonne ModelRegion dans le modèle d’exploration de données à la colonne de série dans les données d’entrée.  
  
7.  Vous allez maintenant générer la requête de prédiction.  
  
     D'abord, ajoutez une colonne à la requête de prédiction pour générer la sortie de la série à laquelle la prédiction s'applique.  
  
    1.  Dans la grille, cliquez sur la première ligne vide, sous **Source**, puis sélectionnez la prévision.  
  
    2.  Dans le **champ** colonne, sélectionnez Region de modèle et pour **Alias**, type `Model Region`.  
  
8.  Ensuite, ajoutez et modifiez la fonction de prédiction.  
  
    1.  Cliquez sur une ligne vide, puis, sous **Source**, sélectionnez **fonction de prédiction**.  
  
    2.  Pour **champ**, sélectionnez **PredictTimeSeries**.  
  
    3.  Pour **Alias**, type **valeurs prédites**.  
  
    4.  Faites glisser le champ Quantité à partir de la **Mining Model** volet dans le **critères/Argument** colonne.  
  
    5.  Dans le **critères/Argument** colonne, après le nom de champ, tapez le texte suivant :  **5,EXTEND_MODEL_CASES**  
  
         Le texte complet de le **critères/Argument** zone de texte doit être comme suit : `[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`  
  
9. Cliquez sur **résultats** et passez en revue les résultats.  
  
     Les prédictions commencent en juillet (première tranche de temps après la fin des données d'origine) et se terminent dans en novembre (cinquième tranche de temps après la fin des données d'origine).  
  
 Vous pouvez voir que, pour utiliser ce type de requête de prédiction efficacement, vous devez savoir quand les anciennes données se terminent, ainsi que le nombre de tranches de temps présentes dans les nouvelles données.  
  
 Par exemple, dans ce modèle, la série de données d'origine s'est terminée en juin et les données correspondent aux mois de juillet, août et septembre.  
  
 Les prédictions qui utilisent EXTEND_MODEL_CASES commencent toujours à la fin de la série de données d'origine. Par conséquent, si vous souhaitez obtenir uniquement les prédictions pour les mois inconnus, vous devez spécifier le point de départ et le point d'arrêt de la prédiction. Les deux valeurs sont spécifiées sous la forme d'un nombre de tranches de temps, en commençant par la fin des anciennes données.  
  
 La procédure suivante montre comment procéder.  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a>Modifiez les points de départ et de fin des prédictions  
  
1.  Dans le Générateur de requêtes de prédiction, cliquez sur **requête** pour basculer vers la vue DMX.  
  
2.  Localisez l'instruction DMX qui contient la fonction PredictTimeSeries et modifiez-la comme suit :  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  Cliquez sur **résultats** et passez en revue les résultats.  
  
     À présent, les prédictions commencent en octobre (quatrième tranche de temps en partant de la fin des données d'origine) et se terminent en décembre (sixième tranche de temps en partant de la fin des données d'origine).  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [À l’aide de données de remplacement des prédictions de série chronologique &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Références techniques relatives à l'algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Contenu du modèle d’exploration de données pour les modèles de séries chronologiques &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
