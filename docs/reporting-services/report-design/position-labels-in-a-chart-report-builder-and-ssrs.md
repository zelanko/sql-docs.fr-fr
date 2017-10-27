---
title: "Positionner des étiquettes dans un graphique (Générateur de rapports et SSRS) | Documents Microsoft"
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
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 53f0d4b0c6aed30746af82de7d5f1caf5e42721c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a>Placer des étiquettes dans un graphique (Générateur de rapports et SSRS)
  Chaque type de graphique figurant dans un rapport paginé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ayant une forme différente, les étiquettes de point de données sont positionnées de manière optimale de façon à ne pas interférer sur le graphique. La position par défaut des étiquettes varie en fonction du type de graphique :  
  
-   Sur les graphiques empilés, les étiquettes peuvent être uniquement être positionnées à l'intérieur de la série.  
  
-   Sur les graphiques en entonnoir ou en pyramide, les étiquettes sont placées à l'extérieur d'une colonne.  
  
-   Sur les graphiques à secteurs, les étiquettes sont placées à l'intérieur des différents secteurs.  
  
-   Sur les graphiques à barres, les étiquettes sont placées en dehors des barres qui représentent les points de données.  
  
-   Sur les graphiques polaires, les étiquettes sont placées en dehors de la zone circulaire qui représente les points de données.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a>Pour modifier la position des étiquettes de point dans un graphique à secteurs  
  
1.  Créez un graphique à secteurs.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**.  
  
4.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés du graphique sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Général** , développez le nœud **CustomAttributes** . Une liste des attributs du graphique à secteurs s'affiche.  
  
6.  Sélectionnez une valeur pour la propriété PieLabelStyle.  
  
## <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a>Pour modifier la position des étiquettes de point dans un graphique en entonnoir ou en pyramide  
  
1.  Créez un graphique en entonnoir ou en pyramide.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**  
  
4.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés du graphique sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Général** , développez le nœud **CustomAttributes** . Une liste des attributs du graphique en entonnoir s'affiche.  
  
6.  Pour un graphique en entonnoir, sélectionnez une valeur pour la propriété FunnelLabelStyle. Pour un graphique en pyramide, sélectionnez une valeur pour la propriété PyramidLabelStyle.  
  
    > [!NOTE]  
    >  Quand cette propriété a une valeur **OutsideInColumn**, les étiquettes sont dessinées dans une colonne verticale. Il est impossible de modifier la position de la colonne.  
  
## <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a>Pour modifier la position des étiquettes de point dans un graphique à barres  
  
1.  Créez un graphique à barres.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**  
  
4.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés du graphique sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Général** , développez le nœud **CustomAttributes** . Une liste des attributs du graphique à barres s'affiche.  
  
6.  Sélectionnez une valeur pour la propriété BarLabelStyle.  
  
 Quand le style de l’étiquette de la barre a la valeur **Outside**, les étiquettes sont placées en dehors de la barre, dans la mesure où elles s’ajustent à la zone du graphique. Si l'étiquette ne peut pas être placée en dehors de barre mais dans la zone du graphique, elle est placée à l'intérieur de la barre à la position la plus proche de l'extrémité de la barre.  
  
## <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a>Pour modifier la position des étiquettes de point dans un graphique à secteurs, un histogramme, un graphique en courbes ou un graphique à nuage de points  
  
1.  Créez un graphique à secteurs, un histogramme, un graphique en courbes ou un graphique à nuage de points.  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique et sélectionnez **Afficher les étiquettes de données**.  
  
3.  Ouvrez le volet Propriétés. Sous l'onglet **Affichage** , cliquez sur **Propriétés**  
  
4.  Sur l'aire de conception, cliquez sur la série. Les propriétés de la série sont affichées dans le volet Propriétés.  
  
5.  Dans la section **Données** , développez le nœud **DataPoint** , puis le nœud **Étiquette**.  
  
6.  Sélectionnez une valeur pour la propriété Position.  
  
## <a name="see-also"></a>Voir aussi  
 [Les graphiques en secteurs &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Graphiques à barres &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Mise en forme les étiquettes des axes sur un graphique &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Étiquettes d’axe de format en tant que Dates ou devises &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Afficher les étiquettes de Point de données en dehors d’un graphique à secteurs &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Mise en forme des Points de données sur un graphique &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  

