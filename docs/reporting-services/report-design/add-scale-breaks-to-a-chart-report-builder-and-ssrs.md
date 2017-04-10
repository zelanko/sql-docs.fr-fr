---
title: "Ajouter des s&#233;parations d&#39;&#233;chelle &#224; un graphique (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Ajouter des s&#233;parations d&#39;&#233;chelle &#224; un graphique (G&#233;n&#233;rateur de rapports et SSRS)
  Une séparation d'échelle est une ligne dessinée sur la zone de traçage d'un graphique pour indiquer une rupture dans la continuité entre les valeurs haute et basse d'un axe des ordonnées (en général, l'axe vertical ou axe des Y). Utilisez une séparation d'échelle pour afficher deux plages distinctes dans la même zone de graphique.  
  
 ![Graphique avec changement d'échelle](../../reporting-services/report-design/media/rs-multipledatarangeschart-scalebreak.gif "Graphique avec changement d'échelle")  
  
> [!NOTE]  
>  Vous ne pouvez pas spécifier où placer une séparation d'échelle sur votre graphique. Le graphique utilise ses propres calculs en fonction des valeurs de votre dataset pour déterminer si l'écart entre les différentes plages de données est suffisant pour dessiner une séparation d'échelle sur l'axe des ordonnées (axe Y) au moment de l'exécution.  
  
 Un exemple de graphique avec séparations d’échelle est disponible sous forme d’exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour activer les séparations d'échelle sur le graphique  
  
1.  Cliquez avec le bouton droit sur l’axe vertical, puis cliquez sur **Propriétés de l’axe**. La boîte de dialogue **Propriétés de l’axe vertical** s’ouvre.  
  
2.  Cochez la case **Activer les séparateurs d’échelle**.  
  
### Pour modifier le style de la séparation d'échelle  
  
1.  Ouvrez le volet Propriétés.  
  
2.  Dans l'aire de conception, cliquez avec le bouton droit sur l'axe Y du graphique. Les propriétés de l'objet de l'axe Y (nommé Axe de graphique par défaut) sont affichées dans le volet Propriétés.  
  
3.  Dans la section **Échelle**, développez la propriété ScaleBreakStyle.  
  
4.  Modifier les valeurs de la propriété ScaleBreakStyle, telles que BreakLineType et Spacing. Pour plus d’informations sur les propriétés des séparations d’échelle, consultez, [Affichage d’une série avec plusieurs plages de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/displaying-a-series-with-multiple-data-ranges-on-a-chart.md).  
  
## Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de l’axe, Options de l’axe &#40;Générateur de rapports et SSRS&#41;](../Topic/Axis%20Properties%20Dialog%20Box,%20Axis%20Options%20\(Report%20Builder%20and%20SSRS\).md)  
  
  