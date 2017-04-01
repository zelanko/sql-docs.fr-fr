---
title: "D&#233;marrer des valeurs de graphique &#224; secteurs en haut du graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# D&#233;marrer des valeurs de graphique &#224; secteurs en haut du graphique &#224; secteurs (G&#233;n&#233;rateur de rapports et SSRS)
Par défaut, dans les graphiques à secteurs des rapports paginés de [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)], la première valeur du dataset démarre à 90 degrés du haut du graphique à secteurs. 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*Les valeurs du graphique démarrent à 90 degrés.*

Vous pouvez préférer avoir la première valeur en haut. 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*Les valeurs du graphique commencent en haut du graphique.*
  
## Pour démarrer le graphique à secteurs en haut  
  
1.  Cliquez sur les secteurs.  
  
2.  Si le volet **Propriétés** n'est pas ouvert, cliquez sur **Propriétés** sous l'onglet **Affichage**.  
  
3.  Dans le volet **Propriétés** , sous **Attributs personnalisés**, remplacez la valeur de **PieStartAngle** définie sur **0** par **270**.  
  
4.  Cliquez sur **Exécuter** pour afficher un aperçu du rapport.  
  
 La première valeur démarre à présent en haut du graphique à secteurs.  
  
## Voir aussi  
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Graphiques à secteurs &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  