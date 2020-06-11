---
title: Assistant Prévision (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- forecasting [data mining]
- time series [data mining]
ms.assetid: c5b33f75-42d4-4598-89e7-94815c142ce6
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3c4d728f810da7abf96d1addc6ef91156a3d5ea
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544421"
---
# <a name="forecast-wizard-data-mining-add-ins-for-excel"></a>Assistant Prévisions (Compléments d'exploration de données pour Excel)
  ![Assistant Association sur le ruban Exploration de données](media/dmc-forecast.gif "Assistant Association sur le ruban Exploration de données")  
  
 L'Assistant Prévision vous permet de prévoir des valeurs dans une série chronologique. Cet Assistant utilise l'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series), un algorithme de régression utilisé pour prévoir les colonnes continues telles que les ventes de produits.  
  
 Chaque modèle de prévision doit contenir une série de cas qui correspond à la colonne différenciant les points d'une séquence. Par exemple, si vous utilisez des données historiques pour prédire les ventes sur une période de plusieurs mois, vous devez utiliser une colonne contenant une série de dates comme série de cas.  
  
 Vous pouvez créer des prédictions à partir du modèle de prévision sans fournir de nouvelles données d'entrée.  
  
 L’outil [prévision &#40;table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) , dans le ruban **analyser** , vous permet également de créer des modèles de prévision, mais il est moins personnalisable et ne peut utiliser que des données dans les tables Excel.  
  
## <a name="using-the-forecast-wizard"></a>Utilisation de l'Assistant Prévision  
  
1.  Dans le ruban **exploration de données** , cliquez sur **prévision**.  
  
2.  Dans **Sélectionner les données source**, choisissez le tableau, la plage ou la source de données externe Excel à utiliser comme entrées.  
  
     Si vous utilisez une source de données externe, vous pouvez définir une vue personnalisée ou des requêtes et les enregistrer en tant que source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
3.  Dans la page **prévision** , pour **horodatage**, sélectionnez une colonne qui contient une valeur numérique unique (y compris des valeurs de date et d’heure) qui peut être utilisée comme série de cas. La source de données doit être triée par ordre croissant dans cette colonne.  
  
     Si vos données n’ont pas une telle colonne, vous pouvez utiliser l’option \<no time stamp> . L'Assistant ajoutera une colonne d'ordre unique pour les données d'entrée ; par conséquent, vous devez vous assurer que les données sont triées comme vous le souhaitez avant d'exécuter l'assistant et de choisir cette option.  
  
4.  Si vous le souhaitez, vous pouvez cliquer sur **paramètres** et personnaliser le comportement du modèle d’exploration de données.  
  
     Les modèles de prévision prennent en charge plusieurs algorithmes différents :  
  
    -   ARIMA  
  
    -   ARTXP (un type de modèle de régression)  
  
    -   ARTXP et ARIMA combinés  
  
     Pour plus d’informations sur les différences, consultez informations techniques de référence sur l' [algorithme MTS (Microsoft Time Series](data-mining/microsoft-time-series-algorithm-technical-reference.md)).  
  
     Vous pouvez également ajouter des indicateurs de périodicité, spécifiant des options de lissage, et personnaliser les options de régression pour le modèle.  
  
5.  Dans la page **Terminer** , indiquez un nom descriptif pour votre jeu de données et votre modèle, puis définissez les options suivantes qui contrôlent la façon dont vous travaillez avec le modèle terminé :  
  
    -   **Parcourir le modèle**. Lorsque cette option est sélectionnée, dès que l’Assistant a terminé de traiter le modèle, il ouvre une fenêtre **Parcourir** pour vous aider à explorer les résultats. Le contenu de la visionneuse dépend du type de modèle que vous créez. Pour plus d’informations, consultez [exploration d’un modèle de prévision](browsing-a-forecasting-model.md).  
  
    -   **Activer l’extraction**. Sélectionnez cette option pour examiner les données sous-jacentes du modèle terminé. Cette option est disponible uniquement si vous créez un modèle d'arbre de décision.  
  
    -   **Utilisez le modèle temporaire**. Si cette option est sélectionnée, le modèle ne sera pas enregistré sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
### <a name="requirements"></a>Spécifications  
 Vos données doivent inclure au moins une colonne pouvant être utilisée en tant que série chronologique. Les valeurs de cette colonne doivent être uniques et continues, autrement dit, il ne doit pas y avoir d’écarts. Avant d'exécuter l'assistant, triez les données de la colonne de série chronologique par ordre croissant.  
  
 Si vos données ne contiennent pas de colonne de date ou d'heure, vous pouvez utiliser une série numérique arbitraire ou laisser l'assistant s'en charger. Si vous laissez l'assistant créer la colonne d'ordre de la série, assurez-vous que les autres colonnes sont triées dans l'ordre souhaité avant de démarrer l'assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Outils d’analyse de table &#40;de prévision pour Excel&#41;](forecast-table-analysis-tools-for-excel.md)   
 [Exploration d'un modèle de prévision](browsing-a-forecasting-model.md)  
  
  
