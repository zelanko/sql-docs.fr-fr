---
title: "Afficher des valeurs de pourcentage dans un graphique à secteurs (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6c0fdf9d1b694f2f6d49389e913d1c156ba77838
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>Afficher des valeurs en pourcentage dans un graphique à secteurs (Générateur de rapports et SSRS)
Dans [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] des rapports paginés, par défaut la légende affiche les catégories. Vous pouvez également la forme de pourcentages dans la légende ou les secteurs eux-mêmes.   

![report-builder-pie-chart-preview-percents](../../reporting-services/media/report-builder-pie-chart-preview-percents.png)

 Le [didacticiel : ajouter un graphique à secteurs à votre rapport (Générateur de rapports)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md) vous explique comment ajouter les pourcentages à secteurs, si vous souhaitez essayer tout d’abord les exemples de données.
 
  
## <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>Pour afficher des valeurs en pourcentage sous forme d'étiquettes sur un graphique à secteurs  
  
1.  Ajoutez un graphique à secteurs à votre rapport. Pour plus d’informations, voir [Ajouter un graphique à un rapport (Générateur de rapports et SSRS)](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le secteur, puis sélectionnez **Afficher les étiquettes de données**. Les étiquettes de données doivent apparaître dans chaque secteur du graphique.  
  
3.  Dans l’aire de conception, cliquez avec le bouton droit sur les étiquettes, puis sélectionnez **Propriétés de l’étiquette de la série**. La boîte de dialogue **Propriétés de l'étiquette de la série** s'affiche.  
  
4.  Tapez **#PERCENT** pour l’option **Données de l’étiquette** .  
  
5.  (Facultatif) Pour spécifier le nombre de décimales l’étiquette, tapez « #PERCENT {P*n*} » où  *n*  est le nombre de décimales à afficher. Par exemple, pour ne pas afficher de décimale, tapez « #PERCENT{P0} ».  
  
## <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>Pour afficher des valeurs en pourcentage dans la légende d'un graphique à secteurs  
  
1.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique à secteurs, puis sélectionnez **Propriétés de la série**. La boîte de dialogue **Propriétés de la série** s’affiche.  
  
2.  Dans **Légende**, tapez **#PERCENT** pour la propriété **Texte de légende personnalisé** .  
  
## <a name="see-also"></a>Voir aussi  
* [Didacticiel : Ajouter un graphique à secteurs à votre rapport (Générateur de rapports)](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)
*  [Graphiques à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
*  [Mise en forme de la légende sur un graphique (Générateur de rapports et SSRS)](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
*  [Afficher des étiquettes de points de données à l’extérieur d’un graphique à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 
  
