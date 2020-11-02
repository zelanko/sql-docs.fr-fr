---
title: Afficher des valeurs en pourcentage sur un graphique à secteurs (Générateur de rapports) | Microsoft Docs
description: Découvrez comment afficher des valeurs en pourcentage sur un graphique à secteurs, dans la légende ou dans les secteurs dans le Générateur de rapports.
ms.date: 12/09/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6068c871bd96908e501c552e0388050aedfa47bf
ms.sourcegitcommit: ea0bf89617e11afe85ad85309e0ec731ed265583
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907227"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>Afficher des valeurs en pourcentage dans un graphique à secteurs (Générateur de rapports et SSRS)
Dans les rapports paginés [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)], la légende affiche par défaut les catégories. Vous souhaiterez peut-être également afficher des pourcentages dans la légende ou dans les secteurs eux-mêmes.   

![Capture d’écran d’un graphique à secteurs montrant les pourcentages des secteurs du graphique.](../../reporting-services/media/report-builder-pie-chart-preview-percents.png)

 Le [Didacticiel : ajouter un graphique à secteurs à un rapport (Générateur de rapports)](../tutorial-add-a-pie-chart-to-your-report-report-builder.md) vous guide pas à pas dans la procédure d’ajout de pourcentage aux secteurs, si vous voulez essayer avec des exemples de données.
 
  
## <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>Pour afficher des valeurs en pourcentage sous forme d'étiquettes sur un graphique à secteurs  
  
1.  Ajoutez un graphique à secteurs à votre rapport. Pour plus d’informations, consultez [Ajouter un graphique à un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le secteur, puis sélectionnez **Afficher les étiquettes de données** . Les étiquettes de données doivent apparaître dans chaque secteur du graphique.  
  
3.  Dans l’aire de conception, cliquez avec le bouton droit sur les étiquettes, puis sélectionnez **Propriétés de l’étiquette de la série** . La boîte de dialogue **Propriétés de l'étiquette de la série** s'affiche.  
  
4.  Tapez **#PERCENT** pour l’option **Données de l’étiquette** .  
  
5.  (Facultatif) Pour indiquer le nombre de décimales affichées sur l’étiquette, tapez « #PERCENT{P *n* } », où *n* correspond au nombre de décimales à afficher. Par exemple, pour ne pas afficher de décimale, tapez « #PERCENT{P0} ».  
  
## <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>Pour afficher des valeurs en pourcentage dans la légende d'un graphique à secteurs  
  
1.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique à secteurs, puis sélectionnez **Propriétés de la série** . La boîte de dialogue **Propriétés de la série** s’affiche.  
  
2.  Dans **Légende** , tapez **#PERCENT** pour la propriété **Texte de légende personnalisé** .  
  
## <a name="see-also"></a>Voir aussi  
* [Tutoriel : Ajouter un graphique à secteurs à un rapport (Générateur de rapports)](../tutorial-add-a-pie-chart-to-your-report-report-builder.md)
*  [Graphiques à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
*  [Mise en forme de la légende sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
*  [Afficher des étiquettes de points de données à l’extérieur d’un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 
  
