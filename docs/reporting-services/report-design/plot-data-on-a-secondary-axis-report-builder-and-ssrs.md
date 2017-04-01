---
title: "Tracer des donn&#233;es sur un axe secondaire (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Tracer des donn&#233;es sur un axe secondaire (G&#233;n&#233;rateur de rapports et SSRS)
  Le graphique a deux types d'axes : principal et secondaire. L'axe secondaire est utile lors de la comparaison de deux jeux de valeurs avec deux plages de données distinctes qui partagent une catégorie commune.  
  
 Par exemple, supposons que vous ayez un graphique qui calcule vos revenus et impôts pour l'année 2008. Dans ce cas, la période 2008 est commune aux deux jeux de valeurs. Toutefois, lorsque les deux séries sont tracées sur le même axe des Y, nous ne pouvons pas établir de comparaison utile, car l'échelle de l'axe des Y est optimisée pour les plus grandes valeurs du dataset. Si nous affichons les revenus sur l'axe principal et les impôts sur l'axe secondaire, nous pouvons afficher chaque série sur son propre axe des Y avec sa propre échelle de valeurs. Les séries partagent encore un axe des abscisses commun.  
  
 Dans les cas où plus de deux séries doivent être comparées, envisagez une approche différente pour comparer et afficher plusieurs séries dans un graphique. Pour plus d’informations, consultez [Plusieurs séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Un exemple de ce graphique est disponible sous forme d'exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour tracer une série sur l'axe secondaire  
  
1.  Cliquez avec le bouton droit sur la série dans le graphique ou sur un champ dans la zone **Valeurs** que vous souhaitez afficher sur l’axe secondaire, puis cliquez sur **Propriétés de la série**. La boîte de dialogue **Propriétés de la série** s'affiche.  
  
2.  Cliquez sur **Axes et zone de graphique**, et sélectionnez l'axe secondaire que vous voulez activer, l'axe des ordonnées ou l'axe des abscisses.  
  
## Voir aussi  
 [Mise en forme des étiquettes des axes sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Spécifier un intervalle d’axe &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  